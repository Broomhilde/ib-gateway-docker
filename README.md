# IB Gateway docker

![Build test](https://github.com/manhinhang/ib-gateway-docker/workflows/Build%20test/badge.svg?branch=master)
[![Docker Pulls](https://img.shields.io/docker/pulls/manhinhang/ib-gateway-docker)](https://hub.docker.com/r/manhinhang/ib-gateway-docker)
[![GitHub](https://img.shields.io/github/license/manhinhang/ib-gateway-docker)](https://github.com/manhinhang/ib-gateway-docker/blob/develop/LICENSE)

lightweight interactive brokers gateway docker

It's just pure `IB Gateway` and don't include any VNC service (for security reason, I don't like expose extra port)

This docker image just installed:

- [IB Gateway](https://www.interactivebrokers.com/en/index.php?f=16457) (latest)

- [IBC](https://github.com/IbcAlpha/IBC) (3.8.2)

- [ib_insync](https://github.com/erdewit/ib_insync) (latest)

## Pull the Docker image from Docker Hub

```bash
docker pull manhinhang/ib-gateway-docker
```

## Build & Run locally

```bash
docker build -t ib-gateway-docker .
docker run -d ib-gateway-docker \
--env IB_ACCOUNT= \ #YOUR_USER_ID 
--env IB_PASSWORD= \ #YOUR_PASSWORD  
--env TRADE_MODE= \ #paper or live 
tail -f /dev/null
```

### Create a container from the image and run it
```bash
docker run -d \
--env IB_ACCOUNT= \ #YOUR_USER_ID 
--env IB_PASSWORD= \ #YOUR_PASSWORD  
--env TRADE_MODE= \ #paper or live 
manhinhang/ib-gateway-docker tail -f /dev/null
```

## Container usage example

This example demonstrated how to connect `IB Gateway`

Example Code: [examples/ib_insync](./examples/ib_insync)

# Tests

The [test cases](test/test_ib_gateway.py) written with testinfra.

Run the tests

```
pytest
```

# Github Actions for continuous integration

After forking `IB Gateway docker` repository, you need config your **interactive brokers** paper account & password in *github secret*

| Key | Description |
| - | - |
| IB_ACCOUNT | your paper account name |
| IB_PASSWORD | your paper account password |

# Disclaimer

This project is not affiliated with [Interactive Brokers Group, Inc.'s](https://www.interactivebrokers.com).

Good luck and enjoy.

