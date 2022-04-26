# ansible-role-cisco-api
Ansible Role for Cisco PSIRT and Support API to query

- OpenVuln
- EoX - future
- Recommended Software - future

## Current Tasks

- get software version and OS-Type of a device and query Cisco OpenVuln API for known vulnerabilities.
- Parse json response and append to a report based Jinja2 template.

## ToDo

- implement EoX
- implement Recommended Software

## Requirements

Access to ![Cisco API Console](https://apiconsole.cisco.com/)

How-To ![link](https://community.cisco.com/t5/services-documents/accessing-the-cisco-psirt-openvuln-api-using-curl/ta-p/3652897)

## Role Variables

- client_id: <your client id>
- client_secret: <your client secret>

## Dependencies

Roles: none
Collection:

- cisco.ios
- ansible.netcommon

## Example Playbook

- name: openvuln
  hosts: ios
  gather_facts: false
  connection: network_cli
  vars:
    client_id: <your client id>
    client_secret: <your client secret>
  roles:
    - cisco-api