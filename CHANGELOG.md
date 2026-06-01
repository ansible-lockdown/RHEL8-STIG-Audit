# Changelog

## STIG V2R7 - 2026 May QA updates

- Renamed `Changelog.MD` to canonical `CHANGELOG.md`
- CONTRIBUTING.rst: rebranded to "Ansible-Lockdown Projects"
- vars/STIG.yml: aligned placeholder values for `rhel8stig_remotelog_server`, `rhel8stig_remotelog_server_port`, `rhel8stig_remotelog_server_protocol` with remediation defaults so out-of-the-box audit checks the same values remediation applies
- vars/STIG.yml: kept `rhel8stig_boot_superuser` at `root` to match the baseline-system value the audit checks against
- run_audit.sh: anchored `VERSION_ID=` grep with `^` to drop the redundant `-w` flag (BSD-grep compatibility)
- RHEL-08-020031 lock-delay test: fixed inverted regex `!/^uint32 [1-5]$/` (rejected legitimate 1-5 values) to positive `/^uint32 [0-5]$/`; dropped malformed `!/^lock-delay=uint32 ^([6-9]...)$/` (stray `^` made the regex match nothing, silently masking out-of-bounds values); broadened positive lock-delay regex to `[0-5]` per XCCDF "5 or less"
- 11 cross-pasted/wrong goss titles aligned verbatim to V2R7 XCCDF: 010121 (FIPS hashing -> null passwords), 010130 (password-auth file -> shadow password suite), 010141 (UEFI auth -> UEFI unique superusers name), 010150 (UEFI title -> BIOS rule), 010201 (generic SSH timeout -> 10-min unresponsive), 010460/010470 (VulnDiscussion paragraph -> rule title), 010610 (typo "prevent ode" -> "prevent code"), 020080 (generic -> lock-delay override), 020082 (idle-delay -> lock-enabled), 020352 (unnecessary accounts -> umask=077)
- RHEL-08-020080 first goss test: corrected meta `Vul_ID: V-230347` -> `V-230354` to match Rule_ID `SV-230354r...` (was a stale paste from sibling 020030)
- RHEL-08-020060 idle-delay test: replaced inverted-only negative `!/^idle-delay=uint32 900/` with positive bounded match `/^idle-delay=(uint32 )?([1-9]|[1-9][0-9]|[1-8][0-9]{2}|900)$/` per XCCDF "If 'idle-delay' is set to '0' or a value greater than '900', this is a finding" - previously the audit FAILED when value was correctly set to 900, the XCCDF-prescribed value
- RHEL-08-010141 + RHEL-08-010201 Rule_ID bumped to V2R7 revisions (`SV-244521r1137691_rule`, `SV-244525r1017331_rule`) - missed by the prior bulk sweep
- RHEL-08-040279 Vul_ID typo `V-24533` -> `V-244553` to match Rule_ID `SV-244553r...` (2 occurrences in the file)
- vars/STIG.yml: removed dead toggle `RHEL_08_030210` (not in V2R7 XCCDF, no goss test consumes it, no rem-side counterpart) - surfaced by cross-repo toggle-parity audit
- vars/STIG.yml: fixed doubled-prefix typo `RPM-GPG-KEY-RPM-GPG-KEY-redhat-release` -> `RPM-GPG-KEY-redhat-release` (broke RHEL-08-010019 GPG key fingerprint check)
- RHEL-08-040172 goss: fixed path from `/etc/systemd/system.conf` (base file) to `/etc/systemd/system.conf.d/55-CtrlAltDel-BurstAction` (drop-in file the rem actually writes); audit was failing because the base file never gets touched
- RHEL-08-010040 goss banner-content check: path `/etc/motd` -> `/etc/issue` to match the file the rem writes (motd is post-login, issue is pre-login banner per the XCCDF SSH-banner intent)
- RHEL-08-010150 Rule_ID revision bump `SV-230235r1017054_rule` -> `SV-230235r1137691_rule` (missed by bulk sweep and prior verification pass)
- vars/STIG.yml: added 7 missing `RHEL_08_*` toggle definitions (010015, 010270, 010275, 010280, 010472, 020360, 030655) - their goss test files gate on `{{ if .Vars.RHEL_08_<id> }}` against previously-undefined vars; tests would silently skip under strict mode
- vars/STIG.yml: reverted `rhel8stig_boot_superuser` default `root` -> `bootloader_admin` to match the rem-side revert (rem asserts the boot superuser must NOT be an existing system user; `root` exists on every host and hard-fails the rem on real systems). Defense-in-depth: GRUB superuser should be distinct from login accounts.

