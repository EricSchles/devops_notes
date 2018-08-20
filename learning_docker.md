# Introduction

Docker is a container platform for making apps portable

## Introductory commands

`docker run -it [IMAGE NAME] /bin/bash`

This runs the docker image in interactive mode running bash.  Which is made possible by specifying the `/bin/bash`.  Note: anything could be used as the executable portion of the command for instance,

`docker run -it [IMAGE NAME] /usr/local/bin/python`

would run the python repl.  This assumes that the executable is on the image you are running, it doesn't "magically" work.

`docker exec -it [CONTAINER ID] [COMMAND EXECUTABLE]`

You can find the [CONTAINER ID] from `docker ps`.  This only works on currently running containers.

Note: `docker ps -a` gives all containers that have ever run.

`docker run -d [IMAGE NAME] --name [UNIQUE NAME OF YOUR CHOICE] -v [ABSOLUTE FILE PATH ON HOST OS]:[ABSOLUTE FILE PATH ON CONTAINER]`

optionally you can do

`docker run -d [IMAGE NAME] --name [UNIQUE NAME OF YOUR CHOICE] -v [ABSOLUTE FILE PATH ON HOST OS]:[ABSOLUTE FILE PATH ON CONTAINER] -it [COMMAND EXECUTEABLE]`

So for instance:

`docker run -d [IMAGE NAME] --name [UNIQUE NAME OF YOUR CHOICE] -v [ABSOLUTE FILE PATH ON HOST OS]:[ABSOLUTE FILE PATH ON CONTAINER] -it /bin/bash`

