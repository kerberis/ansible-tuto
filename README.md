Tutoriel Ansible
================

Ce tutoriel présente ansible étape par étape. Vous avez besoin au minimum d'une machine (physique ou virtuelle) comme noeud ansible. Un environnement [vagrant](https://www.vagrantup.com/about.html) est fourni dans ce tutoriel.

Ansible est un logiciel de gestion de configuration qui vous permet de cotrôler et de configurer des noeuds à partir d'une seule machine. A la différence des autres logiciel de gestion comme chef, puppet, etc. qui ont besoin d'une infrastructure PKI spécifique, ansible utilise une infrastructure SSH commune à tout environnement Linux/BSD.

Ansible est orienté "push". La configuration est poussée par une machine maître (celle qui peut accéder aux noeuds) Les alternatives disposent d'un mode "pull" où les noeuds prennent leur configuration d'une machine maître.

Ce mode est intéressant car il nécessite pas de disposer d'une machine maître connue et publique. Ce sont les noeuds qui doivent être accessibles. Nous verrons plus loin que les noeuds cachés peuvent aussi tirer leur configuration.

# Prerequisites for Ansible

You need the following python modules on your machine (the machine you run ansible 
on) 
- python-yaml
- python-jinja2

On Debian/Ubuntu run:
``sudo apt-get install python-yaml python-jinja2 python-paramiko python-crypto``

We're also assuming you have a keypair in your ~/.ssh directory.

# Installing Ansible

## From source

Ansible devel branch is always usable, so we'll run straight from a git checkout.
You might need to install git for this (`sudo apt-get install git` on Debian/Ubuntu).

    git clone git://github.com/ansible/ansible.git
    cd ./ansible

At this point, we can load the ansible environment:

    source ./hacking/env-setup

## From a deb package

When running from an installed package, this is absolutely not necessary. If
you prefer running from a debian package ansible, provides a `make target` to
build it. You need a few packages to build the deb:

    sudo apt-get install make fakeroot cdbs python-support
    git clone git://github.com/ansible/ansible.git
    cd ./ansible
    make deb
    sudo dpkg -i ../ansible_1.1_all.deb (version may vary)

We'll assume you're using the deb packages in the rest of this tutorial.

# Cloning the tutorial

    git clone https://github.com/leucos/ansible-tuto.git
    cd ansible-tuto

# Using Vagrant with the tutorial

It's highly recommended to use Vagrant to follow this tutorial. If you don't have 
it already, setting up should be quite easy and is described in [step-00/README.md](https://github.com/leucos/ansible-tuto/tree/master/step-00/README.md).

If you wish to proceed without Vagrant (not recommended!), go straight to
[step-01/README.md](https://github.com/leucos/ansible-tuto/tree/master/step-01).

## Contents

Just in case you want to skip to a specific step, here is a topic table of contents.

- [00. Vagrant Setup](https://github.com/leucos/ansible-tuto/tree/master/step-00)
- [01. Basic inventory](https://github.com/leucos/ansible-tuto/tree/master/step-01)
- [02. First modules and facts](https://github.com/leucos/ansible-tuto/tree/master/step-02)
- [03. Groups and variables](https://github.com/leucos/ansible-tuto/tree/master/step-03)
- [04. Playbooks](https://github.com/leucos/ansible-tuto/tree/master/step-04)
- [05. Playbooks, pushing files on nodes](https://github.com/leucos/ansible-tuto/tree/master/step-05)
- [06. Playbooks and failures](https://github.com/leucos/ansible-tuto/tree/master/step-06)
- [07. Playbook conditionals](https://github.com/leucos/ansible-tuto/tree/master/step-07)
- [08. Git module](https://github.com/leucos/ansible-tuto/tree/master/step-08)
- [09. Extending to several hosts](https://github.com/leucos/ansible-tuto/tree/master/step-09)
- [10. Templates](https://github.com/leucos/ansible-tuto/tree/master/step-10)
- [11. Variables again](https://github.com/leucos/ansible-tuto/tree/master/step-11)
- [12. Migrating to roles](https://github.com/leucos/ansible-tuto/tree/master/step-12)
- [13. Using tags (TBD)](https://github.com/leucos/ansible-tuto/tree/master/step-13)
- [14. Roles dependencies (TBD)](https://github.com/leucos/ansible-tuto/tree/master/step-14)
- [15. Debugging (TBD)](https://github.com/leucos/ansible-tuto/tree/master/step-15)
- [99. The end](https://github.com/leucos/ansible-tuto/tree/master/step-99)

## Contributing

Thanks to all people who have contributed to this tutorial:

* Aladin Jaermann
* Alexis Gallagher
* Atilla Mas
* Benny Wong
* Chris Schmitz
* dalton
* Daniel Howard
* David Golden
* Eugene Kalinin
* Hartmut Goebel
* Justin Garrison
* Karlo
* Marchenko Alexandr
* mxxcon
* Patrick Pelletier
* Pierre-Gilles Levallois
* Ruud Kamphuis
* Victor Boivie

I've been using Ansible almost since it's birth, but I learned a lot in
the process of writing it. If you want to jump in, it's a great way to
learn, feel free to add your contributions.

The chapters being written live in the
[writing](https://github.com/leucos/ansible-tuto/tree/writing) branch.

If you have ideas on topics that would require a chapter, please open a
PR.

I'm also open on pairing for writing chapters. Drop me a note if you're
interested.

If you make changes or add chapters, please fill the `test/expectations`
file and run the tests (`test/run.sh`).
See the `test/run.sh` file for (a bit) more information.

When adding a new chapter (e.g. `step-NN`), please issue:

    cd step-99
    ln -sf ../step-NN/{hosts,roles,site.yml,group_vars,host_vars} .

For typos, grammar, etc... please send a PR for the master branch
directly.

Thank you!

