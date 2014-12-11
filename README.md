HostSharing-Ansible-Plone
=========================

To use these modules you have to create a file called ".hsadmin.properties" in the home directory of the package admins. In it you have to define the password of the package admin.

    xyz00@h99:~$ cat .hsadmin.properties 
    xyz00.passWord=geheimwort

This file should be protected, else it would be world readable.

    xyz00@h99:~$ chmod 600 .hsadmin.properties

We clone this git-repo to our machine.

    ~$ git clone https://github.com/Dominic-Schlegel/HostSharing-Ansible-Plone.git

Now we change to its folder:

    ~$ cd HostSharing-Ansible-Plone

We use -i to read the inventory file instead of the /etc/ansible/hosts file. You can set all needed parameters in this inventory file. Change xyz00 to the name of your package admin. Set the name of a new user and a password. This username and password will be used in the Plone buildout process too. Please change them both (NewUser-Password and Plone-Password) after the installation. If you want to login with an SSH-Key instead of an SSH-Password, you have to remove the -k parameter from the following string. The -K is needed to prompt you once for the sudo password of the new user.

    ~$ ansible-playbook -i inventory playbook-plone-minimal.yml -k -K

Have fun watching everything going automatically! And change the default passwords!!


--- Open Source Hosting ---
 https://www.hostsharing.net
