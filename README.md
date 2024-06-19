![project is maintained](https://img.shields.io/maintenance/yes/2024.svg)

# ddev-sitediff <!-- omit in toc -->

* [What is ddev-sitediff?](#what-is-ddev-sitediff)
* [Getting started](#getting-started)
* [Usage](#usage)

## What is ddev-sitediff?

This repository allow developer to quickly add and configure [Sitediff](https://github.com/evolvingweb/sitediff) into a 
Ddev project 


## Getting started

In a Ddev setup, add `ddev-sitediff` by running 

`ddev get https://github.com/robert-ngo/ddev-sitediff/tarball/main`

This would add 3 files into local Ddev setup:

* `docker-compose.sitediff.yaml`: Docker compose setup for sitediff 
* `commands/sitediff/sitediff-build`: to run once, building the sitediff executable inside the container
* `commands/sitediff/sitediff`: custom Ddev command, binding `sitediff` executable to `ddev sitediff`

## Usage

### Without a recipe 

``` 
ddev sitediff init https://example.com 
ddev sitediff crawl     # crawl and cache example.com
ddev sitediff diff      # diff the previously cached version with the actual version
```

### Using existing `sitediff.yaml` config 

Given a `./prod-stage/sitediff/sitediff.yaml` and a `./selected-paths.txt` both exist.

```
ddev sitediff diff -C prod-stage/sitediff/ --paths-file ./selected-paths.txt -e
```

We include the flag `-e` to this command to export report into a `report.tgz`. This is currently a temporary solution 
while waiting for `ddev sitediff serve` to be configured. 

