# Ryu in Docker

This repository is modified and optimized based on [WillFantom's repository](https://github.com/WillFantom/Ryu-Docker), which uses `python:3.8-alpine` to build ryu image.

## Build

Clone this repository, and build a docker image in the repository directory:

```
docker build -f Dockerfile -t ryu-alpine:latest .
```

## Usage

Here are some use cases.

You can just start the container and shell (using the `6633` port):

```
docker run -it -p 6633:6633 --rm ryu-alpine:latest /bin/ash
```

Or, run the example app `simple_switch_13.py` of ryu:

```
docker run -it -p 6633:6633 --rm ryu-alpine:latest ryu-manager ./ryu/ryu/app/simple_switch_13.py
```

You can also mount the current working directory, for example, mount the current host directory to the ` /root/data ` and start the shell:

```
docker run -it -p 6633:6633 -v $(pwd):/root/data --rm ryu-alpine:latest /bin/ash
```

Or, just run your app `your_app.py` in the working directory:

```
docker run -it -p 6633:6633 -v $(pwd):/root/data --rm ryu-alpine:latest ryu-manager ./data/your_app.py
```

