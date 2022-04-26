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


# Security posture via Cisco PSIRT OpenVuln API

*Scanned 6 devices at 2022-04-26 12:52:08*

** Unreachable:** ['8kv1', '8kv2']

## unaffected Devices as of Scanning
- wlc01 with Version:17.08.01 Message: No Cisco Security Advisories affect the Cisco IOSXE Software release
- 8kv0 with Version:17.06.02 Message: No Cisco Security Advisories affect the Cisco IOSXE Software release

## Vulnerable Devices
| Device | Vulnerabilities | Severity | CVSS Score |  First Fixed|
|--------|-----------------|----------|------------|-------------|
|csw01|cisco-sa-trustsec-dos-7fuXDR2| High|7.7|['15.2(7)E5', '15.2(8)E1']|
|csw02|cisco-sa-lldp-dos-sBnuHSjT| Medium|6.8|['15.2(7)E5', '15.2(8)E1']|
|csw02|cisco-sa-ios-nxos-xr-udld-dos-W5hGHgtQ| Medium|7.4|['15.2(5)E2c', '15.2(5a)E1', '15.2(6)E1', '15.2(7)E0s', '15.2(7)E1a', '15.2(7)E2a', '15.2(7)E3k', '15.2(7)E4', '15.2(8)E']|
|csw02|cisco-sa-XE-SAP-OPLbze68| High|7.8|['15.2(4)E6', '15.2(6)E2', '15.2(7)E0s', '15.2(7)E1a', '15.2(7)E2a', '15.2(7)E3k', '15.2(7)E4', '15.2(8)E']|
|csw01|cisco-sa-arp-mtfhBfjE| Medium|5.8|['15.2(2a)E1', '15.2(7)E3k', '15.2(7)E4', '15.2(8)E']|
|csw01|cisco-sa-profinet-J9QMCHPB| High|7.4|['15.2(2a)E1', '15.2(4)E1', '15.2(6)E2b', '15.2(6)E4', '15.2(7)E1', '15.2(7b)E0b', '15.2(8)E']|
|csw02|cisco-sa-info-disclosure-V4BmJBNF| Medium|5.5|['15.2(4)E10a', '15.2(7)E2a', '15.2(7)E3', '15.2(8)E']|
|csw01|cisco-sa-cipdos-hkfTZXEx| High|8.6|['15.2(2a)E1', '15.2(4)E5a', '15.2(4)E10', '15.2(6)E2b', '15.2(6)E4', '15.2(7)E1', '15.2(8)E']|
|csw01|cisco-sa-ikev2-9p23Jj2a| High|7.5|['15.2(4)E9', '15.2(6)E2b', '15.2(6)E3', '15.2(7)E0b', '15.2(7)E1', '15.2(7a)E0b', '15.2(7b)E0b', '15.2(8)E']|
|csw02|cisco-sa-ssh-dos-Un22sd2A| High|7.7|['15.2(4)E10', '15.2(7)E2', '15.2(7b)E0b', '15.2(8)E']|
|csw01|cisco-sa-ssh-dos-Un22sd2A| High|7.7|['15.2(4)E10', '15.2(7)E2', '15.2(7b)E0b', '15.2(8)E']|
|csw01|cisco-sa-snmp-dos-USxSyTk5| High|7.7|['15.2(2a)E1', '15.2(4)E9', '15.2(5)E']|
|csw02|cisco-sa-tcl-ace-C9KuVKmm| Medium|6.7|['15.2(4)E10', '15.2(7)E2', '15.2(7b)E0b', '15.2(8)E']|
|csw02|cisco-sa-sxp-68TEVzR| Medium|6.8|['15.2(4)E9', '15.2(6)E2b', '15.2(7)E1', '15.2(7a)E0b', '15.2(7b)E0b', '15.2(8)E']|
|csw01|cisco-sa-sxp-68TEVzR| Medium|6.8|['15.2(4)E9', '15.2(6)E2b', '15.2(7)E1', '15.2(7a)E0b', '15.2(7b)E0b', '15.2(8)E']|
|csw01|cisco-sa-20200108-ios-csrf| High|8.8|['15.2(4)E10', '15.2(6)E4', '15.2(7)E1', '15.2(7a)E0b', '15.2(7b)E0b', '15.2(8)E']|
|csw01|cisco-sa-20190925-cat4000-tcp-dos| High|8.6|['15.2(2a)E1', '15.2(4)E9', '15.2(5)E1', '15.2(5a)E1', '15.2(6)E0a', '15.2(6)E1', '15.2(7)E0a', '15.2(7)E1', '15.2(7a)E0b', '15.2(7b)E0b']|
|csw02|cisco-sa-20190925-cat4000-tcp-dos| High|8.6|['15.2(2a)E1', '15.2(4)E9', '15.2(5)E1', '15.2(5a)E1', '15.2(6)E0a', '15.2(6)E1', '15.2(7)E0a', '15.2(7)E1', '15.2(7a)E0b', '15.2(7b)E0b']|
|csw01|cisco-sa-20170927-cip| High|8.6|['15.2(2a)E1', '15.2(4)E1', '15.2(5)E1', '15.2(5a)E']|
|csw02|cisco-sa-20170927-cip| High|8.6|['15.2(2a)E1', '15.2(4)E1', '15.2(5)E1', '15.2(5a)E']|



## License

GPL-3.0-or-later

## Author Information

oliverl-21
