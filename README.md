# ansible-role-cisco-api
Ansible Role for Cisco PSIRT and Support API to query

- OpenVuln
- EoX - future
- Recommended Software - future

## Current Tasks

- get software version and OS-Type of a device
- Query Cisco OpenVuln API for known vulnerabilities.
- Parse json response for vulnerabilities and append to a report based on a Jinja2 template.
- If errorCode for nun vulnerable version is thrown by Cisco API, append to report Device, current version and errorMessage

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

```yaml
# playbook.yml
---
- name: openvuln
  hosts: ios
  gather_facts: false
  connection: network_cli
  vars:
    client_id: <your client id>
    client_secret: <your client secret>
  roles:
    - cisco-api
```
## Sample Output

ToDo

![Sample PSIRT Report](./sample/report.md)
## License

GPL-3.0-or-later

## Author Information

oliverl-21
