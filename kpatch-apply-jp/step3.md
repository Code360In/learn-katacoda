# Kernel Live Patchを適用する


これで、前のステップで見つけた特定の kpatch-patch パッケージをインストールすることができます。 しかし、もしメンテナンス状況により異なるカーネルを実行しているシステム群に対してこの操作を行いたい場合には、代わりに、Red Hat は uname -r コマンドを組み込んだ yum install または update コマンドを使用して、実行中のカーネルのバージョンを動的に判断し、どの kpatch をインストールするかを決定するために利用することを推奨します。


`yum -y install "kpatch-patch = $(uname -r)"`{{execute}}

<pre class="file">
<< 出力省略 >>

============================================================================================================================================================
 Package                                     Architecture               Version                     Repository                                         Size
============================================================================================================================================================
Installing:
 kpatch-patch-4_18_0-193                x86_64                1-2.el8                  rhel-8-for-x86_64-baseos-rpms                 14 k

Transaction Summary
============================================================================================================================================================
Install  1 Package

<< 出力省略 >>
</pre>

この `yum` コマンドは、埋め込まれた uname -r コマンドの出力にもとづき、 kpatch-patch-4_18_0-193-1-2 をインストールします。これは前のステップでこのシステムで利用できるパッチセットだと確認されたものです。