# Recovering Data from a Lost/Deleted Disk Partition

A hands-on forensics lab using EaseUS Data Recovery Wizard to recover an entire deleted disk partition — not just individual files — including its original folder structure and categorized file contents.

## Scenario
Deleting a partition removes its entry from the disk's MBR partition table, but the actual data within that partition is typically left untouched until something overwrites it. This lab worked through recovering a fully lost partition, including its internal organization, using EaseUS Data Recovery Wizard.

## What I did

### 1. Prepared a safe recovery destination
- Created a dedicated folder (`Recovered Partition`) on a separate drive with sufficient free space — recovered data must never be written back onto the drive being scanned, to avoid overwriting still-unrecovered data mid-process

### 2. Scanned for the lost partition
- Installed EaseUS Data Recovery Wizard; the tool listed a **Lost Partition-1** entry, representing a partition it detected had previously existed but no longer appeared in the active partition table
- Ran an advanced scan against it, which took real time, consistent with examining a large section of raw disk space rather than a single small index

### 3. Reviewed the recovered structure
- A **Lost Files** folder populated under Lost Partition-1, organized into categorized subfolders (Audio Files, Tags, RAW, and others) — the tool had inferred and preserved meaningful structure rather than presenting a flat file dump

### 4. Recovered the entire partition
- Checked the **Lost Partition-1** box at the top level (rather than selecting individual files), enabling the Recover button for the complete recoverable dataset
- Selected the prepared `Recovered Partition` folder as the destination and began extraction

### 5. Noted a trial-version limitation
- The free trial paused partway through recovery, offering to continue via a premium purchase or stop recovering — chose **Don't Recover Any More**, a limitation of the trial software itself, not part of the actual recovery technique

### 6. Reviewed the organized output
- EaseUS created a timestamped subfolder (`EaseUS [DD HH_MM]`) inside `Recovered Partition`, preserving the original `Lost Partition-1 → Lost Files` hierarchy — keeping each recovery session's output clearly separated and dated

## Key takeaways
- Partition deletion and file deletion share the same underlying weakness at different scales — both remove an index/record without necessarily erasing the underlying data
- An attacker deleting a partition to hide evidence relies on the same flawed assumption as deleting a single file: removing the pointer isn't the same as removing the content
- Recovering at the partition level (vs. individual files) preserves folder structure and categorization, which matters for understanding not just what existed but how it was organized
- Automatic categorization by the recovery tool is what makes a recovered partition's contents practically reviewable, rather than an undifferentiated dump requiring manual sorting
- The deliberate act of deleting a partition can itself become a meaningful forensic finding — evidence of intent to conceal, independent of what the recovered files ultimately reveal

## Tools
EaseUS Data Recovery Wizard (Free/Trial)

---
*Completed in an isolated training lab environment on a provisioned Windows 10 VM.*
