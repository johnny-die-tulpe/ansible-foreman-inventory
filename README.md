# Script for ansible to pull an inventory from foreman

Generates inventory that Ansible can understand by making API requests
to Foreman.

Information about the Foreman's instance can be stored in the **foreman.ini** file.
A **base_url**, **username** and **password** need to be provided. The path to an
alternate configuration file can be provided by exporting the **FOREMAN_INI_PATH**
variable.

When run against a specific host, this script returns the following variables
based on the data obtained from Foreman:

+ id
+ ip
+ name
+ environment
+ os
+ model
+ compute_resource
+ domain
+ architecture
+ created
+ updated
+ status
+ ansible_ssh_host

When run in `--list` mode, instances are grouped by the following categories:

+ group

## Usage

Execute uname on all instances in the dev group

``sh
$ ansible -i theforeman.py dev -m shell -a \"/bin/uname -a\"
``

## Notes

This was [submitted](https://github.com/ansible/ansible/pull/6342) to the Ansible project, but the
patch was not included. I'll maintain this script in this repository for now.

## Internet Systems Consortium license

Copyright (c) 2014, Franck Cuny (<franckcuny@gmail.com>)

Permission to use, copy, modify, and/or distribute this software for any purpose
with or without fee is hereby granted, provided that the above copyright notice
and this permission notice appear in all copies.

THE SOFTWARE IS PROVIDED "AS IS" AND THE AUTHOR DISCLAIMS ALL WARRANTIES WITH
REGARD TO THIS SOFTWARE INCLUDING ALL IMPLIED WARRANTIES OF MERCHANTABILITY AND
FITNESS. IN NO EVENT SHALL THE AUTHOR BE LIABLE FOR ANY SPECIAL, DIRECT,
INDIRECT, OR CONSEQUENTIAL DAMAGES OR ANY DAMAGES WHATSOEVER RESULTING FROM LOSS
OF USE, DATA OR PROFITS, WHETHER IN AN ACTION OF CONTRACT, NEGLIGENCE OR OTHER
TORTUOUS ACTION, ARISING OUT OF OR IN CONNECTION WITH THE USE OR PERFORMANCE OF
THIS SOFTWARE.
