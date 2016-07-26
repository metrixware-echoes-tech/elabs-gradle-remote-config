
# elabs-gradle-remote-config
This repo hosts a set of gradle build scripts to be used as remote plugins using 'apply from: "http://..../"'

## Overview 

The goal of this gradle configuration is to provide a set of build script that can be reused among projects with several modules. The scripts force a way of organizing a multi project repository that is common among the company, in order to facilitate grasping the code architecture. It also centralize the configuration in one file.

Note that with the current configuration, the root project should not contain any code (though, markdown files in ```src/main/doc``` are processed).

## Configuration

The file ```gradle.properties``` at the root of the project's hierarchy defines all the relevant information required to build the project.

```init.gradle``` configures some constants using data from the ```gradle.properties``` and the system. For intance, some variables are initialized using the current date, and the footer for the documentation is initialized by combining date, author, website, contact, ....

The different parts are included in the ```build.gradle``` script (see the sample one) using the ```apply from: http://$gradleConfigUrl/script.gradle``` directive. The ```$gradleConfigUrl``` variable is declared in the ```gradle.properties``` files with the value ```https://raw.githubusercontent.com/echoes-tech/elabs-gradle-remote-config/master/``` (raw access to the github files).

## Required Properties from User Config

In order to upload archives to the nexus repository, two global variables must be set. 
  * **```mavenUser```** : user login on the Nexus server;
  * **```mavenPassword```** : user password on the Nexus server.

These two variables should not be shared among developers, thus one must declare them in the ```~/.gradle/gradle.properties``` file.

The ```sonarUrl``` variable is used to specify the URL for the sonarQube server. It can be shared among developers, or be specficied locally, i.e. ```http://localhost:9000/```.
