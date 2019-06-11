# Gluu server on Ubuntu Xenial
This configs create a Gluu server

The VM is created with 2 CPUs and 8GB of RAM by default as recommended in the Gluu documentation. [Gluu Installation](https://gluu.org/docs/ce/installation-guide/)

## Getting Started
#####1. Install Cygwin
#####2. Install Virtual box
#####3. Install Vagrant
#####4. Run prepare script
```
./prepare.sh
```
#####5. Edit Vagrantfile as needed
#####6. Create the Vagrant instance
This server setup uses Ansible as a provisioning tool. The ansible tasks will install the Gluu server
```
vagrant up
```

#####7. Setup Gluu server
```
# ssh to VM
vagrant ssh

# check the server is up
sudo service gluu-server-3.1.6 status

# login into chroot jail
sudo service gluu-server-3.1.6 login

cd /install/community-edition-setup
./setup.py
```

Follow the Gluu server instructions.

Create a hostname mapping in `etc/hosts` (Linux) or `C:\Windows\System32\drivers\etc\hosts` (Windows):

Next, login to the Gluu UI at https://gluu.local, and authenticate with the credentials you provided while setting up the server

## Configure SAML
[Gluu Documentation](https://gluu.org/docs/ce/admin-guide/saml/)
