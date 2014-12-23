# Ansible playbook - Simple FTP server

The Ansible playbook for this Vagrantfile sets up [vsftpd](https://security.appspot.com/vsftpd.html) to have a simple FTP server. This will simply set up a basic FTP server accessible on a private network. SFTP is *not* set up. Once the server is provisioned, you should be able to connect to the FTP server on 192.168.3.2 on your local environment.

### Vagrantfile

* Box used: [Ubuntu 14.04 64-bit (Trusty)](https://vagrantcloud.com/ubuntu/boxes/trusty64)
* [Virtualbox settings:](https://www.virtualbox.org/manual/ch08.html#vboxmanage-modifyvm)
 * --memory 1024
 * --natdnshostresolver1 on
* [Private network](https://docs.vagrantup.com/v2/networking/private_network.html) on **192.168.3.2**.
* [Forwarded ports](https://docs.vagrantup.com/v2/networking/forwarded_ports.html):
 * 20 (vsftpd data port for active connections)
 * 21 (vsftpd command port)

### Playbook tasks

* Installs vsftpd package from Apt.
* Creates a user for FTP login (see 'Variables' section for the default user login information).
* Sets up the vsftpd configuration file (see 'Variables' section for some configuration options).
* Restarts vsftpd.

## Variables

These variables are located in `provisioning/vars/main.yml`.

* ftp_username (Default: **ftpuser**): The username for the user account that is created on the provisioned server. It will also be the username for logging in to the FTP server.
* ftp_password (Default: **ftpuser**): The password for the user account that is created on the provisioned server. It will also be the password for logging in to the FTP server.
 * **Note:** This is a crypted password. If you want to change this value, please read ["How do I generate crypted password for the user module?"](http://docs.ansible.com/faq.html#how-do-i-generate-crypted-passwords-for-the-user-module) in the Ansible documentation to learn how to set up a new password.
* ftp_home_fir (Default: **/home/ftpuser**): The home directory for the user account that is created on the provisioned server. This will be the root directory when logging in to the FTP server.
* anonymous_enable (Default: **NO**): By default, do not allow anonymous users to log in to the FTP server. Allowed values are **YES** or **NO**.
* chroot_local_user (Default: **YES**): By default, makes the logged-in users home directory the root directory. Allowed values are **YES** or **NO**.
allow_writeable_chroot (Default: **YES**): By default, allow the logged-in users be able to write to the chroot directory. Allowed values are **YES** or **NO**.
