Apache role
-----------

This role requires Ansible 1.4.

This role installs and configures Apache web server. The avaliable paramaters
are listen ports and the list of virtualhosts that point to specific
directories.

*For now, this role only works in RedHat derivatives.*

Variables
---------

* apache_listen_ports: list of ports where Apache will listen
* apache_vhosts: list of dictionaries here virtual hosts are defined.

For more info see defaults/main.yml
