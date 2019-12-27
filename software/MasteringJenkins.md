![cover](https://img1.doubanio.com/view/subject/l/public/s28390838.jpg)

    作者: Jonathan McAllister
    出版社: Packt Publishing
    副标题: Configure and extend Jenkins to architect, build, and automate efficient software delivery pipelines
    出版年: 2015-10-27
    页数: 334
    定价: USD 35.99
    装帧: Paperback
    ISBN: 9781784390891

[豆瓣链接](https://book.douban.com/subject/26715927/)

- [Distributed Builds – Master Slave Mode](#distributed-builds-%e2%80%93-master-slave-mode)
  - [Understanding the master and slave architecture](#understanding-the-master-and-slave-architecture)
  - [Choosing a launch method](#choosing-a-launch-method)
    - [Slave agents via SSH tunneling](#slave-agents-via-ssh-tunneling)
  - [Administering Jenkins slaves](#administering-jenkins-slaves)
    - [The node administration dashboard](#the-node-administration-dashboard)
    - [Preventative monitoring](#preventative-monitoring)
    - [Managing individual slave nodes](#managing-individual-slave-nodes)
  - [Labels, groups, and load balancing](#labels-groups-and-load-balancing)
    - [Attaching a slave to a group by creating a label](#attaching-a-slave-to-a-group-by-creating-a-label)
    - [Attaching a slave to many groups](#attaching-a-slave-to-many-groups)
    - [Restricting slave execution to global or tied jobs](#restricting-slave-execution-to-global-or-tied-jobs)
    - [Jenkins plugins that support distributed builds](#jenkins-plugins-that-support-distributed-builds)
- [Creating Views and Jobs in Jenkins](#creating-views-and-jobs-in-jenkins)
  - [Jobs in Jenkins](#jobs-in-jenkins)
- [Advanced Automated Testing](#advanced-automated-testing)
  - [Quality assurance initiatives and test automation terminology](#quality-assurance-initiatives-and-test-automation-terminology)
  - [The Software Development Lifecycle](#the-software-development-lifecycle)
  - [Connecting product codes to tests](#connecting-product-codes-to-tests)
  - [Baking quality into the product](#baking-quality-into-the-product)
    - [Smoke test tip](#smoke-test-tip)
  - [Distributed testing solutions](#distributed-testing-solutions)
- [Software Deployments and Delivery](#software-deployments-and-delivery)
  - [Standardizing build outputs](#standardizing-build-outputs)
    - [Architecting a packaging scheme](#architecting-a-packaging-scheme)
    - [Build and deployment best practice](#build-and-deployment-best-practice)
    - [Snapshots and Releases Tip](#snapshots-and-releases-tip)
  - [Implementing a Definitive Media Library](#implementing-a-definitive-media-library)
    - [Publishing assets to a DML](#publishing-assets-to-a-dml)
      - [JENKINS' ARCHIVE THE ARTIFACTS POST-BUILD ACTION](#jenkins-archive-the-artifacts-post-build-action)
      - [PUBLISHING TO ARTIFACTORY](#publishing-to-artifactory)
      - [PUBLISHING VIA MAVEN](#publishing-via-maven)
      - [PUSHING A DOCKER CONTAINER](#pushing-a-docker-container)
  - [Automated deployments](#automated-deployments)
    - [Retrieving build artifacts and packages](#retrieving-build-artifacts-and-packages)
      - [FETCHING ARTIFACTS VIA ARCHIVE ARTIFACTS](#fetching-artifacts-via-archive-artifacts)
      - [FETCHING ARTIFACTS FROM ARTIFACTORY](#fetching-artifacts-from-artifactory)
      - [FETCHING ARTIFACTS VIA MAVEN](#fetching-artifacts-via-maven)
    - [Leveraging Jenkins slave nodes for deployment](#leveraging-jenkins-slave-nodes-for-deployment)
- [Continuous Practices](#continuous-practices)
  - [Continuous Integration](#continuous-integration)
    - [What Continuous Integration is not](#what-continuous-integration-is-not)
    - [Code-based branching techniques](#code-based-branching-techniques)
      - [Feature toggles](#feature-toggles)
    - [Continuous Integration in Jenkins](#continuous-integration-in-jenkins)
      - [SCM POLLING](#scm-polling)
      - [RUNNING A JENKINS JOB VIA THE SVN POST-COMMIT HOOKS](#running-a-jenkins-job-via-the-svn-post-commit-hooks)
      - [TRIGGERING A JENKINS JOB VIA GITHUB PUSH](#triggering-a-jenkins-job-via-github-push)
  - [Continuous Delivery](#continuous-delivery)
  - [Continuous Deployment](#continuous-deployment)
    - [Continuous Deployment in Jenkins](#continuous-deployment-in-jenkins)
- [Integrating Jenkins with Other Technologies](#integrating-jenkins-with-other-technologies)
  - [Jenkins and Docker – Linux guide](#jenkins-and-docker-%e2%80%93-linux-guide)
  - [Integrating Jenkins with Ansible – Linux and Windows](#integrating-jenkins-with-ansible-%e2%80%93-linux-and-windows)
  - [Jenkins and Artifactory](#jenkins-and-artifactory)
  - [Jenkins and Selenium Grid](#jenkins-and-selenium-grid)
  - [Jenkins and Jira](#jenkins-and-jira)

# Distributed Builds – Master Slave Mode
## Understanding the master and slave architecture
A Jenkins slave node is simply a device configured to act as an automation executor on behalf of the master. The Jenkins master simply represents the base installation of Jenkins. The master will continue to perform basic operations and serve the user interface, while the slaves do the heavy lifting.

![2-1](https://www.safaribooksonline.com/library/view/mastering-jenkins/9781784390891/graphics/B03470_02_01.jpg)

Figure 2-1: A Jenkins master connected to three slave node devices

Some responsibilities that are specific to the Jenkins master and cannot not be delegated to the slave nodes include:

- SCM polling (SVN, GIT, Perforce, and so on)
- Job scheduling
- LDAP authentication
- Build output, reporting, and notifications
- Job history and build logs
- Executing jobs/tasks tied to the master

![2-2](https://www.safaribooksonline.com/library/view/mastering-jenkins/9781784390891/graphics/B03470_02_02.jpg)

Figure 2-2: Expanded Jenkins master and slave connectivity diagram

## Choosing a launch method
The Jenkins new slave node configuration screen provided us with the following available launch methods.

- Launch slave agents via Java Web Start (preferred)
- Launch slave agents on Unix machines via SSH
- Let Jenkins control this Windows slave as a Windows service (using DCOM and WMI is sometimes error prone)
- Launch slave via execution of command on the Master

### Slave agents via SSH tunneling
The SSH launch method provides a number of valuable features that make this an attractive option when connecting Jenkins slave agents to the master. These benefits include:

- More reliable connectivity and stability
- Encrypted communications
- Auto restart and reconnect functionality
- No need for slave services or init.d scripts

![2-13](https://www.safaribooksonline.com/library/view/mastering-jenkins/9781784390891/graphics/B03470_02_12.jpg)

Figure 2-13: SSH Host and Credentials Section

## Administering Jenkins slaves
### The node administration dashboard
![2-14](https://www.safaribooksonline.com/library/view/mastering-jenkins/9781784390891/graphics/B03470_02_13.jpg)

Figure 2-14: Node administration dashboard

![2-15](https://www.safaribooksonline.com/library/view/mastering-jenkins/9781784390891/graphics/B03470_02_14.jpg)

Figure 2-15: Offline slave node marked with an X

### Preventative monitoring
![2-16](https://www.safaribooksonline.com/library/view/mastering-jenkins/9781784390891/graphics/B03470_02_15.jpg)

Figure 2-16: Preventative node monitoring configuration page

### Managing individual slave nodes
![2-17](https://www.safaribooksonline.com/library/view/mastering-jenkins/9781784390891/graphics/B03470_02_16.jpg)

Figure 2-17: Slave node status and configuration

Let's define each of these options and learn what they do:

- Back to List: Navigates back to the node administration dashboard.
- Status: Navigates us back to the status page for the current selected slave node.
- Delete Slave: Removes the slave from the Jenkins master and severs any ties between the slave and the master.
- Configure: Navigates us to the detailed node configuration page.
- Build History: Displays a set of historical timelines of jobs that have run on this slave node.
- Load Statistics: Shows key metrics and resource utilization in graph form. It has three timespan view options: Short, Medium, and Long. These options allow us to adjust the timespan of the graph accordingly.
- Script Console: Jenkins features a robust built-in scripting system called Groovy. With this console, you can run arbitrary one-off scripts directly on the slave node. You will learn more about writing Groovy scripts for Jenkins later.
- Log: Displays in real time the connection status between the Jenkins master and the slave node. These logs can be very valuable when troubleshooting connectivity issues.

## Labels, groups, and load balancing
![2-18](https://www.safaribooksonline.com/library/view/mastering-jenkins/9781784390891/graphics/B03470_02_17.jpg)

Figure 2-18: A basic Windows build pool

### Attaching a slave to a group by creating a label
By labeling multiple slave nodes with the same label, we can create groups. Groups of devices can prove to be handy when offloading automation. Creating a group of slave nodes simply means that they share a common label.

![2-19](https://www.safaribooksonline.com/library/view/mastering-jenkins/9781784390891/graphics/B03470_02_18.jpg)

Figure 2-19: Adding a Windows label to a slave node

![2-20](https://www.safaribooksonline.com/library/view/mastering-jenkins/9781784390891/graphics/B03470_02_19.jpg)

Figure 2-20: A A slave node in one group (based on a label)

### Attaching a slave to many groups
Through Jenkins label and grouping system, Jenkins provides a mechanism by which jobs can run on one or many slave nodes (load balancing).

![2-21](https://www.safaribooksonline.com/library/view/mastering-jenkins/9781784390891/graphics/B03470_02_20.jpg)

Figure 2-21: Attaching a slave node to multiple groups

![2-22](https://www.safaribooksonline.com/library/view/mastering-jenkins/9781784390891/graphics/B03470_02_21.jpg)

Figure 2-22: A slave node belonging to two groups

### Restricting slave execution to global or tied jobs
![2-23](https://www.safaribooksonline.com/library/view/mastering-jenkins/9781784390891/graphics/B03470_02_22.jpg)

Figure 2-23: Usage dropdown in the detailed configuration form

### Jenkins plugins that support distributed builds
At the time of writing this book, some of the more notable master/slave distributed build extension plugins for Jenkins include:

- Amazon EC2 plugin
- Microsoft Azure
- Swarm
- Docker plugin
- Hadoop plugin
- CloudBees Cloud Connector plugin
- Selenium plugin
- vSphere Cloud plugin

# Creating Views and Jobs in Jenkins
## Jobs in Jenkins
![3-7](https://www.safaribooksonline.com/library/view/mastering-jenkins/9781784390891/graphics/B03470_03_07.jpg)

Figure 3-7: New item basic configuration page

Let's discuss each of the available job types and learn about the individual options prescribed for each job:

- Freestyle project: This provides the ability to create a completely custom job that can behave in any way we choose.
- Maven project: This is designed specifically for JAVA Maven projects. It utilizes Production and Operations Management Society (POMS) and provides an easy to use interface for execution of Maven targets.
- Multiconfiguration project: This is designed for projects that have multiple configurations (x86, x64, and so on). It allows you to specify a single job with multiple output types.
- Copy existing job: This allows the user to duplicate the contents of an existing job and alter the name.
- External job: This allows the user to trigger and monitor an external Jenkins job. This external job type is particularly handy when there are multiple Jenkins instances (for example, a development Jenkins instance and a production Jenkins instance) that are responsible for production deployments.

# Advanced Automated Testing
## Quality assurance initiatives and test automation terminology
Let's take a minute to define some quality assurance, and automated testing terminology:

`Unit tests`: Unit tests can be described as tests that run directly on the build machine during the build process and are designed to validate the I/O of classes, methods, objects, and functions.

![5-1](https://www.safaribooksonline.com/library/view/mastering-jenkins/9781784390891/graphics/B03470_Ch5_01.jpg)

Figure 5-1: A unit test structure

`Smoke / BVT (Build Verification tests)`: Smoke tests (more commonly known as build verification tests) validate basic operational functionality of a software project. Generally these tests attempt to identify simplistic operational failures that are catastrophic, and prevent the software from being considered viable for further testing.

![5-2](https://www.safaribooksonline.com/library/view/mastering-jenkins/9781784390891/graphics/B03470_Ch5_02.jpg)

Figure 5-2: A basic smoke test workflow

`Functional tests`: Functional (or acceptance) tests validate the operability of a software project, and ensure the implementation of the software project is in line with functional requirement specifications, and business initiatives.

`Regression tests`: Regression tests aim to reproduce defects identified by users in the field. The ultimate goal of a regression test is to automate the reproduction of a defect, and ensure that the defect does not re appear. Advanced regression testing solutions should aim to provide a system that can visually reproduce a defect for developers based on the entry of a bug tracking ticket identification number. In such a system a developer would simply enter the bug ID into the automated test case execution system, which would then illustrate the steps needed to reproduce a bug on a given environment.

`Capacity tests`: Capacity tests are tests designed to simulate stress and load on an application suite. These tests help ensure that the software can withstand real-world use and abuse. Testing application load and stress capabilities can be accomplished via the implementation of valid use case scenarios, which are then replicated and distributed across multiple simulators.

`Black Box tests`: Black Box tests execute from that same perspective as the end consumer of the software. They have no visibility into the internals of a software project or the system it runs on and can only see the software from the consumer's perspective.

![5-3](https://www.safaribooksonline.com/library/view/mastering-jenkins/9781784390891/graphics/B03470_Ch5_03.jpg)

Figure 5-3: A simple black box test

`White Box tests`: White box tests are tests that have the ability to see into the internals of a software application and can validate file structures, application process ID's, and other internally available information related to the software. White box tests may also have the ability to see into the system that the software is running on and can verify lower-level operational capabilities of the software itself.

![5-4](https://www.safaribooksonline.com/library/view/mastering-jenkins/9781784390891/graphics/B03470_Ch5_04.jpg)

Figure 5-4: White Box testing

`A/B testing`: Understanding customer usage and acceptance of new features within a software project has been a business hurdle for many years. A/B testing allows business interests to propose new features to end-users, collect usage data metrics through analytics, and provide feedback related to the adoption of a proposed feature. These experiment-driven testing solutions allow the business to decide through data metrics when a feature creates customer value, and when it does not, thus allowing the business to focus on features that drive revenue. More advanced implementations of A/B testing solutions allow the business to incrementally expose users to a feature hypothesis and collect real-time feedback on its adoption.

## The Software Development Lifecycle
![5-5](https://www.safaribooksonline.com/library/view/mastering-jenkins/9781784390891/graphics/B03470_Ch5_05.jpg)

Figure 5-5: The Software Development Lifecycle

![5-6](https://www.safaribooksonline.com/library/view/mastering-jenkins/9781784390891/graphics/B03470_Ch5_06.jpg)

Figure 5-6: Continuous Software Development Lifecycle

## Connecting product codes to tests
![5-7](https://www.safaribooksonline.com/library/view/mastering-jenkins/9781784390891/graphics/B03470_Ch5_08.jpg)

Figure 5-7: The Test Driven Development paradigm

## Baking quality into the product
![5-8](https://www.safaribooksonline.com/library/view/mastering-jenkins/9781784390891/graphics/B03470_Ch5_09.jpg)

Figure 5-8: Test coverage pyramid

### Smoke test tip
It is highly recommend that a simplistic smoke test suite be created and executed immediately after the deployment to an environment. The smoke tests will validate the viability of the environment and determine if it is worth testing further.

## Distributed testing solutions
![5-20](https://www.safaribooksonline.com/library/view/mastering-jenkins/9781784390891/graphics/B03470_Ch5_21.jpg)

Figure 5-20: Distributed slave test architectures

# Software Deployments and Delivery
## Standardizing build outputs
Let's look at the basic flow of a generic build process:

1. Obtain a clean copy of the source code from source control.
2. Fetch any dependencies (preferably from an artifact repository).
3. Version stamp any necessary code (may be a pre-compile or post-compile step, depending on the technology stack).
4. Compile the source code and verify syntax.
5. Execute unit tests (unit-based validation of objects, methods, and classes).
6. Collate compiled objects, binaries, or deliverables into a common output directory.
7. Create a package containing the binaries and deliverables.
8. Publish a versioned deliverable to an artifact repository.

### Architecting a packaging scheme
The following diagram shows a simple source control timeline. It describes the lockstep evolution of product code, automation, and tests with regard to packaging:

![6-1](https://www.safaribooksonline.com/library/view/mastering-jenkins/9781784390891/graphics/B03470_06_01.jpg)

Figure 6-1: Suggested packaging scheme

### Build and deployment best practice
The goal of any build system should be to create a package that can be deployed repeatedly. The common phrase is `build once, deploy many`.

### Snapshots and Releases Tip
When implementing a package system, you may consider creating two or more identical packages: one for snapshots, which represents the latest build, and an additional item , which might represent the latest released version. This can be helpful when performing automated deployments and managing dependencies, as the packages could then be retrieved easily, without the need to specify a version number, and could be fetched via a simple static URL.

## Implementing a Definitive Media Library
A `Definitive Media Library (DML)` a term coined by ITIL and often referred to as a DML is recognized as a single source of truth for company software assets, dependencies, and third-party libraries. By nature a DML ensures assets are backed up, checksum verified, and managed appropriately.

### Publishing assets to a DML
#### JENKINS' ARCHIVE THE ARTIFACTS POST-BUILD ACTION
![6-3](https://www.safaribooksonline.com/library/view/mastering-jenkins/9781784390891/graphics/B03470_06_03.jpg)

Figure 6-3: Archive the artifacts

#### PUBLISHING TO ARTIFACTORY
![6-5](https://www.safaribooksonline.com/library/view/mastering-jenkins/9781784390891/graphics/B03470_06_05.jpg)

Figure 6-5: Artifactory architecture

![6-6](https://www.safaribooksonline.com/library/view/mastering-jenkins/9781784390891/graphics/B03470_06_06.jpg)

Figure 6-6: Publishing artifacts to Artifactory

#### PUBLISHING VIA MAVEN
Artifacts can be published to multiple DML solutions, including Sonatype Nexus, Apache Archiva, Exeters Origin, and others via a simple deploy target, which is embedded directly within the Maven architecture.

#### PUSHING A DOCKER CONTAINER
![6-7](https://www.safaribooksonline.com/library/view/mastering-jenkins/9781784390891/graphics/B03470_06_07.jpg)

Figure 6-7: Execute Docker container build step

## Automated deployments
Below is a list of basic deployment steps, which can serve as a template for creating deployment automation.

- A Jenkins deployment job will be triggered, which will be responsible for the deployment.
- Jenkins will need to either push the package to a targeted environment or perform the following steps on the target environment itself (via slave nodes). The deployment job will need to perform the execution of the following actions:
  - Identify the version of the software to be deployed
  - Download the versioned package from the DML
  - Verify the CRC fingerprints of the deployable entity
  - Extract the contents of the package into a temporary folder on the deployment environment.
- Execute the deployment automation in the package to install the software.
- Verify that the deployment was successful through basic sanity tests
- Jenkins will need to determine whether the deployment was a success or a failure due to recognized return codes.

### Retrieving build artifacts and packages
#### FETCHING ARTIFACTS VIA ARCHIVE ARTIFACTS
![6-9](https://www.safaribooksonline.com/library/view/mastering-jenkins/9781784390891/graphics/B03470_06_09.jpg)

Figure 6-9: Copy artifacts build step

#### FETCHING ARTIFACTS FROM ARTIFACTORY
![6-10](https://www.safaribooksonline.com/library/view/mastering-jenkins/9781784390891/graphics/B03470_06_10.jpg)

Figure 6-10: Automation of Artifact repository

#### FETCHING ARTIFACTS VIA MAVEN
Artifact repositories also provide a scalable solution to resolve Maven dependencies. Resolving dependencies in Maven can be done via a simple update of the POM file.

### Leveraging Jenkins slave nodes for deployment
You can follow these basic steps when deploying an application onto a slave node:

1. Download the deployment package from the DML (you could use copy the artifacts here if you use Jenkins as your DML).
2. Verify that the CRC checksums for the package are downloaded.
3. Extract the deployment package (unzip, tar, and so on).
4. Execute the deployment scripts embedded in the package.
5. Run application startup sequences.

# Continuous Practices
## Continuous Integration
`Continuous Integration (CI)` is a development practice that requires developers to integrate code into a shared repository several times a day. Each check-in is then verified by an automated build, allowing teams to detect problems early.

### What Continuous Integration is not
>"Continuous Integration is NOT running Jenkins on your feature branches. Continuous Integration is a practice where every developer integrates their changes to the mainline at least once a day" --Jez Humble

![8-4](https://www.safaribooksonline.com/library/view/mastering-jenkins/9781784390891/graphics/B03470_08_04.jpg)

Figure 8-4: Continuous Integration

To practice Continuous Integration, the software development group must, at a minimum, do the following:

- Implement a trunk-based development model (or a highly disciplined, short-lived feature branch solution), where each developer commits (or merges) code into the mainline at least once per day
- Automate the detection of commits, and initiate a build for every commit detected
- Automate the execution and reporting of unit tests, which must run as part of the build process and aim to validate the code IO operability
- Create a rapid feedback loop system to notify and flag any potential defects detected by the build process
- Place urgency on addressing or reverting any violating code commits that break the build

### Code-based branching techniques
`Branching by abstraction` and `feature toggles` are two additional software architectural techniques that can be employed to alleviate the need for source control based feature branches.

Branching by abstraction is an architectural technique designed to facilitate refactoring efforts and allow replacement parts to co-exist with living implementations without risk.

![8-5](https://www.safaribooksonline.com/library/view/mastering-jenkins/9781784390891/graphics/B03470_08_05.jpg)

Figure 8-5: Branching Abstraction architecture

#### Feature toggles
Feature toggles represent a source code branching technique which, enable or disable functionality based on a condition.

Consider the following code example:

```js
if (bToggle == true) {
   …
} else {
   …
}
```

A more modern example of a feature toggle solution for an HTML/Javascript web project might look like the following:

```js
<script type="text/javascript">
<!--
    function toggle_feature(id)
    {
       var e = document.getElementById(id);
       if(e.style.display == 'block')
          e.style.display = 'none';
       else
          e.style.display = 'block';
    }
//-->
</script>

<a href="#" onclick="toggle_feature('PrototypeFeature');">Click here to view the prototype effort</a>

<div id="PrototypeFeature">This feature is hidden from view until its toggled on</div>
```

- Feature toggles in Java:
  - Togglz: http://www.togglz.org
  - FF4J: http://www.ff4j.org
  - Fitchy: https://code.google.com/p/fitchy/
- Feature toggles in Python:
  - Gargoyle: https://pypi.python.org/pypi/gargoyle
  - Gutter: https://github.com/disqus/gutter
- Feature Toggles in Embedded/C/C++ (Constructs) (coding techniques):
  - Ifdef
  - Make targets

### Continuous Integration in Jenkins
#### SCM POLLING
Polling a source control solution for changes can be configured in the job configuration page.

#### RUNNING A JENKINS JOB VIA THE SVN POST-COMMIT HOOKS
In addition to SCM polling, a Jenkins job can be triggered through an SVN post-commit hook (push).

#### TRIGGERING A JENKINS JOB VIA GITHUB PUSH
![8-9](https://www.safaribooksonline.com/library/view/mastering-jenkins/9781784390891/graphics/B03470_08_09.jpg)

Figure 8-9: GitHub plugin configuration

## Continuous Delivery
`Continuous Delivery (CD)` represents the expansion of Continuous Integration practices.Continuous Delivery adds automated deployments and acceptance test verification automation to the solution and ensures the software project is in an always-releasable state.

![8-10](https://www.safaribooksonline.com/library/view/mastering-jenkins/9781784390891/graphics/B03470_08_10.jpg)

Figure 8-10: Continuous Delivery workflow

When implementing a continuous delivery solution, there are a few key points that we should keep in mind:

- Keep the build fast
- Illuminate the failures, and recover immediately
- Make deployments push-button, for any version to any environment
- Automate testing and validation operations with defined buckets for each logical test group (unit, smoke, functional, and regression)
- Use feature toggles to avoid branching
- Get feedback early and often (automation feedback, test feedback, build feedback, and UAT feedback)

## Continuous Deployment
![8-20](https://www.safaribooksonline.com/library/view/mastering-jenkins/9781784390891/graphics/B03470_08_20.jpg)

Figure 8-20: Differentiation between Continuous Delivery and Continuous Deployment

If the business unit indeed desires to migrate towards a Continuous Deployment solution, tight controls on quality will be required to facilitate stability and avoid outages. These controls may include any of the following:

- The required unit testing with code coverage metrics
- The required a/b testing or experiment-driven development
- Paired programming
- Automated rollbacks
- Code reviews and static code analysis implementations
- Behavior-driven development (BDD)
- Test-driven development (TDD)
- Automated smoke tests in production

### Continuous Deployment in Jenkins
![8-21](https://www.safaribooksonline.com/library/view/mastering-jenkins/9781784390891/graphics/B03470_08_21.jpg)

Once the promotions become automatic, the build automation solutions will continuously deploy for every commit to the mainline (given that all the automated tests have been passed).

# Integrating Jenkins with Other Technologies
## Jenkins and Docker – Linux guide
- Running Jenkins inside a Docker container – Linux
- Dynamic Jenkins slave nodes using Docker

## Integrating Jenkins with Ansible – Linux and Windows
![9-6](https://www.safaribooksonline.com/library/view/mastering-jenkins/9781784390891/graphics/B03470_09_06.jpg)

Figure 9-6: The Ansible Pull architecture

![9-7](https://www.safaribooksonline.com/library/view/mastering-jenkins/9781784390891/graphics/B03470_09_07.jpg)

Figure 9-7: The Ansible Push architecture

## Jenkins and Artifactory
Jfrog's Artifactory (and Sonatype Nexus) have been pivotal advocates for Continuous Delivery implementations for some time now. Artifactory provides a set of centrally configurable repositories, which can be leveraged to facilitate uploading, storing, downloading, and fetching build packages, Docker containers (Docker registries through Artifactory requires the Pro version), and binary assets.

![9-12](https://www.safaribooksonline.com/library/view/mastering-jenkins/9781784390891/graphics/B03470_09_12.jpg)

Figure 9-12: The basic Artifactory architecture

## Jenkins and Selenium Grid
A Selenium Grid provides a distributed automated testing solution that executes test cases in parallel.

![9-15](https://www.safaribooksonline.com/library/view/mastering-jenkins/9781784390891/graphics/B03470_09_15.jpg)

Figure 9-15: Selenium distributed architecture

## Jenkins and Jira
Jenkins and Jira
Atlassian's Jira (http://www.atlassian.com) has quickly become an industry-wide powerhouse for tracking Agile efforts, managing development implementation queues, and providing project management solutions for software teams.
