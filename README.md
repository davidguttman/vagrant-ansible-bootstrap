# Vagrant Ansible Bootstrap #

When Vagrant boots up an image for you, it expects you to use 'vagrant ssh' to get access. This causes problems when we'd like to treat a local Vagrant image like a remote server for Ansible testing.

This Vagrantfile + small playbook/role will make it so that your Vagrant image will be provisioned with a deploy user that has your key (`~/.ssh/id_rsa.pub`) with sudo rights.

## Usage ##


Clone this repo to a new folder and run `vagrant up`:

    git clone git@github.com:davidguttman/vagrant-ansible-bootstrap.git your-server
    cd your-server
    vagrant up

Once the server is up, you can access it like a normal cloud instance:

    echo 192.168.33.10 > inventory
    ansible-playbook -i inventory -u deploy /path/to/playbook.yml
