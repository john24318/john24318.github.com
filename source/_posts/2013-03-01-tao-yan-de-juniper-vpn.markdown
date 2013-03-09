---
layout: post
title: "討厭的Juniper VPN"
date: 2013-03-01 01:22
comments: true
categories: VPN Linux
---
在Linux安裝討厭的Juniper VPN
<!-- more -->


1.完整移除Java:  
Remove all the Java related packages (Sun, Oracle, OpenJDK, IcedTea plugins, GIJ):
{% codeblock %}
sudo apt-get update
apt-cache search java | awk '{print($1)}' | grep -E -e '^(ia32-)?(sun|oracle)-java' -e '^openjdk-' -e '^icedtea' -e '^(default|gcj)-j(re|dk)' -e '^gcj-(.*)-j(re|dk)' -e 'java-common' | xargs sudo apt-get -y remove
sudo apt-get -y autoremove
{% endcodeblock %}

Purge config files:  
{% codeblock %}
dpkg -l | grep ^rc | awk '{print($2)}' | xargs sudo apt-get -y purge
{% endcodeblock %}

Remove Java config and cache directory:  
{% codeblock %}
sudo bash -c 'ls -d /home/*/.java' | xargs sudo rm -rf
{% endcodeblock %}

Remove manually installed JVMs:  
{% codeblock %}
sudo rm -rf /usr/lib/jvm/*
{% endcodeblock %}

Remove Java entries, if there is still any, from the alternatives:  
{% codeblock %}
for g in ControlPanel java java_vm javaws jcontrol jexec keytool mozilla-javaplugin.so orbd pack200 policytool rmid rmiregistry servertool tnameserv unpack200 appletviewer apt extcheck HtmlConverter idlj jar jarsigner javac javadoc javah javap jconsole jdb jhat jinfo jmap jps jrunscript jsadebugd jstack jstat jstatd native2ascii rmic schemagen serialver wsgen wsimport xjc xulrunner-1.9-javaplugin.so; do sudo update-alternatives --remove-all $g; done
{% endcodeblock %}

Search for possible remaining Java directories:  
{% codeblock %}
sudo updatedb
sudo locate -b '\pack200'
{% endcodeblock %}


2.移除Juniper_networks並重新安裝Java  
Deleting ~/.juniper_networks:  
{% codeblock %}
rm -rf .juniper_networks/^C
{% endcodeblock %}

Download the Oracle JDK from PPA:  
{% codeblock %}
sudo add-apt-repository ppa:webupd8team/java
sudo apt-get update
sudo apt-get install oracle-java7-installer
sudo apt-get install oracle-java7-set-default
{% endcodeblock %}

Config java (Choose Oracle java)
{% codeblock %}
sudo update-alternatives --config java
sudo update-alternatives --config javac
sudo update-alternatives --config javaws
{% endcodeblock %}

Link browser to java applet
{% codeblock %}
mkdir ~/.mozilla/plugins/
ln -s /usr/lib/jvm/java-7-oracle/jre/lib/i386/libnpjp2.so ~/.mozilla/plugins/
{% endcodeblock %}

3.打開firefox瀏覽器連VPN, 查看/var/log/sysloeg, 應該不會出現以下error了:  
kernel: [ 1947.323900] ncsvc[2468]: segfault at 2 ip b75a3b8e sp bfa05320 error 4 in libc-2.15.so[b755e000+19f000]


Reference:  
[http://dougmunsinger.com/posts/juniper-vpn-on-linux.html](http://dougmunsinger.com/posts/juniper-vpn-on-linux.html)
[http://askubuntu.com/questions/84483/how-to-completely-uninstall-java](http://askubuntu.com/questions/84483/how-to-completely-uninstall-java)
[http://mad-scientist.us/juniper.html](http://mad-scientist.us/juniper.html)
[http://www.webupd8.org/2012/01/install-oracle-java-jdk-7-in-ubuntu-via.html](http://www.webupd8.org/2012/01/install-oracle-java-jdk-7-in-ubuntu-via.html)
