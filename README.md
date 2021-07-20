# Ansible Role: Automatic package update

Installs updates automatically on RHEL / CentOS 7 and 8 using yum-cron of dnf-automatic services

## Requirements

None.

## Role Variables

 - use_classyllama_autoupdate: true
 - use_classyllama_autoupdate_upgrade_type: minimal-security
 - use_classyllama_autoupdate_download_updates: true
 - use_classyllama_autoupdate_apply_updates: true
 - use_classyllama_autoupdate_random_sleep: 60
 - use_classyllama_autoupdate_notify:  true
 - use_classyllama_autoupdate_email_to: yuriysklyarenko@classyllama.com

See `defaults/main.yml` for details.

## Dependencies

None.

## Example Playbook

    - hosts: all
      roles:
         - { role: classyllama.autoupdate, tags: autoupdate, when: use_classyllama_autoupdate | default(false) }

## Notes

The following update types are supported:

  - default                            = dnf upgrade
  - security                           = dnf --security upgrade
  - security-severity:Critical         = dnf --sec-severity=Critical upgrade
  - minimal                            = dnf --bugfix upgrade-minimal
  - minimal-security                   = dnf --security upgrade-minimal
  - minimal-security-severity:Critical = dnf --sec-severity=Critical upgrade-minimal

with 'minimal-security' as a default type to install only security updates automatically.

## License

This work is licensed under the MIT license. See LICENSE file for details.

