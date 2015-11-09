Bitcoin core docker image
=========================

Docker image of Bitcoin core client.


Locations
---------

Source of the image is hosted on Bitbucket at
https://bitbucket.org/beli-sk/docker-bitcoin

If you find any problems, please post an issue at
https://bitbucket.org/beli-sk/docker-bitcoin/issues

The built image is located on Docker Hub at
https://hub.docker.com/r/beli/bitcoin/


Pull or build
-------------

The image is built automatically on Docker hub in repository **beli/firefox**
and can be pulled using command

    docker pull beli/bitcoin

or if you'd prefer to build it yourself from the source repository

    git clone https://bitbucket.org/beli-sk/docker-bitcoin.git
    cd docker-bitcoin/
    docker build -t beli/bitcoin .



Usage
-----

Run the container in the background

    docker run -d beli/bitcoin

The container exposes ports 8333 for bitcoin protocol and 8332 for RPC.