## STIG V2R7 May 2026

- Updated benchmark_version to v2r7 in vars/STIG.yml
- Updated BENCHMARK_VER to v2r7 in run_audit.sh
- Updated README to reference V2R7 release
- Updated Rule_ID revision tags for 24 goss test files to V2R7 values
- Promoted 6 rules from cat_2 to cat_1 (medium -> high severity):
  - RHEL-08-010275 (SV-279931r1184237) - DOD-approved encryption in bind package
  - RHEL-08-010280 (SV-279930r1184239) - IP tunnels FIPS 140-3 cryptographic algorithms
  - RHEL-08-010290 (SV-230251r1184240) - SSH server MACs FIPS 140-2 validated algorithms
  - RHEL-08-010291 (SV-230252r1184241) - SSH server DOD-approved encryption ciphers
  - RHEL-08-010296 (SV-272482r1184242) - SSH client MACs FIPS 140-3 validated algorithms
  - RHEL-08-010297 (SV-272483r1184243) - SSH client ciphers FIPS 140-3 validated algorithms
- Demoted 1 rule from cat_1 to cat_2 (high -> medium severity):
  - RHEL-08-040010 (SV-230492r1184277) - EPEL repository packages

## QA Fixes February 2026

- Added `---` document marker to goss.yml for YAML compliance.
- Fixed malformed CCI values: `CCI-00044` corrected to `CCI-000044` across 16 files (RHEL-08-020010 through RHEL-08-020028).
- Fixed malformed CCI values: `CI-002238` corrected to `CCI-002238` in RHEL-08-020027 and RHEL-08-020028.
- Added missing CCI field to RHEL-08-010297 (CCI-001453) and RHEL-08-020012 (CCI-000044).
- Fixed Rule_ID prefix in RHEL-08-040340: `V-230555r1017317_rule` corrected to `SV-230555r1017317_rule`.
- Fixed Group_Title in RHEL-08-010171: `GPOS-000689` corrected to `GPOS-00068` (consistent with all other SRG-OS-000134 references).
- vars/STIG.yml: Fixed duplicate `RPM-GPG-KEY-` prefix in `rpm_gpg_key` value.
- vars/STIG.yml: Fixed Oracle example section (was copy of Alma with wrong values).
- vars/STIG.yml: Standardized commented examples to use `gpg_keys:` (plural) matching active config.
- vars/STIG.yml: Fixed comment typo `RHEL_08_101120` to `RHEL_08_010120`.
- vars/STIG.yml: Added missing variable definitions for `rhel8stig_banner_file`, `os_gpg_key_pubkey_content`, and `os_gpg_key_pubkey_name`.
- run_audit.sh: Fixed unquoted variables (`$MAX`, `$FORMAT`, `$GROUP`).
- Removed leading blank line from RHEL-08-010673.yml.
- Renamed `cat_2/RHEL-08-020000_020353` to `cat_2/RHEL-08-020000_020360` to match actual file range, updated goss.yml reference.

## STIG V2R6 January 2026

