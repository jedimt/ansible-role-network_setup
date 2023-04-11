Ansible Role: Netplan Setup
=========

Configure Netplan for a host.

Requirements
------------

None

Role Variables
--------------

There are three variables included in the role:
    # Primary DNS server
    dns_server: 10.100.24.11

    # Secondary DNS server
    dns_server_2: 10.100.24.21

    # DNS search domain
    domain: tme.nebulon.com

Additionally, there are another set of variables that are defined in host_vars files for each host. This is done to accomidate dissimilar hosts which may
have differing interface names. This assumes there are two interfaces, only one of which is used.

    # Host management network interface name
    data_int: ens3f0np0

    # Management network address in CIDR format
    mgt_net: 10.100.25.46/22

    # Gateway address in IPV4 format
    gateway4: 10.100.24.1

    # Second, unused (by default) network interface
    data_int_2: ens3f1np1

Dependencies
------------

None

Example Playbook
----------------

    # ===========================================================================
    # Network configuration
    # ===========================================================================
    - name: Configure netplan and DNS settings
      hosts: servers
      tags: play_network_setup

      roles:
        - jedimt.network_setup

License
-------

MIT

Author Information
------------------

Aaron Patten
aaronpatten@gmail.com
