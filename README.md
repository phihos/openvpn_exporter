# openvpn_exporter

[![Release](https://img.shields.io/github/v/release/patrickjahns/openvpn_exporter?sort=semver)](https://github.com/patrickjahns/openvpn_exporter/releases)
[![LICENSE](https://img.shields.io/github/license/patrickjahns/openvpn_exporter)](https://github.com/patrickjahns/openvpn_exporter/blob/master/LICENSE)
[![Test and Build](https://github.com/patrickjahns/openvpn_exporter/workflows/Test%20and%20Build/badge.svg)](https://github.com/patrickjahns/openvpn_exporter/actions?query=workflow%3A%22Test+and+Build%22)
[![Go Doc](https://img.shields.io/badge/go.dev-reference-007d9c?logo=go&logoColor=white)](https://pkg.go.dev/github.com/patrickjahns/openvpn_exporter)
[![Go Report Card](https://goreportcard.com/badge/github.com/patrickjahns/openvpn_exporter)](https://goreportcard.com/report/github.com/patrickjahns/openvpn_exporter)

Prometheus exporter for openvpn. Exposes the metrics from [openvpn status file](https://openvpn.net/community-resources/reference-manual-for-openvpn-2-4/) - currently supports format version 1


## Installation

For pre built binaries, please take a look at the [github releases](https://github.com/patrickjahns/openvpn_exporter/releases)

## Usage

### Example metrics

```
# HELP openvpn_build_info A metric with a constant '1' value labeled by version information
# TYPE openvpn_build_info gauge
openvpn_build_info{date="20200425",go="go1.14.2",revision="90ee059",version="90ee059"} 1
# HELP openvpn_bytes_received Amount of data received via the connection
# TYPE openvpn_bytes_received gauge
openvpn_bytes_received{common_name="user1",server="local"} 7.883858e+06
openvpn_bytes_received{common_name="user2",server="local"} 1.6732e+06
openvpn_bytes_received{common_name="user3@test.de",server="local"} 1.9602844e+07
openvpn_bytes_received{common_name="user4",server="local"} 582207
# HELP openvpn_bytes_sent Amount of data sent via the connection
# TYPE openvpn_bytes_sent gauge
openvpn_bytes_sent{common_name="user1",server="local"} 7.76234e+06
openvpn_bytes_sent{common_name="user2",server="local"} 2.065632e+06
openvpn_bytes_sent{common_name="user3@test.de",server="local"} 2.3599532e+07
openvpn_bytes_sent{common_name="user4",server="local"} 575193
# HELP openvpn_connected_since Unixtimestamp when the connection was established
# TYPE openvpn_connected_since gauge
openvpn_connected_since{common_name="user1",server="local"} 1.587551802e+09
openvpn_connected_since{common_name="user2",server="local"} 1.587551812e+09
openvpn_connected_since{common_name="user3@test.de",server="local"} 1.587552165e+09
openvpn_connected_since{common_name="user4",server="local"} 1.587551814e+09
# HELP openvpn_connections Amount of currently connected clients
# TYPE openvpn_connections gauge
openvpn_connections{server="local"} 4
# HELP openvpn_last_updated Unix timestamp when the last time the status was updated
# TYPE openvpn_last_updated gauge
openvpn_last_updated{server="local"} 1.587665671e+09
# HELP openvpn_max_bcast_mcast_queue_len MaxBcastMcastQueueLen of the server
# TYPE openvpn_max_bcast_mcast_queue_len gauge
openvpn_max_bcast_mcast_queue_len{server="local"} 5
# HELP openvpn_start_time Unix timestamp of the start time
# TYPE openvpn_start_time gauge
openvpn_start_time 1.587931295e+09
```

## Development

This project requires Go >= v1.14. To get started, clone the repository and run `make generate`

```shell script
git clone https://github.com/patrickjahns/openvpn_exporter.git
cd openvpn_exporter

make generate
make build

./cmd/openvpn_exporter -h
```

### Building the project

```shell script
make build
```

### Running tests

```shell script
make test
```





