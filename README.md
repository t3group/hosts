Hosts
=========

Ansible Role 简单管理主机hosts文件和主机名配置。

Role Variables
--------------

每一个记录都是有一个字典进行管理的，字段address，hostnames是一个list可以定义多个，
一般情况下我们都习惯定义长短域名，为了满足更加复杂定制化需要针对hosts可以直接指定
自己的hosts文件，替换字段: hosts_override_hosts_template 。

关于其他字段的相信如下:

hosts_ipv4_loopback_hosts: 本地回环地址和主机名，主要作用于hosts。

hosts_additional_hosts: 我们自定义的主机列表。

hosts_override_hosts_template: 自定义的Hosts文件。

Example Playbook
----------------

1. 使用私有hosts文件，并根据inventory配置hostname
```yaml
    - hosts: all
      roles:
         - role: hosts
           hosts_override_hosts_template: hosts
```

2. 通过定义playbook配置主机名
```yaml
    - hosts: all
      roles:
         - role: hosts
           hosts_additional_hosts:
               - address: 192.168.0.1
                 hostnames:
                     - server
                     - server.example.com
```
