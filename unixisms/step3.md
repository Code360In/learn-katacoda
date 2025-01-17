# Accessing hidden files

Sometimes it is useful to have a file or directory that it hidden, meaning it
does not show up when running `ls` normally. This may be because the file is not
often used, or because the file shouldn't be tampered with by inexperienced users.
Any file or directory that begins with a `.` in the name will be interpreted as
hidden, and will only show up when using the `-a` option with `ls`.

List the files in your current directory:

`ls`{{execute T1}}

<pre class=file>
anaconda-ks.cfg  openscap_data  original-ks.cfg
</pre>

Now, try it again with the `-a` option. Many more files and directories will
show up, even though you have not changed where you are looking. 

`ls -a`{{execute T1}}

<pre class=file>
.   anaconda-ks.cfg  .bash_profile  .cshrc  .hushlogin     original-ks.cfg  .tcshrc
..  .bash_logout     .bashrc        .gnupg  openscap_data  .ssh             .viminfo
<pre class=file>

Adding the `-a` option reveals that there are numerous hidden files and directories
in this home directory. These are hidden because they are not files that
you would interact with often, so there is no need for them to clutter up __root__'s
home directory visually. However, they are data that is associated with the
user, so it is beneficial from an organization point of view to store them
in the home directory associated with their specific user.   

>_NOTE_: One common hidden directory you will commonly run into is the `.git`
directory. This is part of any git repository and stores data used in version
control for your local repository.

Creating a new hidden file or directory is quite simple, just start the name with
a `.`

`touch .hidden-file`{{execute T1}}

Now that this file is created, confirm that it only shows up when using `ls -a`:

`ls`{{execute T1}}

<pre class=file>
anaconda-ks.cfg  openscap_data  original-ks.cfg
</pre>

`ls -a`{{execute T1}}

<pre class=file>
.   anaconda-ks.cfg  .bash_profile  .cshrc  .hidden-file  openscap_data    .ssh     .viminfo
..  .bash_logout     .bashrc        .gnupg  .hushlogin    original-ks.cfg  .tcshrc
<pre class=file>
