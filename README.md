
# Introduction

docker-compose files for installation of [matrix] open federated Instant Messaging and
VoIP communication server.

[matrix]: matrix.org

* matrix server: synapse
* UI : Vector.im
* VoIP communication server : Coturn

Credits to https://github.com/allmende/docker-matrix

# Requirements
 
- docker
- docker-compose
- writable access right on the file system of the host by the user docker on the path /srv/matrix/data.


# Config files generation & and server launch with Compose

The deployment is divided in two phases. First, the configuration files and the certificate are generated. The second phase is the execution of the servers. Currently a manual step is required between the two phases (user registration activation).

You can generate the example configuration into `/srv/matrix/data` with this command:

```
docker-compose -f generate.yml up
```

Then enable the registration on the server: (in the file homeserver.yml, which is available at /srv/matrix/data if you did not modify the generate.yml)

```
# Enable registration for new users.
enable_registration: True
``` 

Then run the Matrix, Vector & Coturn server

    docker-compose up

NB: you can optionally add the option -d (for 'detached') to launch the containers in background.

At this point :

- Matrix server should be available at : https://localhost:8448
- Vector server should be available at : https://localhost:8080

You have to set the homeserver to https://localhost:8448 (for now it points to the server of allmende.io, it will change in the future).

Debugging the images happens with

    docker-compose down

To debug the environments instead of the source images, use

    docker-compose stop
    docker-compose rm

instead.
