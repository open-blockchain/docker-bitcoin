Bitcoin core docker image
=========================

Docker image of Bitcoin client.


Versions
--------

Available Docker Hub tags / Git branches:

**xt** - Bitcoin XT from official apt repository maintained by Bitcoin XT developers
**core** - Bitcoin Core from Debian Sid
**latest/master** - points to *xt*


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

The image is built automatically on Docker hub in repository **beli/bitcoin**
and can be pulled using command

    docker pull beli/bitcoin

or if you'd prefer to build it yourself from the source repository

    git clone https://bitbucket.org/beli-sk/docker-bitcoin.git
    cd docker-bitcoin/
    docker build -t beli/bitcoin .



Usage
-----

Configuration parameters can be passed as enviromnent variables to
the container in format:

    CONF_<PARAMETER_NAME>=<value>

so for example:

    CONF_RPCPASSWORD=changeme

would set `rpcpassword=changeme`. The `CONF_RPCPASSWORD` parameter is required.

For parameters which can be passed multiple times, specify multiple values
separated by a pipe symbol (|). That also means the pipe symbol can not be
otherwise used in a parameter value.

The container exposes ports 8333 for bitcoin protocol and 8332 for RPC.

It is also recommended to map a volume for the bitcoin client data directory
at `/bitcoin/data` inside the container for permanently storing the blockchain
database and wallet. The volume should be owned and writable by UID 1000 for
Bitcoin Core and UID 105 / GID 108 for Bitcoin XT.

So to run the container in the background, you would do something like this:

    docker run -d -v ~/bitcoin:/bitcoin/data -e CONF_RPCPASSWORD=changeme beli/bitcoin

Please don't forget to change the password to something more secure.

Or use *docker-compose* in the source directory and either pass `CONF_RPCPASSWORD`
as environment variable to docker compose or edit `docker-compose.yml`.
