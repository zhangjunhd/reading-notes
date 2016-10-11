# Linux动态库与静态库

静态库与动态库二者的不同点在于代码被载入的时刻不同：

* 静态库在程序编译时会被连接到目标代码中，程序运行时将不再需要该静态库，因此体积较大。
* 动态库在程序编译时并不会被连接到目标代码中，而是在程序运行是才被载入，因此在程序运行时还需要动态库存在，因此代码体积较小。与此同时，也会带来如经典的DLL Hell问题(`DLL Hell` 是指当多个应用程序试图共享一个公用组件（如某个动态连接库（DLL）或某个组件对象模型（COM）类）时所引发的一系列问题。最典型的情况是，某个应用程序将要安装一个新版本的共享组件，而该组件与机器上的现有版本不向后兼容。虽然刚安装的应用程序运行正常，但原来依赖前一版本共享组件的应用程序也许已无法再工作。)。
* 当静态库和动态库同名时， gcc命令将优先使用动态库。为了确保使用的是静态库, 编译时可以加上 -static  选项。

### 1 制作并使用静态库
编写代码：
```c
/* add.h */
#ifndef _ADD_H_
#define _ADD_H_

int add(int, int);

#endif

/* add.c */
#include "add.h"

int add(int x, int y)
{
    return x + y;
}

/* main.c */
#include <stdio.h>
#include "add.h"

int main(void)
{
    printf("2+3= %d\n", add(2,3));
    return 0;
}
```

制作静态库：

    #gcc -c add.c             //生成add.o
    #ar crv libadd.a add.o    //生成libadd.a

编译main.c时将静态库链接进去(生成可执行文件main):

    #gcc -o main main.c -I. -L. -ladd

执行ldd main：

    libc.so.6 => /lib64/libc.so.6 (0x000000329d000000)
    /lib64/ld-linux-x86-64.so.2 (0x000000329cc00000)

### 2 制作并隐式使用动态库

把add.c编译生成动态库(创建动态库)：

    #gcc -fPIC -c add.c    //生成add.o
    #gcc -shared -o libadd.so add.o //生成libadd.so
    (上面两行可以整合成一行：#gcc -fPIC -shared -o libadd.so add.c)
    -fpic 使输出的对象模块是按照可重定位地址方式生成的(即与位置无关)。

编译main.c生成可执行程序(动态库隐式调用的使用):

    #gcc -o main main.c ./libadd.so
    或者 #gcc -o main main.c -L. libadd.so

也可将libadd.so 拷贝到目录 /usr/lib或/lib中，然后执行(或 export LD_LIBRARY_PATH=$(pwd) 如果有root权限的话，可以修改/etc/ld.so.conf文件，然后调用 /sbin/ldconfig来达到同样的目的)：

    #gcc -o main main.c libadd.so //此时不需要指定搜索路径

执行ldd main：

    ./libadd.so (0x00002aae08dd3000)
	libc.so.6 => /lib64/libc.so.6 (0x000000329d000000)
	/lib64/ld-linux-x86-64.so.2 (0x000000329cc00000)

### 3 显式使用动态库
显示调用动态库,编译时无需库文件,执行时动态库可存储于任意位置：

```c
//打开动态库
#include<dlfcn.h>
void *dlopen(const char * pathname,int mode);

//获取动态库对象地址
include<dlfcn.h>
void *dlsym(void *handle,const char *name);

//错误检测
include<dlfcn.h>
char *dlerror(vid);

//关闭动态库
include<dlfcn.h>
int dlclose(void * handle);
```

编写main.c

```c
#include <stdio.h>
#include <dlfcn.h>   //显式加载需要用到的头文件

#define LIB  "./libadd.so"   //指定动态库路径

int main(void)
{
    void *dl;
    char *error;
    int (*func)(int,int);

    dl = dlopen(LIB, RTLD_LAZY); /*打开动态链接库*/
    if(dl == NULL) {
        printf("Failed load libary\n");
    }

    error = dlerror(); /*检测错误*/
    if(error != NULL) {
        printf("%s\n", error);
        return -1;
    }

    func = dlsym(dl, "add"); /*获取函数的地址*/
    error = dlerror(); /*检测错误*/
    if(error != NULL) {
        printf("%s\n", error);
        return -1;
    }

    printf("2+3= %d\n", func(2,3));/*调用动态库中函数*/

    dlclose(dl);  /*关闭共享库*/
    error = dlerror(); /*检测错误*/
    if(error != NULL) {
        printf("%s\n", error);
        return -1;
    }

    return 0;
}
```

编译main.c生成可执行程序(动态库显式调用):

    #gcc -ldl -o exe mian.c

执行ldd main：

    libdl.so.2 => /lib64/libdl.so.2 (0x000000329d800000)
	libc.so.6 => /lib64/libc.so.6 (0x000000329d000000)
	/lib64/ld-linux-x86-64.so.2 (0x000000329cc00000)

C++ 显式使用动态库可参考[C++ dlopen mini HOWTO][1]

[1]:http://www.faqs.org/docs/Linux-mini/C++-dlopen.html
