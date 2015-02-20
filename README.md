# Docker implementation of weewx in simulator mode

This small set of files lets you spin up a working Docker instance of weewx on top of minimal ubuntu within just a minute or two, depending on your bandwidth.

It installs nginx for the webserver, and also enables ssh for logging into the container for debugging purposes.

The root password is 'root' which you should of course change to something suitably obscure for you.

Yes, I called the resulting image 'weebuntu' :-)

## build instructions

    make a working directory
    cd into there
    copy the Dockerfile and supervisord.conf files into that directory

### build the image with the desired image tag name
    docker build -t weebuntu .

### verify your image is available in docker

    $ docker images
    REPOSITORY          TAG                 IMAGE ID            CREATED             VIRTUAL SIZE
    weebuntu            latest              62ae86bf4f67        14 hours ago        323.6 MB
    ubuntu              latest              4d6ce913b130        4 days ago          84.98 MB
 
### run the image in a new container
    $ docker run -d -p 80 -p 22 weebuntu
    00a256c24b2b97342fc8a5768e1aeab6cfa6d17df159550e738319dded6c8931
    $ docker ps -a
    CONTAINER ID        IMAGE               COMMAND                CREATED             STATUS              PORTS                                          NAMES
    00a256c24b2b        weebuntu:latest      "/usr/bin/supervisor   9 seconds ago       Up 8 seconds       
    0.0.0.0:49228->22/tcp, 0.0.0.0:49229->80/tcp   drunk_jang
    
See the Dockerfile here for more info at the top...

