# What is the `~` directory?

Linux is filled with shortcuts, and learning these shortcuts
is a crucial step to speeding up your work. One such shortcut
is that `~` is aliased to the current user's home directory.
The `~` alias works in any case where you have to specify a path.
If you wanted to list the contents of the _openscap_data_ subdirectory
located in the home directory of __root__, the following command is
valid:

`ls ~/openscap_data`{{execute T1}}

<pre class=file>
eval_remediate_report.html  eval_remediate_results.xml
</pre>

>_NOTE:_ This is another place where you can practice tab completion.
Typing `ls ~/op` and then pressing tab will complete the path for you
since there is nothing else in __root__'s home directory starting
with `op`.

This means that running `cd ~` will always change directories to
the home directory of the user that you are logged in as.

`cd ~`{{execute T1}}

You will see that your current directory has changed from

<pre class=file>
[root@dd2f5f5596bf /]#
</pre>

to

<pre class=file>
[root@dd2f5f5596bf ~]#
</pre>

>_NOTE:_ The `cd` command contains yet another shortcut, where
running `cd` without any arguments will behave the same as
running `cd ~`.

Print the full path to the directory you are currently in,
the `~` directory, using the "print working directory" command:

`pwd`{{execute T1}}

<pre class=file>
/root
</pre>

This shows that `~` is equivalent to `/root`, the home directory
for the __root__ user. Try the same test for a different user account
on this system, __rhel__. Switch to __rhel__ in the second terminal
tab:

`su - rhel`{{execute T2}}

Adding the `-` after `su` will automatically change directories into
the __rhel__ user's home directory, so print the full directory again:

`pwd`{{execute T2}}

<pre class=file>
/home/rhel
</pre>

You can see that when logged in as __rhel__, `~` is equivalent to
`/home/rhel`, which is the __rhel__ user's home directory.

>_NOTE:_ The __root__ user home directory is in a unique location,
`/root`. All other users' home directories will be located
following the convention `/home/<username>`, as in the case
of the __rhel__ user's home directory.
