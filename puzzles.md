-------------------------------------------------------------------------------
FOR EVERY TASK IN HERE MUST BE ACCOMPLISHED ENTIRELY IN A TERMINAL
-------------------------------------------------------------------------------

Created by: Michael James
Email: tts@michaelbjames.com
Inform me of how long it takes you to complete each task.

I expect you to do a heavy amount of googling around. The software used is
domain specific but there are more abstract takeaways (where to look for
certain kinds of files, permissions, file structures, etc.)



First lets get familiar with the linux system. You're no longer in the world
of easy graphical interfaces to do everything for you.

Everything on linux has a command to run it. Starting firefox (iceweasel here)
is done with the command:

$ iceweasel

Copying one file to another is

$ cp <source file> <destination file>

These things have conventions (source followed by destination)
so to make a link to another file is

$ ln -s <source> <target>

Part of starting up the system is

# /etc/init.d/exim4 start

Note that the last command started with a different character than the others.
It ran as root. Root is special on Linux (and any Unix product such as OS X).
It can do anything. It is the superuser. Be careful with the power that comes
with running a command as root.

If you're ever unsure of **EXACTLY** what a command does, read its manual.
The manual of any command can be accessed with

$ man <command>

(e.g., `man rsync`)



1.
Your first task is to get aquainted with the shell installed on here. You may 
already feel comfortable with bash but there is a whole other world out there of
shells. This shell is zsh

create a shortcut so that `syslog` is a command that runs:
tail -f /var/log/syslog
Ensure that this shortcut works in every instance of a zsh terminal.


That may or may not have been easy for you. Your next task is make a
customization of your choice to a piece of software on this machine.
This is pretty open ended. You might add some color to conky. Maybe change
the shell theme. Maybe do something with the desktop (cycle through some
backgrounds)

start off with:

$ man conky


2.
Let's now get more familiar with regular expressions. They'll help you
throughout the rest of your computer career. You very much need
to be able to describe a set of items with a concise language of what
is similar between all of them.

Note that there are two major classes of regular expressions.
Bash has its own version that is a bit limited but easier to use. (*.txt)
Everyone else uses the otherwise standard version. (.*\.txt)

Command pipes will also help you do more with the regular expressions
you write. You can pluck all files that have a certain type of name
and find out how many are unique.

Write a *sh one liner that will tell me how many user folders we have
in /data. A user folder is defined as a folder whose name is a utln.
The UTLN does not have to be one in the Tufts database, just a pattern
that looks like a utln. A UTLN has at most six letters and exactly
two numbers.


3.
Good, now you should get more comfortable with the concept of a filesystem.
When I was learning this stuff, I thought that if the FS gets corrupt,
everything is lost. The data is much more fluid than I thought.
It takes about 3 hours to wipe a 5400rpm drive (320gb)

Task:
Make a ramdisk in memory


Task:
Make an ext4 fs on temporary USB drive. The goal is that you'll learn to do this
with a user's drive correctly the first time. It might not be ext4 but you may
have to make a new partition or reformat the drive and can't be bothered to use
Havoc.

Make sure you format the right drive!
Check in /dev/sd*
run:
# fdisk -l
Check mounts with:
$ mount



4. Virtualization
This is where things get really fun. You can run any file as input to a VM.
qemu is the command that does the execution. It's fairly powerful.
It's quite challenging to boot OSX in qemu since Apple does some nasty
tricks to ensure their OS only boots on real hardware but there are guides
to boot OSX in qemu. Linux and Windows will be much easier to boot. I do
not know how Windows 8 will fare being VM'd. Win8 uses EFI booting by default
now which is where my concern comes from.

Task:
Boot any hard drive or USB drive in a VM

Google around for qemu commands, seriously.


5. Scripting
It's often easiest to use preexisting utilities to do much of the work for
you. You just need to conduct how the tools will play together.

Write a script that copies files that have a certain string in them in one
directory to another directory.
./script.{sh,rb,js} <keyword> <input directory> <output directory>

The idea of this is to be able to look in a directory of useless filenames
to find the relevant files (e.g., pdf's containing the word psychology
in the directory /data/ecount01 to /data/ecount01/recover/)



Good job. You know your stuff.
You can certainly handle data recovery at this point.

We use testdisk and photorec. Feel free to try another program though.
