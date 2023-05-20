# Other Project
For QEMU ANTIDECTION, see https://github.com/zhaodice/qemu-anti-detection

# Proxmox VE(PVE 7.3-3) Anti Detecion
 | Type       | Engine | Bypass |
 |------------|--------|--------|
 | AntiCheat | Mhyprot | ☑️   |
 | AntiCheat | Anti Cheat Expert(ACE) | ☑️   |
 | AntiCheat | Easy Anti Cheat(EAC) | ☑️   | 
 | AntiCheat | nProtect GameGuard(NP) | ☑️   | 
 | AntiCheat | Vanguard | ‼️(ERROR 1: Incorrect function error) | 
 | Encrypt | VMProtect | ☑️   | 
 | Encrypt | VProtect | ☑️   |  
 | Encrypt | Themida | ☑️   |  
 | Encrypt | Enigma Protector | ☑️   |  
 | Encrypt | Safegine Shielden | ☑️   |  


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
apt install  devscripts
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
	# [Inject]Surprised Detector's Mother Fucker !!!
	patch -p1 < 001-anti-detection.patch
	
	# guest-agent is only required for guest systems
	...
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

# VM Show

`/etc/pve/qemu-server/100.conf`
```
args: -cpu host,+kvm_pv_unhalt,+kvm_pv_eoi,hv_spinlocks=0x1fff,hv_vapic,hv_time,hv_reset,hv_vpindex,hv_runtime,hv_relaxed,kvm=off,hv_vendor_id=intel,vmware-cpuid-freq=false,enforce=false,host-phys-bits=true,hypervisor=off -smbios type=0,version=UX305UA.201 -smbios type=1,manufacturer=ASUS,product=UX305UA,version=2021.1 -smbios type=2,manufacturer=Intel,version=2021.5,product='Intel i9-12900K' -smbios type=3,manufacturer=XBZJ -smbios type=17,manufacturer=KINGSTON,loc_pfx=DDR5,speed=4800,serial=114514,part=FF63 -smbios type=4,manufacturer=Intel,max-speed=4800,current-speed=4800
audio0: device=ich9-intel-hda,driver=none
balloon: 0
bios: ovmf
boot: order=sata0
cores: 12
cpu: host,flags=+pcid
efidisk0: local-lvm:vm-100-disk-0,efitype=4m,pre-enrolled-keys=1,size=4M
hostpci0: 0000:01:00,pcie=1,x-vga=1
machine: pc-q35-7.1
memory: 32768
meta: creation-qemu=7.1.0,ctime=1679627202
name: Windows11
net0: rtl8139=CA:09:F3:97:56:0B,bridge=vmbr0,firewall=1
numa: 1
ostype: win11
sata0: HugeSSD:100/vm-100-disk-1.qcow2,discard=on,size=64G,ssd=1
sata1: HugeHDD:100/vm-100-disk-0.qcow2,backup=0,size=128G
smbios1: uuid=24c326dd-3cec-48fc-bb9f-87aa3984e2c9,manufacturer=QVNVUw==,product=VVgzMDVVQQ==,version=MjAyMS4x,serial=MTI0NjY3,sku=MTM0NDY4,family=Ng==,base64=1
sockets: 1
tpmstate0: local-lvm:vm-100-disk-1,size=4M,version=v2.0
usb0: host=4e53:5406
usb1: host=040b:2000
vga: none
vmgenid: 020229e3-2cdb-4a91-8e77-1d04cf1f060f
```

![Screenshot_20230329_124628](https://user-images.githubusercontent.com/63996691/228429821-443a3a9f-8d24-4712-9760-bbfb1f10aa8d.png)
