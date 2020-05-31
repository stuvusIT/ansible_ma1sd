# Ansible role for ma1sd (Federated Matrix Identity Server)

This role installs and configures [ma1sd](https://github.com/ma1uta/ma1sd) on an APT-based system.
This role does **not** install/configure a reverse proxy.
You have to install and configure a reverse proxy yourself (or using another role, i.e.
[this one](https://github.com/stuvusIT/nginx)) in order to use the features of ma1sd.
Check out the [ma1sd documentation](https://github.com/ma1uta/ma1sd/blob/master/docs/README.md) in
order to configure your reverse proxy correctly.

## Example Playbook

The following is an example playbook which installs and configures ma1sd.

```yml
- hosts: matrix01
  become: true
  roles:
    - role: ma1sd
  vars:
      ma1sd_deb_url: https://github.com/ma1uta/ma1sd/releases/download/2.3.0/ma1sd_2.3.0_all.deb
      ma1sd_checksum: sha256:3da8ed4777dc933fea332c596e228a66f39988885130ab6a5a70825c32fcca5e
      ma1sd_config:
        # Content of /etc/ma1sd/ma1sd.yaml goes here.
        #
        # ...
```

## Source specification

`ma1sd_deb_url` must contain the url where to download the ma1sd deb package (`.deb` file).
`ma1sd_checksum` must contain a checksum (for instance the SHA256 checksum) of that `.deb` file.

## ma1sd Configuration

You have to make yourself familiar with
[how to configure ma1sd](https://github.com/ma1uta/ma1sd/blob/master/docs/configure.md) in order
to set the role variable `ma1sd_config`.

## Role Variables

| Name              |            | Description                                    |
| :---------------- | :--------- | :--------------------------------------------- |
| `ma1sd_deb_url`   | *required* | [#source-specification](#source-specification) |
| `ma1sd_checksum`  | *required* | [#source-specification](#source-specification) |
| `riot_web_config` | *required* | [#ma1sd-configuration](#ma1sd-configuration)   |
