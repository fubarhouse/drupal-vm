<img style="float:left" alight="left" height="128px" width="100px" src="https://github.com/fubarhouse/ansible-role-golang/raw/master/gopher.png">

# Ansible Role: Go

[![Build Status](https://travis-ci.org/fubarhouse/ansible-role-golang.svg?branch=master)](https://travis-ci.org/fubarhouse/ansible-role-golang)
[![Ansible Galaxy](https://img.shields.io/badge/galaxy-fubarhouse--golang-5140.svg)](https://galaxy.ansible.com/fubarhouse/golang)
[![MIT licensed](https://img.shields.io/badge/license-MIT-blue.svg)](https://raw.githubusercontent.com/fubarhouse/ansible-role-golang/master/LICENSE)

* Installs the Google [Go](https://golang.org/) programming language
* Install configurations are entirely automatic
* Install configurations can be manually set
* Installs from configurable mirror
* Installs optional packages using `go get`

## Requirements

  None.

## Role Variables

Installation configuration
````
go_custom_mirror: https://storage.googleapis.com/golang
````

Basic configuration
````
go_version: 1.8.1
GOROOT: /home/vagrant/go
````

Optional configuration
````
GOOS: darwin
GOARCH: amd64
````

****Building from source****

Golang Bootstrap Workspace
````
GOROOT_BOOTSTRAP: /home/vagrant/go1.4
````
Boolean to indicate build should be from source.
````
build_go_from_source: false
````
Boolean to indicate Bootstrap needs installation.
````
install_go_bootstrap: false
````
Which script should be used when building from source
````
go_build_script: make.bash
````

To install `go get` binaries/projects, add them to `go_get`
````
go_get:
- name: gopm
  url: github.com/gpmgo/gopm
- name: golint
  url: github.com/golang/lint/golint
````

To ensure all packages are removed before running the play, you can use the go_reget variable:
````
go_reget: true
````

To add/change the shell profiles to configure, use the `shell_profiles` array.
````
shell_profiles:
- .bash_profile
````

To clean up an installation completely prior to role execution:
````
go_install_clean: true
````
### Setting permissions
**Note**: If you specify insufficient permissions the playbook will treat the following play as a new installation because it will not be able to determine what version is installed. 
To specify the permissions of the codebase, you can set:
````
mode_codebase: 0755
````
To specify the permissions of the workspace, you can set:
````
mode_workspace: 0755
````

## Dependencies

None.

## Example Playbook

````
- hosts: localhost
  roles:
    - fubarhouse.golang
````

## Installation

* Install using `ansible-galaxy install fubarhouse.golang`
* Add this role to your playbook.
* Modify above variables as desired.

## License

MIT / BSD

## Author Information

This role was created in 2016 by [Karl Hepworth](https://twitter.com/fubarhouse).

Image of Go's mascot was created by [Takuya Ueda](https://twitter.com/tenntenn). Licenced under the Creative Commons 3.0 Attributions license. This image has been resized for purpose, but is otherwise unchanged.