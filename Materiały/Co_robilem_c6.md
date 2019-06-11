## Instalowanie dockera

Spróbowałem zrobić z tutorailem [tutaj](https://docs.docker.com/install/linux/docker-ce/ubuntu/)

### Odpalenie kontenera
stud@se ~ $ docker run hello-world

Hello from Docker!
This message shows that your installation appears to be working correctly.

To generate this message, Docker took the following steps:
 1. The Docker client contacted the Docker daemon.
 2. The Docker daemon pulled the "hello-world" image from the Docker Hub.
    (amd64)
 3. The Docker daemon created a new container from that image which runs the
    executable that produces the output you are currently reading.
 4. The Docker daemon streamed that output to the Docker client, which sent it
    to your terminal.

To try something more ambitious, you can run an Ubuntu container with:
 $ docker run -it ubuntu bash

Share images, automate workflows, and more with a free Docker ID:
 https://hub.docker.com/

For more examples and ideas, visit:
 https://docs.docker.com/get-started/

### Kontener stale działający
stud@se ~ $ docker run busybox
stud@se ~ $ docker ps
CONTAINER ID        IMAGE               COMMAND             CREATED             STATUS              PORTS               NAMES
05efa6d76641        cirros              "/sbin/init"        3 seconds ago       Up 3 seconds                            jovial_bell

## Spróbuję postawić kontener z serwerem WWW
[tutorial](https://www.tecmint.com/install-apache-web-server-in-a-docker-container/)

Wkleiłem swoją stronę z WWW.

sudo docker run -dit --name tecmint-web -p 8080:80 -v /home/stud/www:/usr/local/apache2/htdocs/ httpd:2.4


12  sudo docker run -dit --name tecmint-web -p 8080:80 -v /home/stud/www:/usr/local/apache2/htdocs/ httpd:2.4
   13  sudo docker run -dit -p 8080:80 -v /home/stud/www:/usr/local/apache2/htdocs/ httpd:2.4

stud@s3 ~ $ sudo docker run -dit --name tecmint-web -p 8080:80 -v /home/stud/www:/usr/local/apache2/htdocs/ httpd:2.4
Unable to find image 'httpd:2.4' locally
2.4: Pulling from library/httpd
743f2d6c1f65: Pull complete 
c92eb69846a6: Pull complete 
2211b052800a: Pull complete 
a8f7283e297c: Pull complete 
a72363db8c78: Pull complete 
Digest: sha256:6eceaadeab70e6355edb3fef41b8c0b34cafd9b00a17252c875530dcc2d98522
Status: Downloaded newer image for httpd:2.4
7e32df454666b8595f046c31c71606245db8be161d86089f0c9fed3fd01c1ef8

stud@s3 ~/www $ docker ps
CONTAINER ID        IMAGE               COMMAND              CREATED             STATUS              PORTS                  NAMES
5ebacadfa869        httpd:2.4           "httpd-foreground"   6 minutes ago       Up 6 minutes        0.0.0.0:8080->80/tcp   quizzical_easley

Ta linia zadziałała  
sudo docker run -dit -p 8080:80 -v /home/stud/www:/usr/local/apache2/htdocs/ httpd:2.4

Potem wkleiłem do katalogu www moją stronę

Podłączenie do **http://s3:8080/**
