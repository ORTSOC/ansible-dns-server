# ansible-dns-server
ORTSOC Infra Role: DNS Server

## Variables

* `dns_records`:
  * An object list, each object has the following keys:
    * `type`: Record type (e.g. `A`)
    * `name`: Name of the record (e.g. `ns1`)
    * `value`: Value of the record (e.g. `1.2.3.4`)
* `primary_dns_server`: The primary DNS server, as will be applied to the SOA record
* `soa_mail_address`: The SOA mail address (e.g. `root.ortsoc.oregonstate.edu`)
* `domain`: The top level domain used for the infrastructure, with a trailing `.` (e.g. `ortsoc.oregonstate.edu.`)

Additionally, in the inventory file, a DNS server must have `dns_server_type=master` or `dns_server_type=slave`.