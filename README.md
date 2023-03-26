# Other Project
For QEMU ANTIDECTION, see https://github.com/zhaodice/qemu-anti-detection

# Proxmox VE(PVE 7.3-3) Anti Detecion
A patch to hide pve itself, bypass mhyprot,Anti Cheat Expert(ACE),Easy Anti Cheat(EAC),nProtect GameGuard(NP) / VMProtect,~VProtect~(TEST FAILURE,IMMEDIATELY EXITED), Themida, Enigma Protector,Safegine Shielden


# Build deb(or download my release ,jump to install section.)

!!! Create Proxmox VE Virtual Machine as compile enviromnet. !!!

1.Login System


2.Remove the old:
```
mv /etc/apt/sources.list /etc/apt/sources.list.deleted
mv /etc/apt/sources.list.d/pve-enterprise.list /etc/apt/sources.list.d/pve-enterprise.list.deleted
```


3.Add follows into `/etc/apt/sources.list`
```
deb https://mirrors.ustc.edu.cn/debian/ bullseye main contrib non-free
deb https://mirrors.ustc.edu.cn/debian/ bullseye-updates main contrib non-free
deb https://mirrors.ustc.edu.cn/debian/ bullseye-backports main contrib non-free
deb https://mirrors.ustc.edu.cn/debian-security bullseye-security main contrib
#pve源
deb https://mirrors.ustc.edu.cn/proxmox/debian bullseye pve-no-subscription
#ceph源
deb https://mirrors.ustc.edu.cn/proxmox/debian/ceph-pacific bullseye main
#开发源，必须
deb https://mirrors.ustc.edu.cn/proxmox/debian/devel bullseye main
```


4.
(This patch is made at commit 93d558c1eef8f3ec76983cbe6848b0dc606ea5f1)
```
apt update
git clone git://git.proxmox.com/git/pve-qemu.git
cd pve-qemu
git reset --hard 93d558c1eef8f3ec76983cbe6848b0dc606ea5f1
mk-build-deps --install
wget "https://github.com/zhaodice/proxmox-ve-anti-detecion/raw/main/001-anti-detection.patch" -O qemu/001-anti-detection.patch
```

5.

`nano debian/rules`

FIND LINE:

```
	# guest-agent is only required for guest systems
	./configure \
	--with-git-submodules=ignore \
	--docdir=/usr/share/doc/pve-qemu-kvm \
	--localstatedir=/var \
	--prefix=/usr \
	--sysconfdir=/etc \
	--target-list=$(ARCH)-softmmu,aarch64-softmmu \
	--with-suffix="kvm" \
	--with-pkgversion="${DEB_SOURCE}_${DEB_VERSION_UPSTREAM_REVISION}" \
	--audio-drv-list="alsa" \
	--datadir=/usr/share \
	--libexecdir=/usr/lib/kvm \
	--disable-capstone \
	--disable-gtk \
	--disable-guest-agent \
	--disable-guest-agent-msi \
	--disable-libnfs \
	--disable-libssh \
	--disable-sdl \
	--disable-smartcard \
	--disable-strip \
	--disable-xen \
	--enable-curl \
	--enable-docs \
	--enable-glusterfs \
	--enable-gnutls \
	--enable-libiscsi \
	--enable-libusb \
	--enable-linux-aio \
	--enable-linux-io-uring \
	--enable-numa \
	--enable-opengl \
	--enable-rbd \
	--enable-seccomp \
	--enable-slirp \
	--enable-spice \
	--enable-usb-redir \
	--enable-virglrenderer \
	--enable-virtfs \
	--enable-virtiofsd \
	--enable-zstd
```


Inject a line :

```
  # Surprised Detector's Mother Fucker !!!
  patch -p1 < 001-anti-detection.patch
	# guest-agent is only required for guest systems
	./configure \
	--with-git-submodules=ignore \
	--docdir=/usr/share/doc/pve-qemu-kvm \
	--localstatedir=/var \
	--prefix=/usr \
	--sysconfdir=/etc \
	--target-list=$(ARCH)-softmmu,aarch64-softmmu \
	--with-suffix="kvm" \
	--with-pkgversion="${DEB_SOURCE}_${DEB_VERSION_UPSTREAM_REVISION}" \
	--audio-drv-list="alsa" \
	--datadir=/usr/share \
	--libexecdir=/usr/lib/kvm \
	--disable-capstone \
	--disable-gtk \
	--disable-guest-agent \
	--disable-guest-agent-msi \
	--disable-libnfs \
	--disable-libssh \
	--disable-sdl \
	--disable-smartcard \
	--disable-strip \
	--disable-xen \
	--enable-curl \
	--enable-docs \
	--enable-glusterfs \
	--enable-gnutls \
	--enable-libiscsi \
	--enable-libusb \
	--enable-linux-aio \
	--enable-linux-io-uring \
	--enable-numa \
	--enable-opengl \
	--enable-rbd \
	--enable-seccomp \
	--enable-slirp \
	--enable-spice \
	--enable-usb-redir \
	--enable-virglrenderer \
	--enable-virtfs \
	--enable-virtiofsd \
	--enable-zstd
```

6 Current folder is `git's root path`.
```
make clean
make
```

7.You will see a `ERROR` follows

```
dpkg-source: info: unapplying 001-anti-detection.patch
dpkg-source: error: diff pve-qemu-kvm-7.2.0/debian/patches/001-anti-detection.patch modifies file pve-qemu-kvm-7.2.0/subprojects/libvduse/standard-headers/linux/qemu_fw_cfg.h through a symlink: pve-qemu-kvm-7.2.0/subprojects/libvduse/standard-headers/linux
dpkg-buildpackage: error: dpkg-source --after-build . subprocess returned exit status 25
make: *** [Makefile:36: pve-qemu-kvm_7.2.0-8_amd64.deb] Error 25
```

Due to you edit the `rule` files to patch, so it cannot unapplying extra patch

but it is NO PROBLME, because you will see a patched deb file `pve-qemu-kvm_7.2.0-8_amd64.deb` !

# Install deb

copy `pve-qemu-kvm_7.2.0-8_amd64.deb` into your real PVE system.(to use this deb , you should install `librbd-dev=16.2.11-pve1` first)
```
apt install librbd-dev
dpkg -i pve-qemu-kvm_7.2.0-8_amd64.deb
```
