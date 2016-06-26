Ignite Primed Cache Example
==============

A simple example that demonstrates building a docker image that contains a primed Ignite node. This means once the image is run for the first time data will be preloaded as it is packaged with the actual docker image. 

<h3> Prerequisites </h3>
==========

1. Install Apache Ignite
    - https://apacheignite.readme.io/docs/getting-started#installation
2. Install Docker
    - https://docs.docker.com/engine/installation/

<h3> Running the example </h3>
==========

1. Build the docker image:
    - Navigate to the `docker` directory in the project
    - Execute: `sudo docker build . -t cache-store-example`
    - This will build the necessary docker image
2. Run the image:
    - `sudo docker run -it --net=host cache-store-example`
