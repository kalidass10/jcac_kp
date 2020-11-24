# Jcac-jenkins

Spinup jenkins using JCAC plugin template and run docker as slave.

## How to build

For building docker base images we should build it manually:

usage:

    docker build -t base_image:${image-directory}_${version}

where: `${image-directory}` is a directory where `Dockerfile` exist and `${version}` is in the [Semantic Versioning](https://semver.org/) form.

## Docker deamon permission

    sudo chmod 777 /var/run/docker.sock

## How to use infrastructure image

usage: 

    docker run -d --name {container-name} -p 8080:8080 -v /var/run/docker.sock:/var/run/docker.sock -v /usr/bin/docker:/usr/bin/docker base_image:${image-directory}_${version}

where: `${container-name}` is a userdefined container name # example : `${myjenkins}`

    docker ps -a # list the containers 
    docker logs {container-name}

## How to create Docker slave

usage:

    Managejenkins > manage cloud/node>configurecloud>click on test connection

Output: 
    Version = 19.03.13, API Version = 1.40

    Enabled
    save

