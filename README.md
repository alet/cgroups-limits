# User limits module

[![Build Status](https://travis-ci.org/alet/cgroups-limits.svg?branch=master)](https://travis-ci.org/alet/cgroups-limits)

This module turn on cpu and memory limits on specifed user. Module use cgroup facility of linux kernel, but developed for and tested on Ubuntu 14.04

## Installing

$ ansible-galaxy install alet.cgroups-limits

## Usage

This role takes the variable users_limit with dictionaries. Default value for cpu is 50% and for memory 128M. Values are percent for cpu and megabytes for memory. To remove user's limit add "del" parameter with value "True". Sample:
```yml
- name: Limits
  hosts: all
  vars:
    users_limit:
      - { name: vagrant, cpu: 80, mem: 128 }
      - { name: test, del: True }

  roles:
    - cgroups-limits
```

## Important!

There is NO control of summary cpu's percent is 100 and there is NO control of summary of memory are equal to physical.
