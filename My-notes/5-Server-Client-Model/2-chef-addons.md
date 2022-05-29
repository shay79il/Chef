# OHAI

```bash
# Get all info on the node
ohai

# Get ipaddress
ohai ipaddress

# Get os
ohai os

# Get kernel
ohai kernel

# Get kernel/release
ohai kernel/release
```

# Kitchen Testing

```bash

# create VM with chef tools and cookbooks
kitchen create

#
kitchen converge

#
kitchen verify

#
kitchen login

#
kitchen exec

#
kitchen test

#
kitchen setup

#
kitchen destroy

```

# Roles

## Combinations of RunLists to configure different utilities

- Web Server
- Database Server
- Tools

```bash
chef-client -local-mode --runlist "role[web-server]"

```

# Environments

## We may have _Dev_ env and a _Production_ env

### For example

- Dev env has its DB URL in `db.dev.local`
- Prod env has its DB URL in `db.prod.local`

# [Supermarket](https://supermarket.chef.io/cookbooks)

## Look for cookbooks at cookbooks, tools, plugins etc.
