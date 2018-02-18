# Framework for Building Containers

## Installation:

The framework is installed as a submodule within the `build` folder. In the root folder of your GIT project, type the following:
```
git submodule add https://github.com/ballab1/container_build_framework.git build/container_build_framework
```

The framework gets copied into `tmp` folder in the build environemt along with the other scripts and customizations.
Once installed in a GIT project, configure the project default configuration by running 
```
build/container_build_framework/bin/setupContainerFramework
```

Installing the framework, will setup a `contaner` folder in the build folder. This contains subfloders for each of the action categories performed.

Folder | Action
--- | --- 
01.packages |  Install needed OS Support
02.users_groups | Verify users and groups exist
03.downloads | Download & verify external packages
04.applications | Install applications
05.customizations | Add customizations and configuration
06.permissions | Make sure that ownership & permissions are correct
07.cleanup | Clean up 

The **/tmp/build** script, called form the *DockerFile*, loads the framework library scripts, then iterates in order, across the coresponding directories in the `container` folder.
If a folder contains any files, they are processed, otherwise it is skipped. Similarly, if a folder does not exist in the `container' direcoty, it is skipped.

![build folder contents](https://github.com/ballab1/container_build_framework/blob/dev/refactor/docs/build_folder_contents.png) 

## Custom Folders

The `build` folder alos contains zero or more **custom folders**. Theese folders are copied to the root of the of the file system of the container. This allows creation of files and subfolders which will be as-is inside your container. No errors occur when any of these folders do not exist.


## Container Folder
The `container` folder contains the instructions for the framework.

![actions folder](https://github.com/ballab1/container_build_framework/blob/dev/refactor/docs/action_folders.png) 
