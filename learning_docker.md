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

## Pushing a docker image to docker hub

`docker push [DOCKERHUB USER NAME]/[IMAGE NAME]`


## Using a Dockerfile

Once you have made an application and created a Dockerfile, the next step is to containerize your application.

In order to do this, run the following commands:


You can also specify a tag with a : like so:

`docker build -t [IMAGE NAME]:[IMAGE TAG] [RELATIVE PATH]`

the `-t` flag let's you name the image

If you are using the current directory you can do the following:

`docker build -t [IMAGE NAME]:[IMAGE TAG] .`

because `.` is the current working directory.

If you have multiple dockerfiles in the same directory, you name them with an extension, for instance:

`Dockerfile.[EXTENSION NAME]`, for example:

`Dockerfile.pythonapp`

If you want to build that specific Dockerfile then you do,

`docker build -t [IMAGE NAME]:[IMAGE TAG] -f Dockerfile.[EXTENSION NAME] .`

Once the docker file has built, you can run your docker container as follows:

`docker run -p [EXTERNALLY EXPOSED PORT]:[DOCKER EXPOSED PORT] [IMAGE NAME]`

You can also specify environment variables like so:

`docker run -e [ENVIRONMENT VARIABLE NAME]=[ENVIRONMENT VARIABLE VALUE] [IMAGE NAME]`

You can also run a docker container in detached mode, which is the same thing as running it as a daemon or background task or background process like so:

`docker run -d [IMAGE NAME]`

It's important to note that you'll get an error if the port is in use:

If you want to only want the docker container to persist while it is running, the following pattern is useful:

`docker run --rm -it [IMAGE NAME] [EXECUTION COMMAND]`

Notice the `--rm` this is what removes the docker container once it has completed.  Otherwise the container will persist on your machine after the command is run.

`docker logs -f [CONTAINER NAME]`

This will give you the logs for the container.  Generally speaking, logs are information broadcast over standard in / standard out through the machine.

`docker exec -it [CONTAINER NAME] [EXECUTION COMMAND]`

this command allows you to execute commands into a already running container.  Note, this is different than `docker run` because it does not start up a container.  The typical case is to use `docker exec` for debugging and therefore bash is an obvious or typical command to run in conjunction.



