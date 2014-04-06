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
   ansible, please use `/usr/local/etc/ansible/hosts`

#### Running

    $ ansible-playbook -i hosts rails-app.yml -t deploy,postgresql,nginx
    $ <deploy your app>
    $ ansible-playbook -i hosts rails-app.yml -t puma

There is an example Capistrano `deploy.rb` in this repository that you can use too.

