[![Actions Status - Master](https://github.com/juju4/ansible-kunai/workflows/AnsibleCI/badge.svg)](https://github.com/juju4/ansible-kunai/actions?query=branch%3Amain)
[![Actions Status - Devel](https://github.com/juju4/ansible-kunai/workflows/AnsibleCI/badge.svg?branch=devel)](https://github.com/juju4/ansible-kunai/actions?query=branch%3Adevel)

# Kunai ansible role

Ansible role to setup [Kunai, Threat-hunting tool for Linux](https://github.com/kunai-project/kunai)

See also
* https://why.kunai.rocks/

## Requirements & Dependencies

### Ansible
It was tested on the following versions:
 * 2.10-17

### Operating systems

Tested on Ubuntu 24.04, 22.04, 20.04, Centos/Rockylinux 9.

## Example Playbook

Just include this role in your list.
For example

```
- host: myhost
  roles:
    - juju4.kunai
```

you probably want to review variables

## Variables

TBD


## Continuous integration

```
$ pip install molecule docker
$ molecule test
$ MOLECULE_DISTRO=ubuntu:24.04 molecule test --destroy=never
```


## Troubleshooting & Known issues

* "Error: failed to set RLIMIT_MEMLOCK: Operation not permitted (os error 1)"
  * https://why.kunai.rocks/docs/compatibility#rlimit_memlock
  * If container, may need `lxc config set MyContainer limits.kernel.memlock unlimited` ([lxc](https://discuss.linuxcontainers.org/t/error-setting-rlimits-type-8-operation-not-permitted-unknown-in-lxd-container/9976/3)), "lxc.prlimit.memlock: (KB)" ([proxmox /etc/pve/lxc/<ID>.conf)](https://forum.proxmox.com/threads/how-to-increase-max-locked-memory-ulimit-l-on-a-lxc-container.69079/)) or run as privileged. = not enough for proxmox
  * If not, review [memlock settings in /etc/security/limits.conf](https://github.com/RPCS3/rpcs3/issues/9328).

## License

BSD 2-clause
