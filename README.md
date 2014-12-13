Hostsharing-Ansible-Plone
=========================

To use these modules we have to create a file named ".hsadmin.properties" in the home directory of the package admins. In it we have to insert the packagename and password of the package admin. 

Example:

    xyz00@h99:~$ cat .hsadmin.properties 
    xyz00.passWord=insertpkgadminpasswordhere

This file should be protected, else it would be world readable:

    xyz00@h99:~$ chmod 600 .hsadmin.properties

We clone this git-repo to our machine:

    $ git clone https://github.com/Dominic-Schlegel/Hostsharing-Ansible-Plone.git

Then we change the working directory:

    $ cd Hostsharing-Ansible-Plone

All needed parameters can be set in the inventory file now. Change xyz00 to the name of your package admin. Set the name of a new user and a password. This username and password will be used in the Plone buildout process too. Please change them both (NewUser-password in HSAdmin and Plone-password) after the installation. We can edit the inventory file with:

    $ vim inventory
    
The Option -i can be used to read this inventory file instead of the /etc/ansible/hosts file. If we want to login with an SSH-Key instead of an SSH-Password, we have to remove the -k option from the following string. The -K is needed to prompt us once for the sudo password of the new user.

For a simple buildout:

    $ ansible-playbook -i inventory playbook-plone-minimal.yml -k -K
    
Or for a custom buildout (thanks to Veit Schiele):

    $ ansible-playbook -i inventory playbook-plone-custom.yml -k -K

Now we can reach our site via:

    https://www.plone.xyz00.hostsharing.net

Change the default passwords!

Many thanks for help to Michael Hierweck, Peter Hormanns & Veit Schiele.

--- Open Source Hosting ---
 https://www.hostsharing.net
