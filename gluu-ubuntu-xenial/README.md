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

Don’t use 127.0.0.1 or localhost for the IP and hostname. You want to be
able to reach the Gluu Server from your laptop’s browser. Even if you don’t have
DNS set up for this hostname, you can edit your localhost’s file to make sure the
name resolves (hostname mapping in `etc/hosts` (Linux) or `C:\Windows\System32\drivers\etc\hosts` (Windows) )

Once you’re confident your browser can resolve the hostname, navigate to
https://<hostname> (the hostname you used during setup). Your browser will warn
you about the insecure HTTPS connection because the Gluu Server initially generates
self-signed SSL certificates. It’s okay—you would upgrade these on your production
server, but for your test server, such self-signed SSL certificates are fine. You should be
presented with a login form. The default username is admin. Use the password that either
you specified or was auto-generated for you during installation.

## Configure SAML
[Gluu Documentation](https://gluu.org/docs/ce/admin-guide/saml/)
