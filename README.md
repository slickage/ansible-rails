# Ansible Rails

*Adapted from https://github.com/radar/ansible-rails-app*

#### Installed Software

- Ruby 2.1
- PostgreSQL
- nginx
- Puma (jungle)

#### Configuration

1. Change the app name and deploy directory in `vars/defaults.yml`
2. Rename `hosts.example` to `hosts` and change it to your hosts. For Homebrew's
   ansible, this defaults to `/usr/local/etc/ansible/hosts`

#### Running

If you're using vagrant to create the box, please use the insecure SSH key `--private-key= ~/.vagrant.d/insecure_private_key` in the `ansible-playbook` command.

    $ ansible-playbook -i hosts rails-app.yml -t deploy,postgresql,nginx
    $ <deploy your app>
    $ ansible-playbook -i hosts rails-app.yml -t puma

There is an example Capistrano `deploy.rb` in this repository that you can use too.

# Using vagrant to spin up a local dev box
#### requirements
1. install [Vagrant][vagrant]
2. install [VirtualBox][vbox]
3. install [VirtualBox guest additions plugin][vbguest]
4. install [VirtualBox hosts updater plugin][hosts]

#### Running
Navigate to the root ansible-rails directory and run the following command:

	$ vagrant up
This will do:
1. download the virtualbox file (ubuntu)
2. spin it up
3. run the playbook rails-app-local.yml
4. update hosts file so your server can be accessed at 

[vbox]:    https://www.virtualbox.org/wiki/Downloads
[vagrant]: http://downloads.vagrantup.com/
[vbguest]: https://github.com/dotless-de/vagrant-vbguest
[hosts]:   https://github.com/cogitatio/vagrant-hostsupdater
