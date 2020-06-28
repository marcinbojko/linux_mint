# Ansible playbook for your super-admin/devops Linux Mint 19.x based workstation

[![Build Status](https://travis-ci.org/marcinbojko/linux_mint.svg?branch=master)](https://travis-ci.org/marcinbojko/linux_mint)

## Prerequisites

* installed `Linux Mint` 19, 19.1, 19.2, 19.3, 20.0 - all 64-bit, standard options with extra codecs (available as selection during install)
* access to Internet
* `openssh-server` installed and running
* `ansible` in version 2.9 or higher

  ```bash
  sudo apt install openssh-server;systemctl enable ssh && systemctl start ssh
  ```

* PermitRootLogin in `/etc/ssh/sshd_config` if you're using root account

## Assumptions

* 20 GB free space on OS drive
* ssh private key or password method
* user specified in `group_vars` or passed in variable `ansible_ssh_user`
* by default, extra binaries (outside packages) will be installed in `/usr/local/bin` (adjustable by `bin_path` variable) If you prefer to keep them in cloud (sync between computers), down below I'll attach info how to replace binaries with proper symlinks (work in progress)
* adds repositories with codename and filename
* adds missing pgp keys for repositories
* installs essential packages
* installs main packages
* installs extra/optional packages
* downloads 3rd party software and puts it in proper path - `/usr/local/bin` by default (adjustable by `bin_path` variable)
* changes startup settings for specific user (that's why you should not run this as root)
* changes in `ansible.cfg`
* changes in `dconf` settings`
* changes system variables (sysctl)

## In-place upgraded OS warning

Role of this playbook to to work on clean, or clean-upgraded system. This means, it works best when installed for a first time on a clean OS install. I haven't tested it properly on in-place upgrade systems, so both 18=>19 and 19=>20 upgrades are risky and experimental. Make sure all apt repositories (except system ones) are removed from /etc/apt - playbook works best when this list is empty.

## Usage

```bash
ansible-playbook ./linux_mint.yaml -i myhost.lst
```

or change user you're using (startup related stuff will be done for that  specific user user)

```bash
ansible-playbook ./linux_mint.yaml -i myhost.lst --extra-vars "active_user=myuser"
```

in case you'd like to run as root with password or ssh key, you can do desktop related changes for user bob

```bash
ansible-playbook ./linux_mint.yaml -i myhost.lst --extra-vars "active_user=bob"
```

or start at specific step

```bash
ansible-playbook ../linux_mint.yaml -i myhost.lst --start-at-task="taskname"
```

or with specific tags

```bash
ansible-playbook ../linux_mint.yaml -i myhost.lst --tags "base"
```

or passing true/false as JSON

```bash
ansible-playbook ./linux_mint.yaml -i myhost.lst --extra-vars '{"install_optional": "true"}'
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
|install_mitogen|false|install mitogen for ansible and change ansible settings|
|install_state|latest|if set to latest, every pass of playbook will also update packages|
|config_ansible|true|change ansible settings in ansible.cfg|
|config_dconf|true|change dconf settings|
|config_sysctl|true|change sysctl settings|
|active_user|"{{ ansible_ssh_user }}"|user for which you're setting folders. By default taken from group_vars|
|retries_count|4|how many retries|
|delay_time|15|delay time in seconds between retries|
|bin_path|/usr/local/bin|Where to put all downloaded execs|
|reboot_required|false|force reboot even if apt upgrade won't change anything|
|unpack_folder|/tmp/linux_mint|Which folder to use when downloading and unarchiving|

## Repositories

### Repositories: Basic

* `alexx2000` - Double Commander
* `ansible` - Ansible
* `asbru-cm` - Asbru Connection Manager
* `azure-cli` - Azure CLI SDK
* `docker` - Docker-CE
* `gcsfuse` - Google Storage gcsfuse - Mount a GCS bucket locally`
* `gezakovacs` - UNetbootin
* `git-lfs` - Git Large File System
* `googlechrome` - Google Chrome Browser
* `google-cloud-sdk` - Google Cloud Tools SDK
* `kubernetes` - Google Kubernetes kubeadm & kubectl
* `microsoft-prod` - Microsoft .Net Core
* `mozilla-team` - Stable Firefox and Mozilla Software
* `palemoon` - Chromium based Java+Flash browser
* `remmina` - Connection manager - RDP/SSH/VNC
* `shutter` - screenshoot, manipulate, publish
* `synapse-core` - Synaptic Launcher
* `ubuntu-mozilla-security` - Firefox and Thunderbird Security
* `virtualbox` - Virtualization Software
* `vscode` - Microsoft Visual Studio Code
* `y-ppa-manager` - Manage your PPA as human being

### Repositories: Optional

* `brave browser` - Chromium-based secure browsing alternative
* `dockbarx` - DockBarX is a lightweight taskbar
* `enpass` - Password Manager
* `grub-customizer` - customize black screen to something useful
* `insync` - Googledrive & Onedrive Linux Client
* `linuxuprising` - Extra Ubuntu / Linux Mint Applications
* `neofetch` - A command-line system information tool written in bash 3.2+
* `noobslab/icons` - Extra icons pack
* `noobslab/themes` - Extra themes pack
* `puppet5` - Puppet5 and PDK for easy module writing
* `skype` - Microsoft's communicator
* `spotify` - Music streaming service
* `sublime text 3` - Alternative text editor
* `teams` - Microsoft Teams Linux Client
* `trivy` - Container security scanner
* `veeam` - Veeam Agent for Linux
* `veracrypt` - Device encryption utility
* `wepupd8` - packages from webupd8 team

## Packages

### Packages: Essential

### Packages: Basic (not complete list)

|Software|Type|Link|
|------------------|--------|---------------------|
| Amass| In-depth Attack Surface Mapping and Asset Discovery|[https://github.com/OWASP/Amass](https://github.com/OWASP/Amass)|
| AngryIP Scanner |Network Scanner |[https://angryip.org/](https://angryip.org/)|
| Asbru Manager |Connection Manager|[https://www.asbru-cm.net/](https://www.asbru-cm.net/)|
| Azure CLI |Command-line tools for Azure|[https://github.com/Azure/azure-cli](https://github.com/Azure/azure-cli)|
| Balena-etcher |Image Writer| [https://www.balena.io/etcher/](https://www.balena.io/etcher/)|
| Boostnote | Notes for developers |[https://boostnote.io](https://boostnote.io)|
| Ctop| Container process monitor | [https://github.com/bcicen/ctop](https://github.com/bcicen/ctop)|
| Diodon | Clipboard Manager | [https://launchpad.net/diodon](https://launchpad.net/diodon)|
| Dive| Docker image explorer | [https://github.com/wagoodman/dive](https://github.com/wagoodman/dive)|
| Docker/Docker Compose |Docker manager | [https://docs.docker.com/compose/](https://docs.docker.com/compose/)
| Dockle|Container Image Linter for Security|[https://github.com/goodwithtech/dockle](https://github.com/goodwithtech/dockle)|
| Double Commander|File Manager|[https://doublecmd.sourceforge.io/](https://doublecmd.sourceforge.io/)|
| Dropbox/Nemo Integration | Tool | [https://github.com/linuxmint/nemo-extensions/tree/master/nemo-dropbox](https://github.com/linuxmint/nemo-extensions/tree/master/nemo-dropbox)|
| Ffuf|Fast web fuzzer written in Go|[https://github.com/ffuf/ffuf](https://github.com/ffuf/ffuf)|
| GitKraken | Git Client |[https://www.gitkraken.com/](https://www.gitkraken.com/) |
| Google Chrome |Browser | [https://www.google.com/intl/pl_ALL/chrome/](https://www.google.com/intl/pl_ALL/chrome/)|
| Google Cloud SDK|Command-line tools for GCP|[https://cloud.google.com/sdk](https://cloud.google.com/sdk)|
| Google Kubectl/Kubeadm | Kubernetes Manager| [https://kubernetes.io/docs/reference/kubectl/overview/](https://kubernetes.io/docs/reference/kubectl/overview/)|
| Hadolint| Docker linter|[https://github.com/hadolint/hadolint](https://github.com/hadolint/hadolint)|
| Helm | Package manager for Kubernetes |[https://helm.sh/](https://helm.sh/)|
| k3s |Lightweight Kubernetes. 5 less than k8s.|[https://k3s.io/](https://k3s.io/)|
| Keepass | Password Manager| [https://keepass.info/](https://keepass.info/)|
| Kubernetes| Production-Grade Container Orchestration|[https://kubernetes.io/](https://kubernetes.io/)|
| Lens| Kubernetes IDE| [https://k8slens.dev/](https://k8slens.dev/)|
| Minikube | Run Kubernetes locally |[https://github.com/kubernetes/minikube](https://github.com/kubernetes/minikube)|
| Packer | Image creator |[https://www.packer.io/](https://www.packer.io/)|
| Packetsender|Packet Sender can send and receive UDP, TCP, and SSL on the ports of your choosing|[https://packetsender.com/](https://packetsender.com/)|
| Palemoon | Browser alternative (Java_+Flash)| [https://www.palemoon.org/](https://www.palemoon.org/)
| Polaris|Validation of best practices in your Kubernetes clusters|[https://www.fairwinds.com/polaris](https://www.fairwinds.com/polaris)|
| RamboxOS |Multi IM|[https://github.com/TheGoddessInari/hamsket](https://github.com/TheGoddessInari/hamsket)|
| Redshift | Monitor temperature changer| [http://jonls.dk/redshift/](http://jonls.dk/redshift/)|
| Remmina | Remote Connection Manager |[https://remmina.org/](https://remmina.org/)
| RKE| Rancher Kubernetes Engine | [https://github.com/rancher/rke](https://github.com/rancher/rke) |
| Shutter | Screenshot Manipulation| [http://shutter-project.org/](http://shutter-project.org/)|
| Synapse | Symantic Launcher|[https://launchpad.net/synapse-project](https://launchpad.net/synapse-project)|
| Team Viewer | Remote desktop | [https://www.teamviewer.com](https://www.teamviewer.com) |
| Terminus Alpha | Modern Terminal|[https://github.com/Eugeny/terminus](https://github.com/Eugeny/terminus)|
| Terraform|Infrastructure as Code|[https://www.terraform.io/](https://www.terraform.io/)|
| Tflint|TFLint is a Terraform linter focused on possible errors, best practices, etc|[https://github.com/terraform-linters/tflint](https://github.com/terraform-linters/tflint)|
| Vagrant | Unified Workflow|[https://www.vagrantup.com/](https://www.vagrantup.com/)
| Vault | Secrets Manager |[https://www.vaultproject.io/](https://www.vaultproject.io/)
| VirtualBox|Virtualization|[https://www.virtualbox.org/](https://www.virtualbox.org/)|
| Visual Studio Code|Code editor|[https://code.visualstudio.com/](https://code.visualstudio.com/)|
| WPS Office for Linux | Productivity Tools | [https://www.wps.com/wps-office-for-linux/](https://www.wps.com/wps-office-for-linux/)
| XCA | Certificate Manager|[https://hohnstaedt.de/xca/](https://hohnstaedt.de/xca/)|

### Packages: Optional (not complete list)

|Software|Type|Link|
|------------------|--------|---------------------|
| Brave Browser| Browser alternative|[https://brave.com/](https://brave.com/)|
| DockbarX|Panel|[https://github.com/M7S/dockbarx](https://github.com/M7S/dockbarx)|
| Enpass | Password manager | [https://www.enpass.io/](https://www.enpass.io/)|
| GIMP | GNU Image Manipulation Program | [https://www.gimp.org/](https://www.gimp.org/)|
| Insync|Googledrive & Onedrive linux client|[https://www.insynchq.com/](https://www.insynchq.com/)|
| Kodi | Open Source Home Theater| [https://kodi.tv/](https://kodi.tv/)|
| Microsoft Teams | IM |[https://www.microsoft.com/en/microsoft-365?omkt=en-US&rtc=1](https://www.microsoft.com/en/microsoft-365?omkt=en-US&rtc=1)|
| Neofetch |A command-line system information tool written in bash 3.2+| [https://github.com/dylanaraps/neofetch](https://github.com/dylanaraps/neofetch)|
| PDK/Puppet Agent | Puppet Development Kit | [https://puppet.com/docs/pdk/1.x/pdk.html](https://puppet.com/docs/pdk/1.x/pdk.html)|
| Pinta | Drawing/Image Editing| [https://pinta-project.com/pintaproject/pinta/](https://pinta-project.com/pintaproject/pinta/)|
| Skype for Linux | Communicator | [https://www.skype.com](https://www.skype.com)|
| Spotify | Music Player| [https://www.spotify.com/pl/download/linux/](https://www.spotify.com/pl/download/linux/)|
| Sublime Text 3 | Text Editor | [https://www.sublimetext.com/3](https://www.sublimetext.com/3)
| Thunderbird | Email client | [https://www.thunderbird.net](https://www.thunderbird.net)|
| Trivy |A Simple and Comprehensive Vulnerability Scanner for Containers, Suitable for CI|[https://github.com/aquasecurity/trivy](https://github.com/aquasecurity/trivy)
| Veeam Agent for Linux | Backup tool| [https://www.veeam.com](https://www.veeam.com)|
| Veracrypt | Source disk encryption | [https://www.veracrypt.fr/en/Home.html](https://www.veracrypt.fr/en/Home.html)|
| WoeUSB | USB Image writer | [https://github.com/slacka/WoeUSB](https://github.com/slacka/WoeUSB)|

### Packages: Flatpak

|Software|Type|Link|
|------------------|--------|---------------------|
|Postman|The Collaboration Platform for API Development|[https://www.getpostman.com/](https://www.getpostman.com/)|

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
* modifies `sysctl` settings to start use `tcp_congestion_control` set to `bbr`
* modifies `sysctl` settings to decrease default swappiness
* changes `alternatives` for EDITOR
* initial `Timeshift` launch
* change fstrim schedule to `hourly`
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
* add Vagrant plugins
* manual handle 3rd party deb files - pre-download and re-usage on demand
* configure neofetch
* ~~better archive handle~~
* ~~services handling part (by default in Ubuntu/Debian, installed service is set to `enabled/started`)~~
* ~~more idempotency~~
* ~~fix Bionic's broken apps like Asbru-CM~~
* ~~more OS tweaks (i/o scheduler)~~
* ~~add AWS/GCE repositories for their tools~~
* ~~add Visual Studio Code extra extensions~~
* ~~continue to use tagging~~
* ~~add Flatpak packages handling~~
* ~~convert single sysctl values into whole section~~
* ~~better grub defaults handing~~

## Known issues

* Due to how deb packages are treated by apt, we should find a way to install always 'latest' version not specific version. If (after initial run) we'll upgrade package outside this script, next time deb part will fail trying to 'downgrade' package.
* Downloading & installing all packages can be time consuming, depending on your Internet connection speed (aprox 40-60 minut)
* pip - `no module named _internal`

  ```bash
  sudo curl https://bootstrap.pypa.io/get-pip.py -o get-pip.py && sudo python2.7 get-pip.py --force-reinstall
  ```
