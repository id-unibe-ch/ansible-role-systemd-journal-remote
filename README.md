# Ansible Role: systemd-journal-remote

An Ansible role that manages systemd-journal-remote. Currently the role has the following
features:

* Install systemd-journal-remote
* Configure `/etc/systemd/journal-remote.conf`

## Requirements

No prerequisites necessary at the moment.

## Role Variables

Available variables are listed below, along with default values (see also `defaults/main.yml`):
<!-- 
**STYLE GUIDE:**
* All variables should start with the role name (e.g. `systemd_journal_remote_`)
* Variables that are private to the role and only important to people developing the role should be set in `vars/main.yml` and start with `__systemd_journal_remote_`
-->

<!-- Enter ALL mandatory variables into `tasks/check_mandatory_vars.yml` so their presence gets checked before each run -->
### systemd_journal_remote_server_key_file

The server’s private key file.

```yaml
systemd_journal_remote_server_key_file: '/etc/ssl/certs/fqdn.key'
```

**Optional:** No

**Default value:** Undefined

### systemd_journal_remote_server_certificate_file

The server’s certificate file.

```yaml
systemd_journal_remote_server_certificate_file: '/etc/ssl/certs/fqdn.pem'
```

**Optional:** No

**Default value:** Undefined

### systemd_journal_remote_trusted_certificate_file

The file containing the CA certificates.

```yaml
systemd_journal_remote_trusted_certificate_file: /etc/ssl/certs/ca.cert.pem'
```

**Optional:** No

**Default value:** Undefined

### systemd_journal_remote_seal: true
Sign the log data in the journal for maximum security; otherwise set this to false.

```yaml
systemd_journal_remote_seal: true
```

**Optional:** Yes

**Default value:** `true`

### systemd_journal_remote_split_mode

The logs from the remote clients will be split by host in `/var/log/journal/remote`. If you would prefer all the logs to be added to a single file set this to `none`.

```yaml
systemd_journal_remote_split_mode: 'host'
```

**Optional:** Yes

**Default value:** `'host'`

## Example Playbook

Including an example of how to use your role (for instance, with variables passed
in as parameters) is always nice for users too:

```yaml
- hosts: servers
  roles:
     - role: unibeid.systemd-journal-remote
       vars:
         - systemd_journal_remote_server_key_file: '/etc/ssl/certs/fqdn.key'
         - systemd_journal_remote_server_certificate_file: '/etc/ssl/certs/fqdn.pem'
         - systemd_journal_remote_trusted_certificate_file: /etc/ssl/certs/ca.cert.pem'
```

## Compatibility

This role has been written for and tested on and is therefore compatible with:

* rockylinux9

## License

MIT

## Author Information

The role was created in 2026 by the IT-Services Office of the University of Bern
