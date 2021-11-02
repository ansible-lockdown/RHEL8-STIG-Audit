# RHEL/CentOS 8 Goss config

## Overview

based on STIG v1r3 July 2021

Ability to audit a system using a lightweight binary to check the current state.

This is:

- very small 11MB
- lightweight
- self contained

It works using a set of configuration files and directories to audit STIG of RHEL/CentOS 7 servers. These files/directories correlate to the STIG Level and STIG_ID

Tested on

- RHEL8
- CentOS8
- Rocky8
- Alma-Linux 8

feedback on any differences between OSs please raise an issue

## variables

file: vars/stig.yml

Please refer to the file for all options and their meanings

STIG listed variable for every control/benchmark can be turned on/off or section

- other controls
enable_selinux
run_heavy_tasks

- bespoke options
If a site has specific options e.g. password complexity these can also be set.

## Usage

- You must have [goss](https://github.com/aelsabbahy/goss/) available to your host you would like to test.

- You must have sudo/root access to the system as some commands require privilege information.

- Assuming you have already clone this repository you can run goss from where you wish.

- The ability to run via a wrapper script in the form of run_audit.sh is also available.
  - This populates benchmark meta fields consistently inline with remediate generated audits
  - This does need to be run full root privileges
  - Some variables can be amended to suit your system

```sh
# run_audit.sh -h
Script to run the goss audit

Syntax: run_audit.sh [-g|-o|-h]
options:
-g     optional - Add a group that the server should be grouped with
-o     optional - file to output audit data
-h     Print this Help.

```

This also works alongside the [Ansible Lockdown RHEL8-STIG role](https://github.com/ansible-lockdown/RHEL8-STIG)

Which will:

- install
- audit
- remediate
- audit

## Audit variables

These are found in vars/stig.yml
Please refer to the file for all options and their meanings

STIG listed variable for every control/benchmark can be turned on/off or section

### The variable files

In this case installed or skipped using the standard name for a package to be installed or _skip to skip a test.

### Extra settings

Some sections can have several options in that case the skip flag maybe passed to the test or exact details relating to your requirements
e.g.

- rhel8stig_use_gui
- rhel8stig_is_router
- rhel8_stig_nameservers:
  - 8.8.8.8
  - 9.9.9.9

## Examples

- run via wrapper script

```sh
# ./run_audit.sh
Success Audit
    "summary": {
        "failed-count": 290,
        "summary-line": "Count: 544, Failed: 290, Duration: 34.588s",
        "test-count": 544,
        "total-duration": 34588004404
    }
}
Completed file can be found at /var/tmp/audit_1631702160.json
```

- full check

```sh
# {{path to your goss binary}} --vars {{ path to the vars file }} -g {{path to your clone of this repo }}/goss.yml --validate

```

example:

```sh
# /usr/local/bin/goss --vars ../vars/cis.yml -g /home/bolly/rh8_cis_goss/goss.yml validate
......FF....FF................FF...F..FF.............F........................FSSSS.............FS.F.F.F.F.........FFFFF....

Failures/Skipped:

Title: 1.6.1 Ensure core dumps are restricted (Automated)_sysctl
Command: suid_dumpable_2: exit-status:
Expected
    <int>: 1
to equal
    <int>: 0
Command: suid_dumpable_2: stdout: patterns not found: [fs.suid_dumpable = 0]


Title: 1.4.2 Ensure filesystem integrity is regularly checked (Automated)
Service: aidecheck: enabled:
Expected
    <bool>: false
to equal
    <bool>: true
Service: aidecheck: running:
Expected
    <bool>: false
to equal
    <bool>: true

< ---------cut ------- >

Title: 1.1.22 Ensure sticky bit is set on all world-writable directories
Command: version: exit-status:
Expected
    <int>: 0
to equal
    <int>: 123

Total Duration: 5.102s
Count: 124, Failed: 21, Skipped: 5

```

- running a particular section of tests

```sh
# /usr/local/bin/goss -g /home/bolly/rh8_cis_goss/section_1/cis_1.1/cis_1.1.22.yml  validate
............

Total Duration: 0.033s
Count: 12, Failed: 0, Skipped: 0

```

- changing the output

```sh
# /usr/local/bin/goss -g /home/bolly/rh8_cis_goss/section_1/cis_1.1/cis_1.1.22.yml  validate -f documentation
Title: 1.1.20 Check for removeable media nodev
Command: floppy_nodev: exit-status: matches expectation: [0]
Command: floppy_nodev: stdout: matches expectation: [OK]
< -------cut ------- >
Title: 1.1.20 Check for removeable media noexec
Command: floppy_noexec: exit-status: matches expectation: [0]
Command: floppy_noexec: stdout: matches expectation: [OK]


Total Duration: 0.022s
Count: 12, Failed: 0, Skipped: 0
```

## further information

- [goss documentation](https://github.com/aelsabbahy/goss/blob/master/docs/manual.md#patterns)
- [STIG standards](https://public.cyber.mil/stigs/downloads/)

## Feedback required

- If using nftables or iptables rather than firewalld
- RHEL-08-010020 FIPS crypto with ec2 has seen to fail with cert issues.
