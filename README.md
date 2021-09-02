# Ansible Role: Razor Tasks

An Ansible Role that configures CentOS Tasks and Repos in Puppet Razor on Linux.

## Razor Summary

Puppet Razor Server is an Open Source Operating System provisioning tool, details are here:

[https://github.com/puppetlabs/razor-server/wiki]

## Razor Post Task Configuration Use

This role will only create custom CentOS Tasks and Repos in Razor. As kickstart files are tailored to the environment you are deploying to the intention is this Role will be cloned and the kickstart files can be altered as per your environment. Hopefully they help.

I've created the following personal Ansible Role for creating Razor Policies and Tags which inject the metadata variables into the kickstarts e.g. ```<%= node.metadata['mgmt_nic'] %>```:

* nicholasrodriguez.razor_manage_hosts (IN DEV)

These can be copied and used as template for your own environments.

# Requirements

This Role was built and tested after the following Role was deployed but could be used for other Razor deployments not managed by the Role below:

* nicholasrodriguez.razor

# Role Variables

Available variables are listed below, along with default values (see defaults/main.yml):

CentOS version/s to install. A list of dicts specifying the following, examples are below and at least one entry is required.
```
centos_versions:
  - major: "MAJOR RELEASE NUMBER"
    build: "CentOS-<VERSION>-<TYPE>"
    url: "http://address/path/CentOS-7-x86_64-<TYPE>.iso"
```

Example
```
- major: "8.3"
  build: "CentOS-8.3-dvd"
  url: "http://uk.mirrors.clouvider.net/CentOS/8.3.2011/isos/x86_64/CentOS-8.3.2011-x86_64-dvd1.iso"
```

# Example Playbook
```
- hosts: servers
  roles:
     - role: nicholasrodriguez.razor-tasks-centos
```

License
-------

MIT

Author Information
------------------

- https://github.com/nicholasrodriguez/ (maintainer)
