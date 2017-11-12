# debianweb

Add "127.0.0.1    test1.local" & "127.0.0.1    test2.local" to /etc/hosts on host.

Clone the repo and cd ./debianweb

```
bash-3.2$ sudo vagrant destroy
==> default: VM not created. Moving on...
bash-3.2$ sudo vagrant up
Bringing machine 'default' up with 'virtualbox' provider...
==> default: Importing base box 'debian/stretch64'...
==> default: Matching MAC address for NAT networking...
==> default: Setting the name of the VM: debianweb_default_1510489519287_62153
==> default: Clearing any previously set network interfaces...
==> default: Preparing network interfaces based on configuration...
    default: Adapter 1: nat
==> default: You are trying to forward to privileged ports (ports <= 1024). Most
==> default: operating systems restrict this to only privileged process (typically
==> default: processes running as an administrative user). This is a warning in case
==> default: the port forwarding doesn't work. If any problems occur, please try a
==> default: port higher than 1024.
==> default: Forwarding ports...
    default: 80 (guest) => 80 (host) (adapter 1)
    default: 22 (guest) => 2222 (host) (adapter 1)
==> default: Running 'pre-boot' VM customizations...
==> default: Booting VM...
==> default: Waiting for machine to boot. This may take a few minutes...
    default: SSH address: 127.0.0.1:2222
    default: SSH username: vagrant
    default: SSH auth method: private key
    default: 
    default: Vagrant insecure key detected. Vagrant will automatically replace
    default: this with a newly generated keypair for better security.
    default: 
    default: Inserting generated public key within guest...
    default: Removing insecure key from the guest if it's present...
    default: Key inserted! Disconnecting and reconnecting using new SSH key...
==> default: Machine booted and ready!
==> default: Checking for guest additions in VM...
    default: No guest additions were detected on the base box for this VM! Guest
    default: additions are required for forwarded ports, shared folders, host only
    default: networking, and more. If SSH fails on this machine, please install
    default: the guest additions and repackage the box to continue.
    default: 
    default: This is not an error message; everything may continue to work properly,
    default: in which case you may ignore this message.
==> default: Installing rsync to the VM...
==> default: Rsyncing folder: /Users/maliciousgenius/Projects/debianweb/ => /vagrant
==> default: Running provisioner: ansible...
Vagrant has automatically selected the compatibility mode '2.0'
according to the Ansible version installed (2.3.0.0).

Alternatively, the compatibility mode can be specified in your Vagrantfile:
https://www.vagrantup.com/docs/provisioning/ansible_common.html#compatibility_mode

    default: Running ansible-playbook...
[DEPRECATION WARNING]: Instead of sudo/sudo_user, use become/become_user and 
make sure become_method is 'sudo' (default).
This feature will be removed in a 
future release. Deprecation warnings can be disabled by setting 
deprecation_warnings=False in ansible.cfg.

PLAY [all] *********************************************************************

TASK [Gathering Facts] *********************************************************
ok: [default]

TASK [Preparation | Update system to latest] ***********************************
changed: [default]

TASK [Preparation | Network conf] **********************************************
changed: [default]

TASK [Preparation | Fix hosts] *************************************************
changed: [default] => (item={u'ip': u'192.168.13.1', u'name': u'test1.local', u'dbname': u'test1', u'dbpass': u'Pa$$word'})
changed: [default] => (item={u'ip': u'192.168.13.2', u'name': u'test2.local', u'dbname': u'test2', u'dbpass': u'Pa$$word'})

TASK [Preparation | Create users] **********************************************
changed: [default] => (item={u'ip': u'192.168.13.1', u'name': u'test1.local', u'dbname': u'test1', u'dbpass': u'Pa$$word'})
changed: [default] => (item={u'ip': u'192.168.13.2', u'name': u'test2.local', u'dbname': u'test2', u'dbpass': u'Pa$$word'})

TASK [Nginx | Adding signing key] **********************************************
changed: [default]

TASK [Nginx | Adding to sources.list repo url] *********************************
changed: [default]

TASK [Nginx | Install package] *************************************************
changed: [default]

TASK [Nginx | Stop services] ***************************************************
ok: [default]

TASK [LAMP | Adding dotdeb key] ************************************************
changed: [default]

TASK [LAMP | Adding to sources.list repo url] **********************************
changed: [default]

TASK [LAMP | Install packages] *************************************************
changed: [default] => (item=[u'apache2', u'libapache2-mod-php', u'php', u'php-mysql', u'php-xml', u'php-fpm', u'mysql-server', u'python-mysqldb'])

TASK [Joomla | Download distribution file] *************************************
changed: [default]

TASK [Joomla | Make dir for vhost] *********************************************
changed: [default] => (item=test1.local)
changed: [default] => (item=test2.local)

TASK [Joomla | Unpack joomla distribution file] ********************************
changed: [default] => (item=test1.local)
changed: [default] => (item=test2.local)

TASK [Joomla | Aceess to dir] **************************************************
changed: [default] => (item={u'ip': u'192.168.13.1', u'name': u'test1.local', u'dbname': u'test1', u'dbpass': u'Pa$$word'})
changed: [default] => (item={u'ip': u'192.168.13.2', u'name': u'test2.local', u'dbname': u'test2', u'dbpass': u'Pa$$word'})

TASK [Config | Clean default] **************************************************
changed: [default] => (item=/var/www/html)
changed: [default] => (item=/etc/apache2/sites-enabled/000-default.conf)
changed: [default] => (item=/etc/apache2/sites-available/000-default.conf)
changed: [default] => (item=/etc/apache2/sites-available/default-ssl.conf)
changed: [default] => (item=/etc/php/7.0/fpm/pool.d/www.conf)
changed: [default] => (item=/etc/nginx/conf.d/default.conf)

TASK [Config | Apache | Module install] ****************************************
changed: [default] => (item=proxy)
changed: [default] => (item=proxy_balancer)
changed: [default] => (item=proxy_http)
changed: [default] => (item=proxy_fcgi)
changed: [default] => (item=rewrite)

TASK [Config | Apache | Cange "memory limit"] **********************************
changed: [default]

TASK [Config | Apache | Add vhost] *********************************************
changed: [default] => (item={u'ip': u'192.168.13.1', u'name': u'test1.local', u'dbname': u'test1', u'dbpass': u'Pa$$word'})
changed: [default] => (item={u'ip': u'192.168.13.2', u'name': u'test2.local', u'dbname': u'test2', u'dbpass': u'Pa$$word'})

TASK [Config | Apache | Enable configuration] **********************************
changed: [default] => (item={u'ip': u'192.168.13.1', u'name': u'test1.local', u'dbname': u'test1', u'dbpass': u'Pa$$word'})
changed: [default] => (item={u'ip': u'192.168.13.2', u'name': u'test2.local', u'dbname': u'test2', u'dbpass': u'Pa$$word'})

TASK [Config | Apache | Change default port] ***********************************
changed: [default]

TASK [Config | Nginx | Add derictive to nginx.conf] ****************************
changed: [default]

TASK [Config | Nginx | runtime user] *******************************************
changed: [default]

TASK [Config | Nginx | vhost conf] *********************************************
changed: [default] => (item={u'ip': u'192.168.13.1', u'name': u'test1.local', u'dbname': u'test1', u'dbpass': u'Pa$$word'})
changed: [default] => (item={u'ip': u'192.168.13.2', u'name': u'test2.local', u'dbname': u'test2', u'dbpass': u'Pa$$word'})

TASK [Config | fpm] ************************************************************
changed: [default] => (item={u'ip': u'192.168.13.1', u'name': u'test1.local', u'dbname': u'test1', u'dbpass': u'Pa$$word'})
changed: [default] => (item={u'ip': u'192.168.13.2', u'name': u'test2.local', u'dbname': u'test2', u'dbpass': u'Pa$$word'})

TASK [Config | mysql | Create database] ****************************************
changed: [default] => (item={u'ip': u'192.168.13.1', u'name': u'test1.local', u'dbname': u'test1', u'dbpass': u'Pa$$word'})
changed: [default] => (item={u'ip': u'192.168.13.2', u'name': u'test2.local', u'dbname': u'test2', u'dbpass': u'Pa$$word'})

TASK [Config | mysql | Add user and access] ************************************
changed: [default] => (item={u'ip': u'192.168.13.1', u'name': u'test1.local', u'dbname': u'test1', u'dbpass': u'Pa$$word'})
changed: [default] => (item={u'ip': u'192.168.13.2', u'name': u'test2.local', u'dbname': u'test2', u'dbpass': u'Pa$$word'})

RUNNING HANDLER [apache2 reload] ***********************************************
changed: [default]

RUNNING HANDLER [fpm reload] ***************************************************
changed: [default]

RUNNING HANDLER [nginx reload] *************************************************
changed: [default]

PLAY RECAP *********************************************************************
default                    : ok=31   changed=29   unreachable=0    failed=0   


==> default: Machine 'default' has a post `vagrant up` message. This is a message
==> default: from the creator of the Vagrantfile, and not from Vagrant itself:
==> default: 
==> default: Vanilla Debian box. See https://app.vagrantup.com/debian for help and bug reports

```
