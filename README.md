Bitcoin core docker image
=========================

Docker image of Bitcoin Core from Debian Sid.

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
database and wallet. The volume should be owned and writable by UID 1000.

So to run the container in the background, you would do something like this:

    docker run -d -v ~/bitcoin:/bitcoin/data -e CONF_RPCPASSWORD=changeme beli/bitcoin

Or use *docker-compose* in the source directory and either pass `CONF_RPCPASSWORD`
as environment variable to docker compose or edit `docker-compose.yml`.
