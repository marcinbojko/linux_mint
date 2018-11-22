# Ansible playbook for your super-admin/devops Linux Mint 19 based workstation

## Prerequisites

* installed Linux Mint 19, 64-bit, standard options with extra codecs (selectable during install)
* access to Internet (NAT/bridged)
* openssh-server installed and running
* Ansible in version 2.7 higher

```bash
sudo apt install openssh-server;systemctl enable ssh && systemctl start ssh
```

## Assumptions

* 5GB free space on OS drive
* ssh private key or password method
* user specified in `group_vars` or passed in variable `active_user` will have applications added to `Startup Applications`
* by default extra binaries (outside packages) will be installed in `/usr/local/bin`. If you prefer to keep them in cloud (syn between computers) down belowe I'll atach how to replace binaries with proper symlinks
* Adds repositories with codename and filename
* adds missing pgp keys for repositories
* install essential packages
* install main packages
* install extra/optional packages
* downloads outside repository software and puts it in proper path `/usr/local/bin` by default

## Usage

```bash
ansible-playbook ../linux_mint.yaml -i myhost.lst
```

or start at specific step

```bash
ansible-playbook ../linux_mint.yaml -i myhost.lst --start-at-task="taskname"
```

## Variables

Most Variables are stored in `variables.yml` file. Feel free to adjust them to suit your needs.
For these in playbook:

```yaml
    install_optional: true                    # should optional packages be installed?
    active_user: "{{ ansible_ssh_user }}"     # user for which you're setting folders. By default taken from group_vars
    codename: bionic                          # codename of version you're setting PPAs for
    retries_count: 3                          # how many retries
    delay_time: 10                            # delay time in seconds between retries
    bin_path: /usr/local/bin                  # Where to put all downloades execs.
    reboot_required: false                    # force reboot even if apt upgrade won't changed anything
```

## Repositories

### Repositories: Basic

* ansible - `Ansible`
* remmina - `Best Connection manager - RDP/SSH/VNC`
* y-ppa-manager - `manage your PPA as human being`
* vscode - `suprisingly good product from Microsoft`
* palemoon - `chrome based Java+Flash+nonsecure websites access`
* google chrome - `best browser`
* virtualbox - `virtualization`
* puppet5 -`Puppet5 and PDK for easy module writing`
* kubernetes - `kubeadm & kubectl`
* docker - `Docker-CE`
* veeam - `Veeam Agent for Linux`

### Repositories: Optional

* grub-customizer - `customize black screen to something useful`
* shutter (screenshot & image manipulation) - `screenshoot, manipulate, publish`
* sublime text 3 (vscode alternative)
* enpass (keepass alternative)
* spotify - `music for atmosphere`

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

| htop/atop/nmon/stress |Tools|

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

## 3-rd party apps

### Archives

### Files

## Startups

Some applications are copied to `autostart` folder

* Remmina
* Diodon
* Cairo-Dock
* Synapse
* Redshift
* Shutter

### OS Tweaks

* handle *.local domain with avahi
* handle mDNS with .local domains
* change IO Scheduler for SSD Drives
* initial `Timeshift` launch
* change fstrim schedule to `daily`

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

* create a separate repo, make it public after some tests
* better download file versioning (switch to latest where possible, separate version from URL)
* more idempotency
* better docs
* services handling part (by default in Ubuntu/Debian, installed service is set to `enabled/started`)
* fix Bionic's broken apps like Asbru-CM
* more OS tweaks (scheduler, )
* Add AWS/GCE repositories for their tools.

## Known issues

* Due to how deb packages are treated by app, we should find a way to install always 'latest' version not specific version. If (after initial run) we'll upgrade package outside this script, next time deb part will fail trying to 'downgrade' package.

* Downloading & installing all packages can be time consuming, depending on your Internet connection speed (aprox 40-60 minut)