# For proxmox ve 8.1.5-3
# Credit
This step was wrote by @Artipep ,see https://github.com/zhaodice/proxmox-ve-anti-detection/issues/21 .

Referering https://github.com/zhaodice/proxmox-ve-anti-detection/issues/11

Thank you to all contributors

# Please Create Proxmox VE Virtual Machine as compile enviromnet First. 
Keep away from installing pollustion 

# Question: If you have an error while installing mk-build-deps 

mk-build-deps: Unable to install pve-qemu-kvm-build-deps at /usr/bin/mk-build-deps line 459.
mk-build-deps: Unable to install all build-dep packages

add a link to your /etc/apt/sources.list or uncomment the following

deb https://mirrors.ustc.edu.cn/proxmox/debian/ceph-quincy bookworm main



# Question: If you have a build error 

fatal: clone of 'git://git.proxmox.com/git/mirror_qemu' into submodule path '/root/pve-qemu/qemu' failed
Failed to clone 'qemu' a second time, aborting
make: *** [Makefile:21: submodule] Error 1

run in the pve-qemu folder

rm qemu -r
git submodule update

and continue from step 7

# Build Steps

1.Login System

2.Remove the old one:

mv /etc/apt/sources.list /etc/apt/sources.list.deleted
mv /etc/apt/sources.list.d/pve-enterprise.list /etc/apt/sources.list.d/pve-enterprise.list.deleted

3.1.nano /etc/apt/sources.list

deb https://mirrors.ustc.edu.cn/debian/ bookworm main contrib non-free non-free-firmware
deb https://mirrors.ustc.edu.cn/debian/ bookworm-updates main contrib non-free non-free-firmware
deb https://mirrors.ustc.edu.cn/debian/ bookworm-backports main contrib non-free non-free non-free-firmware
deb https://mirrors.ustc.edu.cn/debian-security bookworm-security main contrib non-free non-free-firmware
#pve源
deb https://mirrors.ustc.edu.cn/proxmox/debian bookworm pve-no-subscription
#ceph源
deb https://mirrors.ustc.edu.cn/proxmox/debian/ceph-quincy bookworm main
#开发源，必须
deb https://mirrors.ustc.edu.cn/proxmox/debian/devel bookworm main

3.2 nano /etc/apt/sources.list.d/pve-enterprise.list
#deb https://enterprise.proxmox.com/debian/pve bookworm pve-enterprise

3.3 nano /etc/apt/sources.list.d/ceph.list
#deb https://enterprise.proxmox.com/debian/ceph-quincy bookworm enterprise
#deb http://download.proxmox.com/debian/ceph-quincy bookworm no-subscription

3.4 nano /etc/apt/sources.list.d/pve-no-subscription.list
deb https://mirrors.ustc.edu.cn/proxmox/debian/pve bookworm pve-no-subscription

3.5 update & upgrade your systtem
apt update -y && apt dist-upgrade -y

4. Go to https://git.proxmox.com/?p=pve-qemu.git;a=summary and search for the pve-qemu release you need.
(let's take 8.1.5-3 as an example). 
Open the releases and copy the commit tree (for 8.1.5-3 - d70533ff83b5298fe86733dd6f9341e6e20c01c0)
(This patch is made at commit d70533ff83b5298fe86733dd6f9341e6e20c01c0)
apt install git
git clone git://git.proxmox.com/git/pve-qemu.git
cd pve-qemu
git reset --hard d70533ff83b5298fe86733dd6f9341e6e20c01c0
apt install devscripts
mk-build-deps --install
git submodule update

5.nano debian/rules
FIND LINE:

`# guest-agent is only required for guest systems`

Inject a line :

```
# [Inject]Surprised Detector's Mother Fucker !!!
patch -p1 < 001-anti-detection.patch

# guest-agent is only required for guest systems
...
```

6.nano debian/rules
FIND LINE:

```
# guest-agent is only required for guest systems
./configure \
        --disable-downloads \
	--with-git-submodules=ignore \
	--docdir=/usr/share/doc/pve-qemu-kvm\
	--localstatedir=/var \
	--prefix=/usr \
....
```

Delete the --disable-downloads \ line.

7.Open your webbrowser, visit https://github.com/zhaodice/qemu-anti-detection/ and find the patch version you need.
(for 8.1.5-3 - https://github.com/zhaodice/qemu-anti-detection/blob/main/qemu-8.1.0.patch ), download raw file, rename the file to 001-anti-detection.patch, connect to your server via SFTP, go to root/pve-qemu/qemu and copy the file.

8.Current folder is git's root path and make it
make clean
make

9.install deb
apt install librbd-dev
dpkg -i --force-all pve-qemu-kvm_X.X.X.X_amd64.deb
(for 8.1.5-3 - dpkg -i --force-all pve-qemu-kvm_8.1.5-3_amd64.deb)

(if you need to move the file to another server, connect to your server via SFTP, go to root/pve-qemu and download your pve-qemu-kvm_X.X.X.X_amd64.deb and on the other server put the file into root/pve-qemu and run the above command)
