# tufts-data-recovery
Data recovery resources for Tufts Technology Support/Student Repair

This repository contains information about the (primarily Linux-based) data
recovery techniques used by the Student Repair branch of Tufts Technology Support.

# Current file manifest

  - [puzzles.md](puzzles.md) covers a progression of puzzles to solve to help get
    acquainted with the Linux command line. This is the suggested starting place for
    newcomers.
    
  - [SMART.md](SMART.md) contains information about how to use the command line tool
    `smartctl`, which is used to assess the health of a hard drive.
    
  - [Linux CLI key commands and concepts.md](Linux CLI key commands and concepts.md)
    is a bulleted list of commands and concepts to be familiar with. This is intended
    to be used as a general reference rather than a learning tool, per sé, though it
    may be used as the latter.

#Planned additions

- Solutions to the puzzles

- Steps to follow for a typical data recovery case, depending on whether:
  
  1. The files were accidentally deleted
  2. The partition was formatted or deleted, but not overwritten, or if the partition is corrupt  
  3. The partition was formatted or deleted and then overwritten
    
- Pages on the following tools:
  - Ddrescue
  - Testdisk
  - The Sleuth Kit
  - QEMU


# See also

[The Ubuntu Data Recovery help page](https://help.ubuntu.com/community/DataRecovery) has helpful primers on the following tools:

- Partition recovery tools like:
  - GNU Parted (`parted`)
  - Testdisk (`testdisk`)
  - Gpart (`gpart`)

- The imaging tool GNU Ddrescue (`ddrescue`)

- Individual file recovery tools:
  - Foremost (`foremost`)
  - Scalpel (`scalpel`)
  - Magic Rescue (`magicrescue`)
  - Photorec (`photorec`)
  - Recoverjpeg (`recoverjpeg`)
  - NTFS Undelete (`ntfsundelete`)

- The recovery suite Sleuthkit (specifically `autopsy`, `dls`, `fls`, `icat`, and `sorter`)

[The Art of the Command Line](https://github.com/jlevy/the-art-of-command-line)
has a more thorough introduction to the Linux/Unix command line.
