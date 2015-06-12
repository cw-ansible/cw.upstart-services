<!--

---
lang: american
---
-->

[![Build Status](https://travis-ci.org/cw-ansible/cw.upstart-services.svg?branch=master)](https://travis-ci.org/cw-ansible/cw.upstart-services)
[![Tweet this](http://img.shields.io/badge/Tweet-it00aced.svg)](https://twitter.com/intent/tweet?tw_p=tweetbutton&via=renard_0&url=https%3A%2F%2Fgithub.com%2Fcw-ansible%2Fcw.upstart-services&text=Add%20wrapper%20to%20disable%20%23upstart%20services%20with%20%23ansible.)
[![Follow me on twitter](http://img.shields.io/badge/Twitter-Follow-00aced.svg)](https://twitter.com/intent/follow?region=follow_link&screen_name=renard_0&tw_p=followbutton)


# Upstart services

Add a wrapper to upstart command to not run disabled upstart services.

## Usage

Include the `cw.upstart-services` module to your playbook.

## Description

Replace `/sbin/initctl`, `/usr/sbin/invoke-rc.d`, and `/usr/sbin/service`
with a custom wrapper that do not start services start if it has been
disabled or if invokation is done withing a chrooted environment.

A service is disabled if there is a `manual` in it's configuration override
file (ie. `/etc/init/foo.override`).

If you really need to start a service that has been disable you still can
run:

- `service.distrib FOO start`
- `initctl.distrib start FOO`

## Warning

Please note that this module is not meant to be use without purposes, you
should have some good reasons to use it. For example you can use it if you
are building golden images on an hypervisor and you need to disable some
services, you can use that module.

This module does not work for old System V startup services since they are
standalone scripts. If you need to disable a System V service you probably
need to add an `exit` command in its default file (`/etc/default/FOO`).

## Configuration

See specific documentation in `defaults/main.yml`.

## Copyright

Author: Sébastien Gross `<seb•ɑƬ•chezwam•ɖɵʈ•org>` [@renard_0](https://twitter.com/renard_0)

License: WTFPL, grab your copy here: http://www.wtfpl.net
