
# Running OpenLava in docker containers.

This repo is a start to show how to run [openlava](http://www.openlava.org/) within docker containers using docker-compose.

Run docker-compose: 

    $ docker-compose up -d                 
    Recreating devopsopenlava_master_1...
    Recreating devopsopenlava_node2_1...
    Recreating devopsopenlava_node3_1...
    Recreating devopsopenlava_node1_1...

List the started containers:

    $ $ docker ps
    CONTAINER ID        IMAGE                          COMMAND             CREATED             STATUS              PORTS                     NAMES
    da5b77edacef        devopsopenlava_node1:latest    "/bin/bash"         5 minutes ago       Up 5 minutes                                  devopsopenlava_node1_1    
    de75b5f22136        devopsopenlava_node3:latest    "/bin/bash"         5 minutes ago       Up 5 minutes                                  devopsopenlava_node3_1    
    c26929f67ec9        devopsopenlava_node2:latest    "/bin/bash"         5 minutes ago       Up 5 minutes                                  devopsopenlava_node2_1    
    90f161d7be33        devopsopenlava_master:latest   "/bin/bash"         5 minutes ago       Up 5 minutes        6322-6325/tcp, 6322/udp   devopsopenlava_master_1    

And attach to a container to start playing:

    $ docker attach devopsopenlava_master_1
    root@master:/openlava-2.2# vi /etc/hosts 
    root@master:/openlava-2.2# service openlava start
    /etc/init.d/openlava: 29: /etc/init.d/openlava: killall: not found
    Starting daemons...
    lim started
    res started
    sbatchd started
    root@master:/openlava-2.2# lsid
    openlava project 2.2, Jun 11 2015

    My cluster name is openlava
    My master name is master
    root@master:/openlava-2.2# bhosts
    HOST_NAME          STATUS       JL/U    MAX  NJOBS    RUN  SSUSP  USUSP    RSV 
    master             ok              -      4      0      0      0      0      0
    node1              ok              -      1      0      0      0      0      0
    node2              ok              -      1      0      0      0      0      0
    node3              ok              -      1      0      0      0      0      0

## TODO:

 * fix last remaining manual steps (e.g. fixing /etc/hosts)
 * autostart openlava service
 * fix killall issue
 * run lim, res, etc within docker (turtles all the way)
 * expose right ports to outside world

