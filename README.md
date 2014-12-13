HostSharing-Ansible-Plone
=========================

To use these modules you have to create a file named ".hsadmin.properties" in the home directory of the package admins. In it you have to define the packagename and password of the package admin.

    xyz00@h99:~$ cat .hsadmin.properties 
    xyz00.passWord=insertpkgadminpasswordhere

This file should be protected, else it would be world readable.

    xyz00@h99:~$ chmod 600 .hsadmin.properties

We clone this git-repo to our machine.

    $ git clone https://github.com/Dominic-Schlegel/HostSharing-Ansible-Plone.git

Now we change the working directory:

    $ cd HostSharing-Ansible-Plone

You can use -i to read the inventory file instead of the /etc/ansible/hosts file and you can set all needed parameters in this inventory file. Change xyz00 to the name of your package admin. Set the name of a new user and a password. This username and password will be used in the Plone buildout process too. Please change them both (NewUser-Password and Plone-Password) after the installation. If you want to login with an SSH-Key instead of an SSH-Password, you have to remove the -k parameter from the following string. The -K is needed to prompt you once for the sudo password of the new user.

For a simple buildout use:

    $ ansible-playbook -i inventory playbook-plone-minimal.yml -k -K
    
Or for a custom buildout, thanks to Veit Schiele, use:

    $ ansible-playbook -i inventory playbook-plone-custom.yml -k -K

You can reach your site now via:

    https://plone.xyz00.hostsharing.net

Change the default passwords!

Many thanks for help & code to Michael Hierweck, Peter Hormanns & Veit Schiele.

--- Open Source Hosting ---
 https://www.hostsharing.net
