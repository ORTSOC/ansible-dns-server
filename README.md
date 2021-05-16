ansible-dns-server
=========

Deploys a DNS server for internal DNS resolving.

Requirements
------------

- Debian 10
- sudo
- ssh

Role Variables
--------------

- `dns_records`:
  - An object list, each object has the following keys:
    - `type`: Record type (e.g. `A`)
    - `name`: Name of the record (e.g. `ns1`)
    - `value`: Value of the record (e.g. `1.2.3.4`)
- `primary_dns_server`: The primary DNS server, as will be applied to the SOA record
- `soa_mail_address`: The SOA mail address (e.g. `root.ortsoc.oregonstate.edu`)
- `domain`: The top level domain used for the infrastructure, with a trailing `.` (e.g. `ortsoc.oregonstate.edu.`)
- `forwarders`: List of upstream DNS servers
- `rpz_records`: blocklist of domains as records
- `dns_ip_subnets`: the IP subnet to allow DNS resolution on.
- `nameservers`: list of DNS name servers that run this role.

Example Playbook
----------------

sets up es1.my.domain, es2.my.domain, and es3.my.domain A records.
```yaml
dns_records:
  - type: A
    name: es1
    value: 1.1.1.1

  - type: A
    name: es2
    value: 1.1.1.2

  - type: A
    name: es3
    value: 1.1.1.3

domain: my.domain

primary_dns_server: ns1.my.domain.
soa_mail_address: root.my.domain.

nameservers:
  - ns1.my.domain.
  - ns2.my.domain.

dns_ip_subnets:
  - 128.193.124

rpz_records:
  - type: CNAME
    name: baddomain.xyz
    value: .

forwarders:
  - 8.8.8.8
  - 8.8.4.4
```
License
-------

GPL3

Author Information
------------------

ORTSOC, Oregon State University
