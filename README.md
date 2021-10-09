# Logging-drivers-Docker

Docker includes multiple logging mechanisms to help you get information from running containers and services. These mechanisms are called logging drivers.

Steps to 
    - Configure the default logging driver
    - Configure the logging driver for a container
    - Configure the delivery mode of log messages
    
```

1. Use the following command to navigate to daemon.json and open it and add the following code in the daemon.json file to set the logging driver to syslog::
$ sudo nano /etc/docker/daemon.json
"log-driver": "syslog"

2. Use the following command to restart the Docker daemon:
$ sudo service docker restart

3. Use the following command to check the current default logging driver:
$ sudo docker info --format '{{.LoggingDriver}}’

4. Use the following command to start a nginx container with the journald logging driver:
$ sudo docker run -it --log-driver journald --name mycustom nginx
$ sudo docker ps -a

5. Use the following command to check the current logging driver for a running container:
$ sudo docker inspect -f \
'{{.HostConfig.LogConfig.Type}}' mycustom

6. Use the following command to start a busybox container with log-output in non-blocking mode and a 3-megabyte buffer:
$ sudo docker run -it --log-opt mode=non-blocking \
--log-opt max-buffer-size=3m --name busybox_container busybox

7. Use the following command to inspect a container for LogConfig:
$ sudo docker inspect busybox_container

```

