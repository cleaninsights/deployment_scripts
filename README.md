## Clean insights deployment scripts

Takes a fresh 16.04 image (which you have SSH access to) and makes it into a piwik server.  Be sure to change up the creds when creating a real production instance.

Based on:
* https://github.com/ICTO/ansible-piwik
* https://github.com/thefinn93/ansible-letsencrypt

## Setting up a new Piwik server with TLS

* Create a box, make sure you have ssh access to it.  On digital ocean, this is easy-peasy (just add your public key upon creation).

* Create a DNS record for this box.  This is important.  Letsencrypt needs to verify who you are so they gotta be able to find you.

* Add the new machine's IP and hostname to the ansible.hosts file

* Run `ansible-playbook -i ansible.hosts python-init.yaml -u root -e "ansible_python_interpreter=/usr/bin/python3"
` to set up the correct interpreter.

* Run `ansible-playbook -i ansible.hosts piwik-playbook.yaml -u root`