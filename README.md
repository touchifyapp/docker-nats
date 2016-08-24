# Supported tags and respective Dockerfile links

*  [`0.9.4`, `0.9`, `latest` (Dockerfile)](https://github.com/touchifyapp/docker-nats/blob/master/Dockerfile)

This image is updated via [pull requests to the `touchifyapp/docker-nats` GitHub repo](https://github.com/touchifyapp/docker-nats/pulls).

# [NATS](http://nats.io): A high-performance cloud native messaging system.

![NATS logo](https://raw.githubusercontent.com/docker-library/docs/45d33e1726fed03a2a40363a9699e0587e713c55/nats/logo.png)

`nats` is a high performance server for the NATS Messaging System.

## How to use

### As a simple container

```
# Run a NATS server
# Each server exposes multiple ports
# 4222 is for clients.
# 8222 is an HTTP management port for information reporting.
# 6222 is a routing port for clustering.
# use -p or -P as needed.

$ docker run -d --name nats-main touchify/nats
```

### As a Docker 1.12 service cluster

```
# Create a network overlay
$ docker network create -d overlay events

# Run a NATS cluster.
# Use NATS_SERVICE_NAME variable to configure the cluster name.

$ docker service create \
$     --name nats-cluster \
$     --env NATS_SERVICE_NAME=nats-cluster \
$     --network events \
$     --replicas 3 \
$     touchify/nats
```

## Environments variables

```
Cluster Options:
    NATS_SERVICE_NAME                For use in Docker 1.12 in Swarm mode.
                                     Should equal to Docker service name in Swarm.
                                     Used to configure the NATS cluster.

Cluster authentication Options :
    NATS_CLUSTER_USER                User for cluster authentication.
    NATS_CLUSTER_PASSWORD            Password for cluster authentication.
    NATS_CLUSTER_TIMEOUT             Timeout for cluster authentication.
```

## Command line options

```
Server Options:
    -a, --addr HOST                  Bind to HOST address (default: 0.0.0.0)
    -p, --port PORT                  Use PORT for clients (default: 4222)
    -P, --pid FILE                   File to store PID
    -m, --http_port PORT             Use HTTP PORT for monitoring
    -ms,--https_port PORT            Use HTTPS PORT for monitoring
    -c, --config FILE                Configuration File

Logging Options:
    -l, --log FILE                   File to redirect log output
    -T, --logtime                    Timestamp log entries (default: true)
    -s, --syslog                     Enable syslog as log method
    -r, --remote_syslog              Syslog server addr (udp://localhost:514)
    -D, --debug                      Enable debugging output
    -V, --trace                      Trace the raw protocol
    -DV                              Debug and Trace

Authorization Options:
        --user user                  User required for connections
        --pass password              Password required for connections
        --auth <token>               Authorization token required for connections

TLS Options:
        --tls                        Enable TLS, do not verify clients (default: false)
        --tlscert FILE               Server certificate file
        --tlskey FILE                Private key for server certificate
        --tlsverify                  Enable TLS, very client certificates
        --tlscacert FILE             Client certificate CA for verification

Cluster Options:
        --routes <rurl-1, rurl-2>    Routes to solicit and connect
        --cluster <cluster-url>      Cluster URL for solicited routes
        --no_advertise <bool>        Advertise known cluster IPs to clients

Common Options:
    -h, --help                       Show this message
    -v, --version                    Show version
        --help_tls                   TLS help.
```

## License

View [license information](https://github.com/touchifyapp/docker-nats/blob/master/LICENSE) for the software contained in this image.

## Supported Docker versions

This image is officially supported on Docker version 1.12+.

Please see [the Docker installation documentation](https://docs.docker.com/installation/) for details on how to upgrade your Docker daemon.

## User Feedback

### Documentation

Documentation for this image is stored in [the `touchifyapp/docker-nats` GitHub repo](https://github.com/touchifyapp/docker-nats).
Be sure to familiarize yourself with the repository's README.md file before attempting a pull request.

### Issues

If you have any problems with or questions about this image, please contact us through a [GitHub issue](https://github.com/touchifyapp/docker-nats/issues).

### Contributing

You are invited to contribute new features, fixes, or updates, large or small; we are always thrilled to receive pull requests, and do our best to process them as fast as we can.

Before you start to code, we recommend discussing your plans through a [GitHub issue](https://github.com/touchifyapp/docker-nats/issues), especially for more ambitious contributions. This gives other contributors a chance to point you in the right direction, give you feedback on your design, and help you find out if someone else is working on the same thing.
