# Ansible playbook for your super-admin/devops Linux Mint 19.x based workstation

## Prerequisites

* installed Linux Mint 19, 19.1, 19.2 64-bit, standard options with extra codecs (available as selection during install)
* access to Internet
* openssh-server installed and running
* Ansible in version 2.8 or higher

  ```bash
  sudo apt install openssh-server;systemctl enable ssh && systemctl start ssh
  ```

* PermitRootLogin in `/etc/ssh/sshd_config` if you're using root account

## Assumptions

* 15GB free space on OS drive
* ssh private key or password method
* user specified in `group_vars` or passed in variable `ansible_ssh_user`
* by default, extra binaries (outside packages) will be installed in `/usr/local/bin`. If you prefer to keep them in cloud (sync between computers), down below I'll attach info how to replace binaries with proper symlinks (work in progress)
* adds repositories with codename and filename
* adds missing pgp keys for repositories
* installs essential packages
* installs main packages
* installs extra/optional packages
* downloads 3rd party software and puts it in proper path - `/usr/local/bin` by default

## Usage

```bash
ansible-playbook ./linux_mint.yaml -i myhost.lst
```

or change user you're using

```bash
ansible-playbook ./linux_mint.yaml -i myhost.lst --extra-vars "ansible_ssh_user=myuser"
```

or start at specific step

```bash
ansible-playbook ../linux_mint.yaml -i myhost.lst --start-at-task="taskname"
```

or with specific tags

```bash
ansible-playbook ../linux_mint.yaml -i myhost.lst --tags "base"
```

## Variables

Most variables are stored in `variables.yml` file. Feel free to adjust them to suit your needs.
For these variables in playbook:

|variable|default|description|
|--------|-------|-----------|
|install_optional|true|should optional packages be installed|
|install_deb|true|should extra deb packages should be installed|
|install_flatpak|true|should flatpak packages be installed
|install_vscode_extensions|true|should we install extra vscode extensions|
|install_mitogen|true|install mitogen for ansible and change ansible settings|
|config_ansible|true|change ansible settings in ansible.cfg|
|config_dconf|true|change dconf settings|
|config_sysctl|true|change sysctl settings|
|active_user|"{{ ansible_ssh_user }}"|user for which you're setting folders. By default taken from group_vars|
|codename|bionic|codename of version you're setting PPAs for|
|retries_count|4|how many retries|
|delay_time|15|delay time in seconds between retries|
|bin_path|/usr/local/bin|Where to put all downloaded execs|
|reboot_required|false|force reboot even if apt upgrade won't change anything|

## Repositories

### Repositories: Basic

* alexx2000 - `Double Commander`
* ansible - `Ansible`
* asbru-cm - `Asbru Connection Manager`
* azure-cli - `Azure CLI`
* docker - `Docker-CE`
* gcsfuse - `gcsfuse - Mount a GCS bucket locally`
* gezakovacs - `UNetbootin`
* git-lfs - `git-lfs`
* google chrome - `best browser`
* google-cloud-sdk - `google cloud sdk`
* kubernetes - `kubeadm & kubectl`
* microsoft-prod - `.Net Core`
* mozilla-team - `Stable Firefox and Mozilla`
* palemoon - `chrome based Java+Flash+nonsecure websites access`
* puppet5 -`Puppet5 and PDK for easy module writing`
* remmina - `Best Connection manager - RDP/SSH/VNC`
* synapse-core - `synapse-core`
* ubuntu-mozilla-security - `Firefox and Thunderbird Security`
* virtualbox - `virtualization`
* vscode - `suprisingly good product from Microsoft`
* y-ppa-manager - `manage your PPA as human being`

### Repositories: Optional

* enpass (keepass alternative)
* compholio
* dockbarx - `DockBarX is a lightweight taskbar`
* forticlient
* grub-customizer - `customize black screen to something useful`
* neofetch -  `A command-line system information tool written in bash 3.2+`
* noobslab/icons
* noobslab/themes
* puppet5
* shutter (screenshot & image manipulation) - `screenshoot, manipulate, publish`
* skype
* spotify - `music for atmosphere`
* sublime text 3 (vscode alternative)
* trivy - `container security scanner`
* wepupdt8
* veeam - `Veeam Agent for Linux`
* veracrypt - `device encryption utility`

