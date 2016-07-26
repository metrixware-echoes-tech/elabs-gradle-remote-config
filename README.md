
# elabs-gradle-remote-config
This repo hosts a set of gradle build scripts to be used as remote plugins using 'apply from: "http://..../"'

## Required Properties from User Config

In order to upload archives to the nexus repository, two global variables must be set. 
  * **```mavenUser```** : user login on the Nexus server;
  * **```mavenPassword```** : user password on the Nexus server.

These two variables should not be shared among developers, thus one must declare them in the ```~/.gradle/gradle.properties``` file.

sonarURL
