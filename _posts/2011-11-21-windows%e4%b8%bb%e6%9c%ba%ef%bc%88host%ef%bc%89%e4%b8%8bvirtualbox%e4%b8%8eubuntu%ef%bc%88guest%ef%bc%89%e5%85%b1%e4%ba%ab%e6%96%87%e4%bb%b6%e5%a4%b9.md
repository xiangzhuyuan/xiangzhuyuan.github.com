---
layout: post
title: Windows主机（Host）下Virtualbox与Ubuntu（Guest）共享文件夹
date: 2011-11-21 12:09
comments: true
categories: []
---
<p>1. 安装增强功能包(Guest Additions) 安装好Ubuntu 8.10后，运行Ubuntu并登录。</p> <p>然后在VirtualBox的菜单里选择"设备(Devices)" -&gt; "安装增强功能包(Install Guest Additions)"。 </p> <p>2. 设置共享文件夹重启完成后点击"设备(Devices)" -&gt; 共享文件夹(Shared Folders)菜单，添加一个共享文件夹，选项固定和临时是指该文件夹是否是持久的。共享名可以任取一个自己喜欢的，比如"test"。 </p> <p>3. 挂载共享文件夹 Ubuntu，在命令行终端下输入： </p><pre class="shell">sudo mkdir /mnt/share
sudo mount -t vboxsf test /mnt/share </pre>
<p>其中"test"是之前创建的共享文件夹的名字,</p>
<p>假如您不想每一次都手动挂载，可以在/etc/fstab中添加一项 </p><pre class="shell">test /mnt/share vboxsf rw,gid=100,uid=1000,auto 0 0 </pre>
<p>这样就能够自动挂载了。 </p>
<p>4. 卸载的话使用下面的命令： </p><pre class="shell">sudo umount -f /mnt/shared </pre>
<p>共享文件夹的名称千万不要和挂载点的名称相同。</p>
<p>比如，上面的挂载点是/mnt/share，如果共享文件夹的名字也是shared的话，在挂载的时候就会出现如下的错误信息 </p><pre class="shell">/sbin/mount.vboxsf: mounting failed with the error: Protocol error </pre>
