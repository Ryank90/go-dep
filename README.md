# Go Dep

A docker image for the Go dependency tool

This image will allow you to install the dependencies required for your Golang application and *vendor* them. For more information on how vendoring works with Golang see their [wiki](https://github.com/golang/go/wiki/PackageManagementTools#go15vendorexperiment).

## Usage
Simply run a container with this image and map the path to your Golang app as a volume, and set the working directory.

You can then pass any dep command to the container, see the [dep repo](https://github.com/golang/dep) for more information.

### Examples

Initialise the vendor folder:
```bash
$ docker run -it --rm -v path/to/app:/go/src/path/to/app -w /go/src/path/to/app ryank90/go-dep init
```

Report status of dependencies:
```bash
$ docker run -it --rm -v path/to/app:/go/src/path/to/app -w /go/src/path/to/app ryank90/go-dep status
```

Install project dependencies;
```bash
$ docker run -it --rm -v path/to/app:/go/src/path/to/app -w /go/src/path/to/app ryank90/go-dep ensure
```

## Why not use the GOPATH?
Sure you can use your GOPATH to manage dependencies on your local machine and most of the time it will work fine. But there are cases where this may not work, for example if your Golang application is part of a [monolithic repo](https://danluu.com/monorepo/) (outside of the GOPATH) with apps in other languages.

Basically put this image allows you to install your Golang depencies without the need to `go get`, without the need to install `dep` and to be honest without the need to have Golang on your host machine!
