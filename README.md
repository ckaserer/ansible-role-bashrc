[![](https://img.shields.io/travis/com/ckaserer/ansible-role-bashrc/master?style=flat-square)](https://travis-ci.com/ckaserer/ansible-role-bashrc)
![gplv3](https://img.shields.io/badge/license-GPL%20v3.0-brightgreen.svg?style=flat-square)
![Maintenance](https://img.shields.io/maintenance/yes/2021?style=flat-square)

# ckaserer.bashrc

If you work most of the time on the CLI, like I do, you might want to add a bit of color to your life. With this customized bashrc you get a bash prompt streched over 2 line so you can easily see the user, host, path and git branch if you are in a git repository at a glance. In addition `ls` and `grep` are colorized if your system supports it.

<p align="center">
<img alt="git" src="https://github.com/ckaserer/bashrc/raw/master/.images/git.png">
</p>

<br>

<p align="center">
<img alt="nogit" src="https://github.com/ckaserer/bashrc/raw/master/.images/no-git.png">
</p>


## Let's bring color and git support to your bash!

There are two variants you can use the bashrc role. Either enable the bashrc only for the user ansible utilizes to connect to the target nodes or add the bashrc as systemwide default.

Either way we need to install the latest version of the bashrc ansible role from ansible galaxy via

```
ansible-galaxy install ckaserer.bashrc
```

---

## User

The playbook below downloads the latest bashrc version and enable it for your current user on your current node. 

Alternativly you can set `hosts` to a group of ansible nodes or `all`. This will enable the bashrc for the user utilzed by ansible to connect to the target nodes.

```
- hosts: localhost
  tasks:
    - name: "Include ckaserer.bashrc"
      include_role:
        name: "ckaserer.bashrc"
```

---

## Systemwide Default

The playbook below downloads the latest bashrc version on all nodes and enable it for all users. 

Alternativly you can set `hosts` to a group of ansible nodes or `localhost`.

Executing the systemwide variant requires root privileges hence the additional `become: true` in the `include_role` task.

```
- hosts: all
  tasks:
    - name: "Include ckaserer.bashrc"
      include_role:
        name: "ckaserer.bashrc"
        apply:
          become: true
        vars:
          systemwide: true
```    
