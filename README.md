# Build Parent

[![SonarCloud](https://sonarcloud.io/images/project_badges/sonarcloud-white.svg)](https://sonarcloud.io/summary/new_code?id=ikmdev_tinkar-core)
[![Security Rating](https://sonarcloud.io/api/project_badges/measure?project=ikmdev_tinkar-core&metric=security_rating)](https://sonarcloud.io/summary/new_code?id=ikmdev_tinkar-core)
[![Coverage](https://sonarcloud.io/api/project_badges/measure?project=ikmdev_tinkar-core&metric=coverage)](https://sonarcloud.io/summary/new_code?id=ikmdev_tinkar-core)

A Simple maven build parent that configures and customizes builds for all child modules.  This can be used
by any project that would like to inherit these build configurations. This includes a number of the compiling,
code quality, code style, and plugin configurations of Tinkar and related HL7 projects.

The output of this project is solely a pom file and is distributed via standard Maven release procedures.

### Team Ownership - Product Owner
Automation/Devops Team

## Getting Started

Required for running this:

1. Download and install Open JDK Java 21
2. Download and install Apache Maven 3.9.8 or later
3. Download and install Git

## Building and Running

Follow the steps below to build and run Komet on your local machine:

1. Clone the repository from GitHub to your local machine

2. Change local directory to cloned repo location

3. Enter the following command to build the application:

Unix/Linux/OSX:

```bash
./mvnw clean install
```

Windows:

```bash
./mvnw.cmd clean install
```

## How to Contribute
=======
## Issues and Contributions
Technical and non-technical issues can be reported to the [Issue Tracker](https://github.com/ikmdev/build-parent/issues).

Contributions can be submitted via pull requests. Please check the [contribution guide](doc/how-to-contribute.md) for more details.