## Packages

### Packages: Essential

### Packages: Basic (not complete list)

|Software|Type|Link|
|------------------|--------|---------------------|
| AngryIP Scanner |Network Scanner |[https://angryip.org/](https://angryip.org/)|
| GitKraken | Git Client |[https://www.gitkraken.com/](https://www.gitkraken.com/) |
| Remmina | Remote Connection Manager |[https://remmina.org/](https://remmina.org/)
| Helm | Package manager for Kubernetes |[https://helm.sh/](https://helm.sh/)|
| Hashicorp Packer | Image creator |[https://www.packer.io/](https://www.packer.io/)|
| Hashicorp Vault | Secrets Manager |[https://www.vaultproject.io/](https://www.vaultproject.io/)
| Hashicorp Vagrant | Unified Workflow|[https://www.vagrantup.com/](https://www.vagrantup.com/)
| Docker/Docker Compose |Docker manager | [https://docs.docker.com/compose/](https://docs.docker.com/compose/)
| Google Kubectl/Kubeadm | Kubernetes Manager| [https://kubernetes.io/docs/reference/kubectl/overview/](https://kubernetes.io/docs/reference/kubectl/overview/)|
| Synapse | Symantic Launcher|[https://launchpad.net/synapse-project](https://launchpad.net/synapse-project)|
| XCA | Certificate Manager|[https://hohnstaedt.de/xca/](https://hohnstaedt.de/xca/)|
| Shutter | Screenshot Manipulation| [http://shutter-project.org/](http://shutter-project.org/)|
| Palemoon | Browser alternative (Java_+Flash)| [https://www.palemoon.org/](https://www.palemoon.org/)
| Google Chrome |Browser | [https://www.google.com/intl/pl_ALL/chrome/](https://www.google.com/intl/pl_ALL/chrome/)|
| Keepass | Password Manager| [https://keepass.info/](https://keepass.info/)|
| Redshift | Monitor temperature changer| [http://jonls.dk/redshift/](http://jonls.dk/redshift/)|
| Boostnote | Notes for developers |[https://boostnote.io](https://boostnote.io)|
| Franz | Multi IM |[https://meetfranz.com/](https://meetfranz.com/)|
| Diodon | Clipboard Manager | [https://launchpad.net/diodon](https://launchpad.net/diodon)|
| Dropbox/Nemo Integration | Tool | [https://github.com/linuxmint/nemo-extensions/tree/master/nemo-dropbox](https://github.com/linuxmint/nemo-extensions/tree/master/nemo-dropbox)|
| Team Viewer | Remote desktop | [https://www.teamviewer.com](https://www.teamviewer.com) |
| WPS Office for Linux | Productivity Tools | [https://www.wps.com/wps-office-for-linux/](https://www.wps.com/wps-office-for-linux/)
| ctop| Container process monitor | [https://github.com/bcicen/ctop](https://github.com/bcicen/ctop)|
| dive| Docker image explorer | [https://github.com/wagoodman/dive](https://github.com/wagoodman/dive)|
| trivy|A Simple and Comprehensive Vulnerability Scanner for Containers, Suitable for CI|[https://github.com/knqyf263/trivy](https://github.com/knqyf263/trivy)
|rke| Rancher Kubernetes Engine | [https://github.com/rancher/rke](https://github.com/rancher/rke) |
| htop/atop/nmon/stress |Monitoring tools| |

### Packages: Optional (not complete list)

|Software|Type|Link|
|------------------|--------|---------------------|
| Spotify | Music Player| [https://www.spotify.com/pl/download/linux/](https://www.spotify.com/pl/download/linux/)|
| Enpass | Password manager | [https://www.enpass.io/](https://www.enpass.io/)|
| Kodi | Open Source Home Theater| [https://kodi.tv/](https://kodi.tv/)|
| Cairo-Dock | Desktop interface | [http://glx-dock.org/](http://glx-dock.org/)|
| PDK/Puppet Agent | Puppet Development Kit | [https://puppet.com/docs/pdk/1.x/pdk.html](https://puppet.com/docs/pdk/1.x/pdk.html)|
| Thunderbird | Email client | [https://www.thunderbird.net](https://www.thunderbird.net)|
| Pinta | Drawing/Image Editing| [https://pinta-project.com/pintaproject/pinta/](https://pinta-project.com/pintaproject/pinta/)|
| Skype for Linux | Communicator | [https://www.skype.com](https://www.skype.com)|
| WoeUSB | USB Image writer | [https://github.com/slacka/WoeUSB](https://github.com/slacka/WoeUSB)|
| Veeam Agent for Linux | Backup tool| [https://www.veeam.com](https://www.veeam.com)|
| Sublime Text 3 | Text Editor | [https://www.sublimetext.com/3](https://www.sublimetext.com/3)
| Veracrypt | Source disk encryption | [https://www.veracrypt.fr/en/Home.html](https://www.veracrypt.fr/en/Home.html)|
| Neofetch | | [https://github.com/dylanaraps/neofetch](https://github.com/dylanaraps/neofetch)|
| GIMP | GNU Image Manipulation Program | [https://www.gimp.org/](https://www.gimp.org/)|

## 3-rd party apps

### Archives

### Files

## Startup applications

Some applications are copied to `autostart` folder

* Remmina
* Diodon
* DockbarX
* Dropbox
* Synapse
* Redshift
* Shutter

### OS Tweaks

* handle *.local domain with avahi
* changes timezone and ntpd settings
* handle mDNS with .local domains
* change IO Scheduler for SSD Drives (use install_grub=true)
* modifies `sysctl` settings to start use `tcp_congestion_control` set to `bbr`
* modifies `sysctl` settings to decrease default swappiness
* changes `alternatives` for EDITOR
* initial `Timeshift` launch
* change fstrim schedule to `hourly`
* adds `mitogen` for your ansible and adjusts config (if your mitogen is older then ansible disable this using `config_ansible=false`)
* installs popular Microsoft Visual Studio Code extensions
* change `dconf` settings

## Q&A

* Q: Will it work with specific version WSL/Ubuntu/PidgeonOS?
* A: Don't know, don't care. Do your own variables.yml and check

* Q: What will happen if I'll run it multiple times?
* A: I hope - your applications will be upgraded, same for repos and keys. But, due to DEB/APT dependency you have to look for possible `downgrade` related errors. See `Known Issues` for it.

* Q: Can i check this in Ubuntu
* A: Yes, but be prepared to create your own `variables.yml` and pass it as a parameter

* Q: Can I participate?
* A: Yes, but please create your own branch and do PR. Do not merge to master. Please keep master branch clean.

* Q: I don't know how to do the above
* A: Then don't do it ;)

* Q: Why there is so many Ubuntu:Bionic/Xenial, not so many LinuxMint:Tara repositories?
* A: Tara is built over Bionic packages, so rarely it requires to have specific repo.

## To Do

* better download file versioning (switch to latest where possible, separate version from URL, use separate folder for downloads)
* better docs
* ~~services handling part (by default in Ubuntu/Debian, installed service is set to `enabled/started`)~~
* ~~more idempotency~~
* ~~fix Bionic's broken apps like Asbru-CM~~
* ~~more OS tweaks (i/o scheduler)~~
* ~~add AWS/GCE repositories for their tools~~
* ~~add Visual Studio Code extra extensions~~
* ~~continue to use tagging~~
* add Vagrant plugins
* ~~add Flatpak packages handling~~
* convert single sysctl values into whole section
* better grub defaults handing
* manual handle 3rd party deb files - pre-download and re-usage on demand
* configure neofetch

## Known issues

* Due to how deb packages are treated by apt, we should find a way to install always 'latest' version not specific version. If (after initial run) we'll upgrade package outside this script, next time deb part will fail trying to 'downgrade' package.
* Downloading & installing all packages can be time consuming, depending on your Internet connection speed (aprox 40-60 minut)
* pip - `no module named _internal`

  ```bash
  sudo curl https://bootstrap.pypa.io/get-pip.py -o get-pip.py && sudo python2.7 get-pip.py --force-reinstall
  ```
