# postfix

[![Build Status](https://drone.osshelp.ru/api/badges/ansible/postfix/status.svg)](https://drone.osshelp.ru/ansible/postfix)

Ansible role for Postfix installation and configuration. Additionally, role installs postfix-pcre and mailutils packages.

## Usage (example)

```yaml
roles:
  - role: postfix
    mynetworks: 1.2.3.4
    anon_headers: false
    header_checks: 'pcre:/etc/postfix/client.pcre'
    additional_params:
      - {key: smtp_tls_protocols, value: '!SSLv2, !SSLv3'}
```

## Available parameters

### Main

| Param | Default | Description |
| -------- | -------- | -------- |
| `postfix_setup` | `full` | See [OSSHelp KB article](https://oss.help/kb4895) |
| hostname | `ansible_hostname` or `localhost` | Will be used for `myhostname` param in main configuration file. |
| servername | `ansible_hostname` or `localhost` | Will be used for Subject header replacement in mails from cron. |
| mydestination | `localhost` | Will be used for `mydestination` param in main configuration file. |
| mynetworks_default| `127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128` | Will be used as default contents of `mynetworks` param in main configuration file. |
| mynetworks | - | Could be used for adding addresses to `mynetworks` param in main configuration file. |
| interfaces | `all` | Will be used as default contents of `inet_interfaces` param in main configuration file. |
| protocols | `all` | Will be used as default contents of `inet_protocols` param in main configuration file. |
| opendkim | `false` | Whether to generate the default section for OpenDKIM in main configuration file. |
| is_relay | `false` | Whether to anonymize headers in outgoing emails. |
| header_checks | `pcre:/etc/postfix/anon-headers.pcre` | String pointing to file with regexps for headers replacement. |
| postfix_disable_headers_replacement | `false` | Whether to disable headers replacement completely (even for cron emails) |
| tls_params | see defaults | Key-value array with default TLS params. |
| postfix_myorigin.file | `''` | Absolute path to file for usage as `myorigin` param value in main configuration file. |
| postfix_myorigin.value | `''` | Contents of `postfix_myorigin.file`. |
| additional_params | - | Key-value array for adding parameters to main configuration file. |
| postfix_packages | see defaults | List of packages to install |

## FAQ

None, so far.

## Useful links

- [Official documentation](http://www.postfix.org/BASIC_CONFIGURATION_README.html)
- [Our article](https://oss.help/kb891)

## TODO

Nothing, so far.

## License

GPL3

## Author

OSSHelp Team, see <https://oss.help>
