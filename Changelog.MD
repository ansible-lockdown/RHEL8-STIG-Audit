# Changelog

stig V1R3 23rd July 2021

stig.yml

- linting
- new rules (see below)

## All control changes have a new rule ID

## CAT-1

- RHEL-08-010000
  - update rule id and title
- RHEL-08-020330
  - updated checks
- RHEL-08-020331
  - new control
- RHEL-08-020332
  - new control

## CAT-2

- RHEL-08-010001
  - new control
- RHEL-08-010049
  - new control
- RHEL-08-010050
  - moved some content to 010049
- RHEL-08-010130
  - moved some content to 010131
- RHEL-08-010131
  - new control
- RHEL-08-010140
  - moved some content to 010141
- RHEL-08-010141
  - new control
- RHEL-08-010149
  - new control
- RHEL-08-010150
  - moved content to 010149
- RHEL-08-010151
- RHEL-08-010152
  - new control
- RHEL-08-010159
  - new control
- RHEL-08-010160
  - moved content to 010159
- RHEL-08-010200
  - moved content to 010201
- RHEL-08-010201
  - new control
- RHEL-08-010287
  - new control
- RHEL-08-010290
  - moved content to 010287
- RHEL-08-010291
  - tidy up
- RHEL-08-010384
- RHEL-08-010390
  - updated
- RHEL-08-010400
  - updated check
- RHEL-08-010422
  - updated check
- RHEL-08-010472
  - new control
- RHEL-08-010490, RHEL-08-030630
  - update title
- RHEL-08-010510
  - updated check
- RHEL-08-010521
  - title
  - moved content to 010522
- RHEL-08-010522
  - new control
- RHEL-08-010544
  - new control
- RHEL-08-010571
  - updated to bios boot only check
- RHEL-08-010572
  - new control
- RHEL-08-010700
  - title update
- RHEL-08-010710
- RHEL-08-010731
  - new control
- RHEL-08-010740
  - updated rule
- RHEL-08-010741
  - new control
- RHEL-08-010830
- RHEL-08-020011,
  - updated checks
- RHEL-08-020013
  - updated checks
- RHEL-08- 020015
  - updated checks
- RHEL-08-020017
  - updated checks
- RHEL-08-020019
  - updated checks
- RHEL-08-020021
  - updated check
- RHEL-08-020023
  - updated checks
- RHEL-08-020025
  - new control
- RHEL-08-020026
  - new control
- RHEL-08-020031
  - new control
- RHEL-08-020032
  - new control
- RHEL-08-020039
  - new control
- RHEL-08-020040
  - moved some comntent to 020039
- RHEL-08-020080
  - moved some checks to 020081 & 020082
- RHEL-08-020081
  - new control
- RHEL-08-020082
  - new control


- RHEL-08-030010 - Fixed typo in Check and Fix, and added a restart daemon statement to the Fix text.
- RHEL-08-030050 - Updated configuration file entry in Fix Text.
- RHEL-08-030180 - Updated the Rule Title and Check content.
- RHEL-08-030181 - Added a requirement to start and enable the auditd.service.
- RHEL-08-030320, RHEL-08-030603 - Fixed typo in Fix text.
- RHEL-08-030602 - Fixed typo in the finding statement.
- RHEL-08-030680 - Updated package name throughout requirement.
- RHEL-08-030730 - Updated the requirement to move the space_left_action to a unique STIG ID.
- RHEL-08-030731 - Added a requirement to notify the SA and ISSO when the audit storage reaches 75 percent capacity.
- RHEL-08-040023 - Fixed typos throughout.
- RHEL-08-040100 - Updated the requirement to move the enable firewall portion to a unique STIG ID.
- RHEL-08-040101 - Added a requirement to enable the firewall.
- RHEL-08-040060 - Removed this requirement as the version of openssh that ships with RHEL 8 does not support SSHv1.
- RHEL-08-040003 - Merged with RHEL-08- 040370.
- RHEL-08-040370 - Updated CCI mapping.
- RHEL-08-040135 - Updated the requirement to move the "enable fapolicy" and "configure a deny- all, permit-by-exception policy" portions to unique STIG IDs.
- RHEL-08-040136 - Added requirement for the fapolicy module to be enabled.
- RHEL-08-040137 - Added requirement for the fapolicy module to be configured with a deny-all, permit-by-exception policy.
- RHEL-08-040139 - Added requirement to have the USBGuard installed.
- RHEL-08-040140 - Updated requirement to move installation and enablement of USBGuard to unique STIG IDs.
- RHEL-08-040141 - Added requirement to enable the USBGuard.
- RHEL-08-040150 - Updated Check and Fix content by removing extraneous services.
- RHEL-08-040159 - Added requirement to have SSH installed.
- RHEL-08-040160 - Updated requirement to move the installation of SSH to a unique STIG ID.
- RHEL-08-040162 - Removed requirement for the client configuration of SSH.
- RHEL-08-040209 - Added requirement to prevent IPv4 ICMP redirect messages from being accepted. - RHEL-08-040210, RHEL-08-040240, RHEL-08- 040250, RHEL-08-040280 - Updated requirement to move the IPv4 portion to a unique STIG ID.
- RHEL-08-040220, RHEL-08-040230, RHEL-08- 040270 - Updated the "not applicable" statement.
- RHEL-08-040239 - Added requirement to prevent IPv4 source-routed packets from being forwarded.
- RHEL-08-040249 - Added requirement to prevent IPv4 source-routed packets from being forwarded by default.
- RHEL-08-040279 - Added requirement to ignore IPv4 ICMP redirect messages.
- RHEL-08-040286 - Added requirement to harden the BPF JIT.
