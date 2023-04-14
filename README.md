Ansible Role: Delete Nebulon nPod
=========

Simple role to delete a Nebulon nPod

Requirements
------------

- Ansible 3.0 (Ansible Core 2.10) or later
- Nebulon nebulon.nebulon_on Ansible module 1.4.0+
- Nebulon smartInfrastructure servers with the Nebulon Services Processing Unit (SPU) installed
- Internet connectivity to Nebulon ON UCAPI GraphQL endpoint
- Nebulon Python SDK (nebpyclient) 2.0.8

Role Variables
--------------

There are Nebulon SPU default variables in the defaults/main.yml file.

    # Vault protected credentials. This assumes an Ansible Vault with the vault_neb_username
    # and vault_neb_password variables are defined and passed to the role.
    neb_username: "{{ vault_neb_username }}"
    neb_password: "{{ vault_neb_password }}"

    # Specify a name for the nPod to be deleted
    npod_name: "Default nPod"

Dependencies
------------

None.

Example Playbook
----------------

    # ===========================================================================
    # Delete Nebulon nPod
    # ===========================================================================
    - name: Delete Nebulon nPod
      hosts: localhost
      connection: local
      gather_facts: false

      vars_files:
        # Ansible vault with all required passwords
        - "../../credentials.yml"

      roles:
        - { role: jedimt.nebulon_delete_npod, npod_name: "K8s_Lenovo" }

License
-------

MIT

Author Information
------------------

Aaron Patten
aaronpatten@gmail.com
