
# Running OpenLava in docker containers.

Run docker-compose: 

    $ docker-compose up -d
    Recreating devopsopenlava_master_1...
    Recreating devopsopenlava_node1_1...

List the started containers:

    $ docker ps
    CONTAINER ID        IMAGE                          COMMAND             CREATED             STATUS              PORTS                                                      NAMES
    6439db1e27ae        devopsopenlava_node1:latest    "/bin/bash"         2 seconds ago       Up 1 seconds        6322-6325/tcp, 6322/udp                                    devopsopenlava_node1_1    
    39aa9a6f96a0        devopsopenlava_master:latest   "/bin/bash"         3 seconds ago       Up 1 seconds        0.0.0.0:6322->6322/udp, 0.0.0.0:6322-6325->6322-6325/tcp   devopsopenlava_master_1   

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

## TODO:

 * fix last remaining manual steps (adding node1 to /etc/hosts on master)
 * autostart openlava service
 * fix killall issue
 * run lim, res, etc within docker (turtles all the way)

