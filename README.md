# appdeps
Simple commandline tool to check and/or wait for application dependencies.

In particular, it will check and/or wait for files or ports.

appdeps is primarily intended for [Docker](https://www.docker.com/) containers.

## Installation
```
pip install appdeps
```

## Usage
```
usage: appdeps.py [-h] [--wait-secs WAIT_SECS] [--interval-secs INTERVAL_SECS]
                  [--port PORT] [--port-wait PORT_WAIT] [--file FILE]
                  [--file-wait FILE_WAIT]

Check and/or wait for application dependencies.

optional arguments:
  -h, --help            show this help message and exit
  --wait-secs WAIT_SECS
                        Number of seconds to wait.
  --interval-secs INTERVAL_SECS
                        Number of seconds to wait in between checks.
  --port PORT           Check that port is open. Format is host:port.
  --port-wait PORT_WAIT
                        Wait for port to open. Format is host:port.
  --file FILE           Check that file exists.
  --file-wait FILE_WAIT
                        Wait for file to exist.
```

## Example
Here's an example using appdeps in a dockerfile:
```
CMD python /usr/local/vivo-install/appdeps.py --wait-secs 60 --file-wait /usr/local/vivo/home/runtime.properties --port-wait db:3306 \
    && ./catalina.sh run
```
