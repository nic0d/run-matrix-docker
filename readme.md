
# Introduction

Dockerfile for installation of [matrix] open federated Instant Messaging and
VoIP communication server.

[matrix]: matrix.org

Credits to https://github.com/allmende/docker-matrix



# Config files generation & and server launch with Compose

You can generate the example configuration into `/srv/matrix/data` with

    docker-compose -f generate.yml up

Then enable the registration on the server: (in the file homeserver.yml, which is available at /srv/matrix/data if if you did not modify the generate.yml)

```
# Enable registration for new users.
enable_registration: True
``` 

Then run the Matrix, Vector & Coturn server

    docker-compose -d up

At this point :

- Matrix server should be available at : https://localhost:8448
- Vector server should be available at : https://localhost:8080

Debugging the images happens with

    docker-compose down

To debug the environments instead of the source images, use

    docker-compose stop
    docker-compose rm

instead.
