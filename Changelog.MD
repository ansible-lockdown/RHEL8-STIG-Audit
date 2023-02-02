# Changelog

## Stig V1R9 23 Jan 2023

- update to run_audit.sh to allow for Oracle linux
- alignment with STIG release with remediate
- some tests extended to check for more options
- fixed banner variable

## Stig V1R8 22nd Oct 2022

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
  
## Stig V1R7 27th July 2022

- auditd config tests now exntded for mutliple locations
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

## Stig V1R6 27th April 2022

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

## Stig V1R5 27th January 2022

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



## Stig V1R4 27th October 2021

- new rules
- stig.yml in upper case

## all controls changed have a new ruleid

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

## Stig V1R3 23rd July 2021

stig.yml

- linting
- new rules (see below)
- Added new benchmark metadata to be populated

goss.yml & run_audit.sh

- wrapper script for values and corresponding values for benchmark in goss.yml

## All control changes have a new rule ID

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
  - moved some content to 0101439 & 010141
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
