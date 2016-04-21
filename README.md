# Anaconda 2016 design updates

## Goals

* Optimize Anaconda for the Workstation and Server split
  - Focus on Workstation first
* Simplify installations under typical conditions
    1. Empty disk
    2. Preinstalled OS (Windows or OS X)
    3. Preinstalled OS — but with enough unallocated space
    4. Previous Linux install?
* Realign Anaconda with newer design patterns shared with the desktop

## Audience

Same audience as Fedora Workstation:
<https://fedoraproject.org/wiki/Workstation/Workstation_PRD>

**Summary**: Students, small & indie developers, hobbyists

## Scenarios

All of these scenarios assume people want to run Fedora natively on the hardware. Scenario #1 also happens to apply for those wishing to run Fedora in a virtual machine.

  1. **Empty** drive
    - Automatically allocate and install
    - (How? Basic partitions? LVM? RAID? — Currently, this is LVM.)

  2. Existing OS, **full drive** (not enough installation space)
    * Offer to resize Mac / Win (default)
    - Option to wipe... and then act like scenario #1, falling back to default
      paritioning
    - Check for any possible gotchas (like Windows suspend to disk or unclean
      unmount), and provide a solution on what to do to fix it, to enable
      resizing

  3. Existing OS, **enough unused space** for Fedora
    - Occurs after external partition editor used (remove / resize partitions)
    - Auto-configure remaining space similar to scenario #1 (empty drive)

  4. Existing **Linux with /home** partition
    - Reinstall and re-use /home (without reformatting /home)
    - If there's another, non-Linux OS… option to switch to #1 / #3…?

  5. Existing **Linux without /home** partition — (Ubuntu doesn't use /home)
    - Possible to remove /etc/, /usr/, /var/, but preserve /home/ and do
      a fresh install?
    - Partition might be encrypted (and would need to decrypt before)

## 2016 Redesign Document

[The 2016 Anaconda redesign overview](anaconda-2016-redesign.md) has a lot more detail,
with inline mockups.
