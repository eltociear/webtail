# webtail

[![Go Reference][ref1]][ref2]
 [![GitHub Release][gr1]][gr2]
 [![Build Status][bs1]][bs2]
 [![FOSSA Status][fs1]][fs2]
 [![GitHub license][gl1]][gl2]

[![codecov][cc1]][cc2]
 [![Test Coverage][cct1]][cct2]
 [![Maintainability][ccm1]][ccm2]
 [![GoCard][gc1]][gc2]

[cct1]: https://api.codeclimate.com/v1/badges/909eca87d9ee5b216a6b/test_coverage
[cct2]: https://codeclimate.com/github/LeKovr/webtail/test_coverage
[ccm1]: https://api.codeclimate.com/v1/badges/909eca87d9ee5b216a6b/maintainability
[ccm2]: https://codeclimate.com/github/LeKovr/webtail/maintainability
[fs1]: https://app.fossa.com/api/projects/git%2Bgithub.com%2FLeKovr%2Fwebtail.svg?type=shield
[fs2]: https://app.fossa.com/projects/git%2Bgithub.com%2FLeKovr%2Fwebtail?ref=badge_shield
[ref1]: https://pkg.go.dev/badge/github.com/LeKovr/webtail.svg
[ref2]: https://pkg.go.dev/github.com/LeKovr/webtail
[cc1]: https://codecov.io/gh/LeKovr/webtail/branch/master/graph/badge.svg
[cc2]: https://codecov.io/gh/LeKovr/webtail
[gc1]: https://goreportcard.com/badge/github.com/LeKovr/webtail
[gc2]: https://goreportcard.com/report/github.com/LeKovr/webtail
[bs1]: https://cloud.drone.io/api/badges/LeKovr/webtail/status.svg
[bs2]: https://cloud.drone.io/LeKovr/webtail
[gr1]: https://img.shields.io/github/release/LeKovr/webtail.svg
[gr2]: https://github.com/LeKovr/webtail/releases
[gl1]: https://img.shields.io/github/license/LeKovr/webtail.svg
[gl2]: https://github.com/LeKovr/webtail/blob/master/LICENSE

[webtail](https://github.com/LeKovr/webtail) - Tail [log]files via websocket

This service loads list of logfiles from directory tree & continuously shows result of chosen file tail via websocket.

Project status: MVP

![Ping stream sample](webtail-ping.png)

[![FOSSA Status](https://app.fossa.com/api/projects/git%2Bgithub.com%2FLeKovr%2Fwebtail.svg?type=large)](https://app.fossa.com/projects/git%2Bgithub.com%2FLeKovr%2Fwebtail?ref=badge_large)

## Install

```sh
go get github.com/LeKovr/webtail
```

### Download binary

See [Latest release](https://github.com/LeKovr/webtail/releases/latest)

### Docker

v0.43.1 is the [last version available at dockerhub](https://hub.docker.com/repository/docker/lekovr/webtail/tags).

Starting from 0.43.2 docker images are published at ghcr.io, so use

```sh
docker pull ghcr.io/lekovr/webtail:latest
```

See [docker-compose.yml](docker-compose.yml) for usage example.

## Embed package in your service

```go
package main
import (
    "github.com/LeKovr/webtail"
)

func main() {
    wt, err := webtail.New(log, cfg.WebTail)
    if err != nil {
        return
    }
    go wt.Run()
    defer wt.Close()
    // ...
    http.Handle("/tail", wt)
}
```
See also: [app.go](https://github.com/LeKovr/webtail/blob/master/cmd/webtail/app.go)

## Note about gorilla/websocket

Starting from v0.30 this code is based on [gorilla/websocket chat example](https://github.com/gorilla/websocket/tree/master/examples/chat). See {client,hub}.go

## TODO

* [x] js: add mask for row coloring
* [ ] add tests & more docs
* [ ] add text field for server-side log filtering

## License

The MIT License (MIT), see [LICENSE](LICENSE).

Copyright (c) 2016-2021 Aleksey Kovrizhkin <lekovr+webtail@gmail.com>
