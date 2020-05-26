# Registering a machine to the Red Hat Insights service

Red Hat Insights is now included in every Red Hat Enterprise Linux subscription.

In most Red Hat Enterprise Linux 8 installations, the insights-client software will be installed by default.  However, the minimal package set does not include installing the insights-client package and other versions of Red Hat Enterprise Linux, while the package is available, will likely need it installed.  

Install the insights-client package on the machine.

`yum -y install insights-client`{{execute}}

Next, register your system with Red Hat Insights.

`insights-client --register`{{execute}}

<pre class=file>
You successfully registered 3c7e6bd4-2673-4d67-83f6-97cd2e420503 to account 6227255.
Successfully registered host a06560c57e40
Automatic scheduling for Insights has been enabled.
Starting to collect Insights data for a06560c57e40
Uploading Insights data.
Successfully uploaded report from a06560c57e40 to account 6227255.
</pre>

From the above output, you can observe that the system has been successfully
registered with the Red Hat Insights service.  As part of the registration,
the machine also uploads a report to the Red Hat Insights service so that
it may be analized for any Insights.

For future reference, make note of your system hostname.

`hostname`{{execute}}

<pre class=file>
a06560c57e40
</pre>

>_NOTE:_ Your hostname will be different than the one listed in the output above

At any time in the future, you can get information about Insights registration
by using the `--status` option to `insights-client`.

`insights-client --status`{{execute}}

<pre class=file>
System is registered locally via .registered file. Registered at 2019-08-14T14:12:37.638768
Insights API confirms registration.
</pre>

Check whether or not SQL Server is running on the machine.

`systemctl status mssql-server.service --no-pager`{{execute T1}}

<pre class="file">
<< OUTPUT ABRIDGED >>

Active: failed (Result: exit-code) since Tue 2020-03-10 03:29:37 EDT; 8min ago

<< OUTPUT ABRIDGED >>
</pre>

Verify that the Active status is __Failed (NOT running)__. Let's have insights tell us what might be the issue here.