- Aligned vars/STIG.yml with Private-RHEL8-STIG defaults/main.yml and goss template.
- benchmark_version updated to v2r6.
- RHEL-08-010015 - New CAT1 audit check: crypto-policies package installed (SV-279933r1156352_rule).
- RHEL-08-010020 - Crypto-policies implementation (FIPS 140-3 systemwide policy); check aligned to V2R6.
- RHEL-08-010030 - Moved from CAT2 to CAT1 section in vars/STIG.yml (task file already in cat_1/).
- RHEL-08-010149 - Corrected metadata Cat: 1 to Cat: 2 in audit task file.
- RHEL-08-010270 - New CAT1 audit check: cryptographic policy must not be overridden (SV-279932r1156349_rule).
- RHEL-08-010275 - New CAT2 audit check: DOD-approved encryption in bind package (SV-279931r1156346_rule).
- RHEL-08-010280 - New CAT2 audit check: IP tunnels FIPS 140-3 cryptographic algorithms (SV-279930r1156343_rule).
- RHEL-08-010287 - Removed (rule not in V2R6; redundant with crypto-policies).
- RHEL-08-010290 - SSH server MACs: title FIPS 140-2 → FIPS 140-3, Rule_ID SV-230251r1155370_rule.
- RHEL-08-010291 - SSH server ciphers: title and check aligned to FIPS 140-3, Rule_ID SV-230252r1155364_rule, cipher order per V2R6.
- RHEL-08-010293 - Removed (rule not in V2R6; OpenSSL requirement controlled by crypto-policies).
- RHEL-08-010294, 010295, 040342 - Removed (rules not in V2R6; crypto-policies).
- RHEL-08-010472 - New CAT3 audit check: rng-tools package installed (SV-244527r1017333_rule).
- RHEL-08-010660 - Removed (rule not in V2R6).
- RHEL-08-020000, 020340 - Removed (rules not in V2R6.
- RHEL-08-020360 - New CAT2 audit check: shell session TMOUT 10 min inactivity (SV-279929r1156340_rule).
- RHEL-08-030210 - Removed (not in V2R6 or Private-RHEL8-STIG).
- RHEL-08-030655 - New CAT2 audit check: audit cron scripts/executables (SV-274877r1106148_rule).
- Rule_IDs updated to V2R6 for: 010296, 010297, 010350, 010572, 010580, 010630, 010640, 010650, 010670, 010671, 010673, 010700, 010800, 020060, 040070, 040140, 040172, 040370, 010455, 010672, 010674, 010675, 020015, 040010, 040282, 040285.
- Title/check aligned to V2R6: 040010 (EPEL repo check, title); 020060 (title: 15 min session lock); 010350 (title: group-owned by root); 040070 (title: automounter disabled).

## STIG V2R3 April 2025

Many controls Rule ID updated
Other metadata updated where required
Updated some regex expressions
- RHEL-08-101030 - Moved to CAT1
- RHEL-08-010296 - Added Client ssh MACs control.
- RHEL-08-010297 - Added Client ssh Cipher control.
- RHEL-08-010455 - Added requirement.
- RHEL-08-020103 - removed
- RHEL-08-020104 - removed

## STIG V2R2 January 2025

Rule IDs updated for listed controls after changes in control

- RHEL-08-010030 - moved from CAT2 to CAT1 control
- RHEL-08-010130 - hashing round increase min from 5000 to 100000
- RHEL-08-010290 - MAC reordered
- RHEL-08-010291 - Ciphers reordered
- RHEL-08-010292 - RuleID
- RHEL-08-010680 - RuleID

## STIG V2R1 October 2025

Rule IDs updated for all controls
NIST Control ID associations added

- RHEL-08-010350 - command updated
- RHEL-08-010472 - Not Applicable if FIPS
- RHEL-08-020035 - version 8.7+
- RHEL-08-020039 RHEL-08-020040 RHEL-08-020041 RHEL-08-020042, RHEL-08-020070 - TMUX removed
- RHEL-08-020220, RHEL-08-020221 - remember not required for PAM
- RHEL-08-020320 - Updated Check and Fix
- RHEL-08-030603, RHEL-08-040139, RHEL-08-040140, RHEL-08-040141 - Rules updated Ok if no USB peripherals
- RHEL-08-040284
- RHEL-08-040370
- RHEL-08-010001 - removed as not a NIST value

## STIG V1R14 April 2024

Updated Rule IDs

- CAT I
  - RHEL-08-020330 - CAT1
- CAT II
  - RHEL-08-010040
  - RHEL-08-010070
  - RHEL-08-010200
  - RHEL-08-010201
  - RHEL-08-010423
  - RHEL-08-010520
  - RHEL-08-010521
  - RHEL-08-010522
  - RHEL-08-010550
  - RHEL-08-010830
  - RHEL-08-020350
  - RHEL-08-040161
  - RHEL-08-040340
  - RHEL-08-040341

## STIG V1R13 24th Jan 2024

Rule ID updated

- 010001
- 020250
- 020290
- 040090

CAT II

- 020035 - updated rule and added handler for logind restart
- 040020 - /bin/false update and Rule ID update
- 040080 - /bin/false and Rule ID - updated test
- 040111 - /bin/false and Rule ID - updated test

CAT III

- 040021 - /bin/false and Rule ID
- 040022 - /bin/false and Rule ID
- 040023 - /bin/false and Rule ID
- 040024 - /bin/false and Rule ID
- 040025 - /bin/false and Rule ID
- 040026 - /bin/false and Rule ID

## STIG V1R12 25th Oct 2023

Updated to use goss 0.4.4
many controls updated, duplicates identified and resolved

run_audit.sh updated
directory renamed

- 010020
- 010471
- 030741
- 030742
- 040400

## STIG V1R11 26th July 2023

Controls updated

- CAT2:
  - 010030 - Rule ID
  - 010200 - Rule ID
  - 010201 - Rule ID
  - 010290 - Rule ID and SSH MACs updated
  - 010291 - Rule ID and SSH Ciphers updated
  - 010770 - Rule ID
  - 020035 - Rule ID
  - 020041 - Rule ID and tmux script update
  - 030690 - Rule ID and protocol options added
  - 040159 - Rule ID
  - 040160 - Rule ID
  - 040342 - Rule ID and SSH KEX algorithms updated

- CAT3
  - 010471 - Rule ID

## STIG V1R10 27th April 2023

- Added new controls
  - RHEL-08-10019
  - RHEL-08-10358
- updated control IDs
  - RHEL-08-10360
  - RHEL-08-10540
  - RHEL-08-10541
  - RHEL-08-10544
  - RHEL-08-10800
  - RHEL-08-20040
  - RHEL-08-20100
  - RHEL-08-20101
  - RHEL-08-20102
  - RHEL-08-20103
  - RHEL-08-20220
  - RHEL-08-20221
  - RHEL-08-20270
  - RHEL-08-30070
  - RHEL-08-40150

## STIG V1R9 23 Jan 2023

- update to run_audit.sh to allow for Oracle Linux
- alignment with STIG release with remediation
- some tests extended to check for more options
- fixed banner variable

## STIG V1R8 22nd Oct 2022

- auditd outfile name change to include benchmark name
- new Rule ID for listed

- CAT 1
  - RHEL-08-010000
  - RHEL-08-020330 - added ssh_config.d path & stdout check

- CAT 2
  - RHEL-08-010040 - added ssh_config.d path & stdout check
  - RHEL-08-010090 - Title update
  - RHEL-08-010200 - added ssh_config.d path & stdout check
  - RHEL-08-010201 - added ssh_config.d path & stdout check
  - RHEL-08-010360
  - RHEL-08-010372
  - RHEL-08-010373
  - RHEL-08-010374
  - RHEL-08-010383
  - RHEL-08-010384
  - RHEL-08-010400
  - RHEL-08-010430
  - RHEL-08-010500 - added ssh_config.d path & stdout check
  - RHEL-08-010510 - added ssh_config.d path & stdout check
  - RHEL-08-010520 - added ssh_config.d path & stdout check
  - RHEL-08-010521 - added ssh_config.d path & stdout check
  - RHEL-08-010522 - added ssh_config.d path & stdout check
  - RHEL-08-010550 - added ssh_config.d path & stdout check
  - RHEL-08-010671 - updated regex
  - RHEL-08-010830 - added ssh_config.d path & stdout check
  - RHEL-08-020090 - Initial
  - RHEL-08-020104
  - RHEL-08-020110
  - RHEL-08-020120
  - RHEL-08-020130
  - RHEL-08-020140
  - RHEL-08-020150
  - RHEL-08-020160
  - RHEL-08-020170
  - RHEL-08-020190
  - RHEL-08-020221
  - RHEL-08-020230
  - RHEL-08-020280
  - RHEL-08-020300
  - RHEL-08-020350 - CCI update
  - RHEL-08-020352 - update test
  - RHEL-08-040137 - updated tests for versions and rule id
  - RHEL-08-040161 - added ssh_config.d path & stdout check
  - RHEL-08-040209
  - RHEL-08-040210
  - RHEL-08-040220
  - RHEL-08-040230
  - RHEL-08-040239
  - RHEL-08-040240
  - RHEL-08-040249
  - RHEL-08-040250
  - RHEL-08-040259
  - RHEL-08-040260
  - RHEL-08-040261
  - RHEL-08-040262
  - RHEL-08-040270
  - RHEL-08-040279
  - RHEL-08-040280
  - RHEL-08-040281
  - RHEL-08-040282
  - RHEL-08-040283
  - RHEL-08-040284
  - RHEL-08-040285
  - RHEL-08-040286
  - RHEL-08-040340 - added ssh_config.d path & stdout check
  - RHEL-08-040341 - added ssh_config.d path & stdout check
  - RHEL-08-040400 - new control

- CAT 3
  - RHEL-08-010375 - updated check
  - RHEL-08-010376 - updated check
  - RHEL-08-020340 - CCI updated

## STIG V1R7 27th July 2022

- auditd config tests now extended for multiple locations
- pwquality based checks extended for all files
- all files linted for blank line at end of file
- new Rule ID for listed

  - RHEL-08-010372
  - RHEL-08-010373
  - RHEL-08-010375
  - RHEL-08-010376
  - RHEL-08-010379
  - RHEL-08-010380
  - RHEL-08-010383
  - RHEL-08-010384
  - RHEL-08-010430
  - RHEL-08-010671
  - RHEL-08-010672
  - RHEL-08-020041
  - RHEL-08-020104
  - RHEL-08-020110
  - RHEL-08-020120
  - RHEL-08-020130
  - RHEL-08-020140
  - RHEL-08-020150
  - RHEL-08-020160
  - RHEL-08-020170
  - RHEL-08-020230
  - RHEL-08-020280
  - RHEL-08-020300
  - RHEL-08-030650
  - RHEL-08-040111
  - RHEL-08-040170
  - RHEL-08-040209
  - RHEL-08-040210
  - RHEL-08-040220
  - RHEL-08-040230
  - RHEL-08-040239
  - RHEL-08-040240
  - RHEL-08-040250
  - RHEL-08-040259
  - RHEL-08-040260
  - RHEL-08-040261
  - RHEL-08-040262
  - RHEL-08-040270
  - RHEL-08-040279
  - RHEL-08-040280
  - RHEL-08-040281
  - RHEL-08-040282
  - RHEL-08-040283
  - RHEL-08-040284
  - RHEL-08-040285
  - RHEL-08-040286

## STIG V1R6 27th April 2022

- new Rule ID for all listed

  - RHEL-08-030710
  - RHEL-08-010372
  - RHEL-08-010373
  - RHEL-08-010375
  - RHEL-08-010376
  - RHEL-08-010430
  - RHEL-08-010671
  - RHEL-08-020090
  - RHEL-08-030181
  - RHEL-08-040004
  - RHEL-08-040209
  - RHEL-08-040210
  - RHEL-08-040220
  - RHEL-08-040230
  - RHEL-08-040239
  - RHEL-08-040240
  - RHEL-08-040250
  - RHEL-08-040259
  - RHEL-08-040260
  - RHEL-08-040261
  - RHEL-08-040262
  - RHEL-08-040270
  - RHEL-08-040279
  - RHEL-08-040280
  - RHEL-08-040281
  - RHEL-08-040282
  - RHEL-08-040283
  - RHEL-08-040284
  - RHEL-08-040285
  - RHEL-08-040286

## STIG V1R5 27th January 2022

- New Rule ID for all listed
- os_release variable requirements for new rules. Is set by run_audit script but can be manually set in STIG.yml also.

### Cat 1

- RHEL-08-010121 - new control

### Cat 2

- RHEL-08-010030
- RHEL-08-010090
- RHEL-08-010130 - updated control
- RHEL-08-010131 - no longer required
- RHEL-08-010159 - updated control
- RHEL-08-010160 - updated control
- RHEL-08-010287
- RHEL-08-010294 - updated control
- RHEL-08-010331 - new control
- RHEL-08-010341 - new control
- RHEL-08-010351 - new control
- RHEL-08-010359 - new control
- RHEL-08-010360 - updated control
- RHEL-08-010379 - new control
- RHEL-08-010383 -
- RHEL-08-010384
- RHEL-08-010385 - new control
- RHEL-08-010400 - updated control
- RHEL-08-010560 - no longer required
- RHEL-08-010572
- RHEL-08-020041 - updated control
- RHEL-08-020100 - updated control
- RHEL-08-020101 - new control
- RHEL-08-020102 - new control
- RHEL-08-020103 - new control
- RHEL-08-020104 - new control
- RHEL-08-020140
- RHEL-08-020220 - updated control
- RHEL-08-020221 - new control
- RHEL-08-030200 - updated control joined
- RHEL-08-030210 - Now in 030200
- RHEL-08-030220 - Now in 030200
- RHEL-08-030230 - Now in 030200
- RHEL-08-030240 - Now in 030200
- RHEL-08-030270 - Now in 030200
- RHEL-08-030360 - updated control joined
- RHEL-08-030361 - updated control joined
- RHEL-08-030362 - joined to 030361
- RHEL-08-030363 - joined to 030361
- RHEL-08-030364 - joined to 030361
- RHEL-08-030365 - joined to 030361
- RHEL-08-030380 - joined to 030360
- RHEL-08-030420 - updated control joined
- RHEL-08-030430 - joined to 030420
- RHEL-08-030440 - joined to 030420
- RHEL-08-030450 - joined to 030420
- RHEL-08-030460 - joined to 030420
- RHEL-08-030470 - joined to 030420
- RHEL-08-030480 - updated control joined
- RHEL-08-030500 - joined to 030480
- RHEL-08-030510 - joined to 030480
- RHEL-08-030520 - joined to 030480
- RHEL-08-030490 - updated control joined
- RHEL-08-030530 - joined to 030490
- RHEL-08-030540 - joined to 030490
- RHEL-08-030660
- RHEL-08-040020 - updated control joined
- RHEL-08-040080
- RHEL-08-040090
- RHEL-08-040137
- RHEL-08-040320
- RHEL-08-040321 - new control

### Cat 3



## STIG V1R4 27th October 2021

- new rules
- stig.yml in upper case

## All controls changed have a new Rule ID

### Cat 1

- 010020

### Cat 2

- 010141 & 010149 - added extra check
- 010180 - removed incorporated to 010700
- 010190
- 010295
- 010300
- 010320 - check rewritten
- 010330
- 010372 - check updated
- 010373 - check updated
- 010374 - check updated
- 010384
- 010421 - check updated
- 010422 - check updated
- 010423 - check updated

- 010430 - check updated
- 010690
- 020027 - new control
- 020028 - new control
- 020050
- 020353 - added new check
- 040132
- 040133
- 040134
- 040209 - check updated
- 040210 - check updated
- 040220 - check updated
- 040230 - check updated
- 040239 - check updated
- 040240 - check updated
- 040249 - check updated
- 040250 - check updated
- 040259 - new control
- 040260 - part moved to 040259 & new check
- 040261 - new check
- 040262 - new check
- 040270 - new check
- 040279 - new check
- 040280 - new check
- 040281 - new check
- 040282 - new check
- 040283 - new check
- 040284 - new check
- 040285 - new check
- 040286 - new check

### Cat 3

- 010375 - check updated
- 010376 - check updated
- 030601 - check updated
- 030602 - check updated
- 040004 - check updated
- 040021 - aligned check
- 040022 - aligned check
- 040023 - aligned check
- 040024 - aligned check
- 040025
- 040026

## STIG V1R3 23rd July 2021

stig.yml

- linting
- new rules (see below)
- Added new benchmark metadata to be populated

goss.yml & run_audit.sh

- wrapper script for values and corresponding values for benchmark in goss.yml

## All control changes have a new Rule ID

### CAT-1

- RHEL-08-010000
  - update rule id and title
- RHEL-08-010150
  - moved content to 010149
- RHEL-08-020330
  - updated checks
- RHEL-08-020331
  - new control
- RHEL-08-020332
  - new control

### CAT-2

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
- RHEL-08-010490
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
- RHEL-08-020015
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
  - moved some content to 020039
- RHEL-08-020080
  - moved some checks to 020081 & 020082
- RHEL-08-020081
  - new control
- RHEL-08-020082
  - new control
- RHEL-08-030010
  - title change
- RHEL-08-030050
  - updated check
- RHEL-08-030180
  - title updated
- RHEL-08-030181
  - new control
- RHEL-08-030320
- RHEL-08-030630
- RHEL-08-030680
  - package name updated
- RHEL-08-030730
  - moved part check to 030731
- RHEL-08-030731
  - new control
- RHEL-08-040023
  - updated check
- RHEL-08-040100
- RHEL-08-040101
  - new control
- RHEL-08-040135
  - moved some content to 010436 & 010437
- RHEL-08-040136
  - new control
- RHEL-08-040137
  - new control
- RHEL-08-040139
  - new control
- RHEL-08-040140
  - moved some content to 040139 & 040141
- RHEL-08-040141
  - new control
- RHEL-08-040150
  - changes in requirements
- RHEL-08-040159
  - new control
- RHEL-08-040160
  - moved some content to 010459
- RHEL-08-040162
  - Removed
- RHEL-08-040209
  - new control
- RHEL-08-040210
  - moved ipv4 to 040209
  - new title
- RHEL-08-040220
- RHEL-08-040230
- RHEL-08-040239
  - new control
- RHEL-08-040240
  - moved ipv4 to 040239
  - new title
- RHEL-08-040249
  - new control
- RHEL-08-040250
  - moved ipv4 to 040249
- RHEL-08-040270
- RHEL-08-040279
  - new control
- RHEL-08-040280
  - moved ipv4 check to 040279
- RHEL-08-040286
  - new control
- RHEL-08-040370 - Updated CCI mapping

### CAT-3

- RHEL-08-030602
- RHEL-08-030603
