## Remove CTRL-M characters from a file in UNIX

You can also do it in vi: % vi filename

Inside vi [in ESC mode] type: :%s/^M//g

To enter ^M, type CTRL-V, then CTRL-M. That is, hold down the CTRL key then press V and M in succession.
