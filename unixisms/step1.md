# Accessing documentation using `man`

`man` is the command to access manual pages on Linux. These tell you how to
use specific commands, programs, and conventions on your system, so knowing
how to efficiently use the `man` command will save you time during research
and troubleshooting. However, if you do not know how to leverage the `man`
command, you may be discouraged from using this resource altogether.

The contents are divided up into nine sections. You can find more information
on these sections in the [Enable Sysadmin article](https://www.redhat.com/sysadmin/top-five-man-options) on `man` pages.

Within these sections, each page has a name. The name of the page is how you
can access the information within it. But what do you do if you don't know the
name of a page? The following command will list all `man` pages available on
your system:

`man -k .`{{execute T1}}

<pre class=file>
<< OUTPUT ABRIDGED >>

zgrep (1)            - search possibly compressed files for a regular expression
zless (1)            - file perusal filter for crt viewing of compressed text
zmore (1)            - file perusal filter for crt viewing of compressed text
znew (1)             - recompress .Z files to .gz files
zramctl (8)          - set up and control zram devices
zsoelim (1)          - interpret .so requests in groff input
</pre>

This list can be quite extensive, though, so you may want to pipe (`|`) the output
into `less` or another text viewer.

If you aren't sure exactly what a page contains, the `-f` option will
print a short description for the specified page.

`man -f grep`{{execute T1}}

<pre class=file>
grep (1)             - print lines matching a pattern
</pre>

One thing that is essential for every Linux user to learn
is tab completion. Tab completion allows you to press the _tab_ key
to fill in the rest of the characters of the current item that you
are typing. This will only complete if you have typed enough
characters to uniquely identify one item that is available. If what
you have typed so far is not unique, then nothing will happen on the
first tab press. The second time you press tab, a list of options that
match the string you have entered will be printed.
Because of this, tab completion saves time and cuts down on mistakes.

You could try tab completion for yourself by re-typing the previous command, but
instead of typing `grep` all the way out, just type `gre` and then press tab.
You will see that `grep` fills in, and you can hit enter to execute the command.

These commmands work great if you know the title of the `man` page that you
are looking for, but what if you want to search for specific contents instead?
`man` supports a `--regex` option that lets you search through all man pages
using regular expressions. This will then open each page that contains a match
sequentially. If you instead wish to just output the location of the matches,
you can use the `-wK` options to return __w__here __k__eywords are
located. Say you were looking for information on the chrony daemon:

`man -wK chronyd`{{execute T1}}

<pre class=file>
/usr/share/man/man1/chronyc.1.gz
/usr/share/man/man8/systemd-timedated.service.8.gz
/usr/share/man/man8/chronyd.8.gz
/usr/share/man/man5/chrony.conf.5.gz
</pre>

Then, if you decided you were looking for the `man` page on commands (section 1),
you could open it with `man chronyc`. Since this command supports the regular
expression option, you can add `--regex` to use
wildcards and other regex characters to help you narrow in your search.
