Ansible Role: Netplan Setup
=========

Build and apply a Netplan configuration for a host. This role assumes there are two physical adapters and will set static IP information for the primary interface and disable the secondary interface. This is useful for Kubernetes deployments where having an active secondary interface can cause traffic routing problems for MetalLB.

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

Additionally, there are another set of variables that are defined in host_vars files for each host. This is done to provide per-host network information. Alternatively, the mgt_net and gateway4 variables could be dynamically generated from hostvars, assuming DHCP reservations apply the correct IP configuration to the host and we are just codifying that information in static assigments.

    # Management network address in CIDR format
    mgt_net: 10.100.25.46/22

    # Gateway address in IPV4 format
    gateway4: 10.100.24.1


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
