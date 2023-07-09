# Ansible playbook for your DevOps/SysOps Linux Mint 21.x based workstation

[![Super-Linter](https://github.com/marcinbojko/linux_mint/actions/workflows/01_lint_me.yml/badge.svg)](https://github.com/marcinbojko/linux_mint/actions/workflows/01_lint_me.yml)
[![Ansible Lint](https://github.com/marcinbojko/linux_mint/actions/workflows/02_ansible_lint.yml/badge.svg)](https://github.com/marcinbojko/linux_mint/actions/workflows/02_ansible_lint.yml)
<!-- TOC -->

- [Ansible playbook for your DevOps/SysOps Linux Mint 21.x based workstation](#ansible-playbook-for-your-devopssysops-linux-mint-21x-based-workstation)
  - [Prerequisites](#prerequisites)
    - [Ansible 2.10 and higher reminder](#ansible-210-and-higher-reminder)
  - [Assumptions](#assumptions)
  - [In-place upgraded OS warning](#in-place-upgraded-os-warning)
    - [Python2 removal](#python2-removal)
  - [Usage](#usage)
  - [Variables](#variables)
    - [variables for tasks](#variables-for-tasks)
  - [Custom variables, custom variable files](#custom-variables-custom-variable-files)
    - [Custom file content](#custom-file-content)
    - [Custom file example](#custom-file-example)
  - [Repositories](#repositories)
    - [Repositories: Basic](#repositories-basic)
    - [Repositories: Optional](#repositories-optional)
  - [Packages](#packages)
    - [Packages: Essential](#packages-essential)
    - [Packages: Basic not complete list](#packages-basic-not-complete-list)
    - [Packages: Optional not complete list](#packages-optional-not-complete-list)
    - [Packages: Flatpak](#packages-flatpak)
    - [Packages: npm](#packages-npm)
  - [Tasks](#tasks)
  - [Startup applications](#startup-applications)
    - [OS Tweaks](#os-tweaks)
  - [Q&A](#qa)
  - [To Do](#to-do)
  - [Known issues](#known-issues)

<!-- /TOC -->

## Prerequisites

- installed `Linux Mint` 21.0/21.1 - all 64-bit, standard options with extra codecs (available as selection during install)
- for previous versions of Mint (20.x) - last release supporting `Linux Mint 20` was 2.6.1
- access to internet
- `openssh-server` installed and running
- `ansible` in version 2.10 or higher
- `sudo ansible-galaxy install -r requirements.yml`

  ```bash
  sudo apt install openssh-server;sudo systemctl enable ssh && sudo systemctl start ssh
  ```

- PermitRootLogin in `/etc/ssh/sshd_config` if you're using root account

### Ansible 2.10 and higher reminder

- `sudo ansible-galaxy install -r requirements.yml  --roles-path /etc/ansible/roles`

## Assumptions

- 20 GB free space on OS drive
- ssh private key or password method
- user specified in `group_vars` or passed in variable `ansible_ssh_user`
- by default, extra binaries (outside packages) will be installed in `/usr/local/bin` (adjustable by `bin_path` variable) If you prefer to keep them in cloud (sync between computers), down below I'll attach info how to replace binaries with proper -ymlinks (work in progress)
- adds repositories with codename and filename
- adds missing pgp keys for repositories
- installs essential packages
- installs main packages
- installs extra/optional packages
- downloads 3rd party software and puts it in proper path - `/usr/local/bin` by default (adjustable by `bin_path` variable)
- changes startup settings for specific user (that's why you should not run this as root)
- changes in `ansible.cfg`
- changes in `dconf` settings
- changes in `sysctl` system settings

## In-place upgraded OS warning

Role of this playbook is to work on clean or cleanly-upgraded system. I haven't tested it properly in case of in-place upgrade systems, so both 18=>19 and 19=>20 upgrades and playbook usage, are risky and experimental. Make sure all apt repositories (except system ones) are removed from /etc/apt - playbook works best when this list is empty.

Warning - systems after upgrade will require: `ansible_python_interpreter=/usr/bin/python3` setting.

### Python2 removal

Be aware several packages (virtualbox-6.1, zenmap) will install python2 and remove python-is-python3 package.

```bash
sudo apt update
sudo apt install python-is-python3
sudo apt update
sudo apt remove python2 --simulate
sudo apt remove python2
```

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

Most variables are stored in `mint19|20.yaml` file. If you need extra settings, instead of modyfing it, use custom variable files.

|variable|default|description|
|--------|-------|-----------|
|install_optional|true|should optional packages be installed|
|install_deb|true|should extra deb packages should be installed|
|install_flatpak|true|should flatpak packages be installed|
|install_npm|true|should npm packages be installed|
|install_vscode_extensions|true|should we install extra vscode extensions|
|install_steampipe_plugins|true|should we install extra steampipe plugins|
|install_zsh|false|should we install oh-my-zsh and p10k theme|
|install_yubico|false|should we install yubico software|
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
|||

### variables for tasks

Are stored in `mint20_tasks.yaml`

## Custom variables, custom variable files

If you don't want to track changes or change main variable file content with every pull, create your own custom variable files. By default playbook will look for files: `mint[ansible_distribution_major_version]*.yaml`
This means - if your distro is `Linux Mint 19`, place a file in a playbook folder witha name: `mint19_custom.yaml`
If your distro is `Linux Mint 20`, place a file in a playbook folder with a name: `mint20_custom.yaml`
These filters are added to .gitignore to not override your changes
Be careful not to add multiple matching files with corresponding names

### Custom file content

```yaml
custom_repositories: []
custom_keys: []
custom_packages: []
```

### Custom file example

`mint20_custom.yaml`

```yaml
custom_repositories:
- repo: ppa:videolan/master-daily
  filename: videolan
custom_keys:
- https://somekeyfile/key.pgp
custom_packages:
- vlc
```

## Repositories

### Repositories: Basic

- `alexx2000` - Double Commander
- `ansible` - Ansible - **removed in Linux Mint 20**
- `azure-cli` - Azure CLI SDK
- `docker` - Docker-CE
- `gcsfuse` - Google Storage gcsfuse - Mount a GCS bucket locally`
- `gezakovacs` - UNetbootin
- `git-lfs` - Git Large File System - **removed in Linux Mint 20**
- `googlechrome` - Google Chrome Browser
- `google-cloud-sdk` - Google Cloud Tools SDK
- `kubernetes` - Google Kubernetes kubeadm & kubectl
- `microsoft-prod` - Microsoft .Net Core
- `mozilla-team` - Stable Firefox and Mozilla Software
- `palemoon` - Chromium based Java+Flash browser
- `remmina` - Connection manager - RDP/SSH/VNC
- `shutter` - screenshoot, manipulate, publish
- `synapse-core` - Synaptic Launcher
- `ubuntu-mozilla-security` - Firefox and Thunderbird Security
- `virtualbox` - Virtualization Software
- `vscode` - Microsoft Visual Studio Code
- `y-ppa-manager` - Manage your PPA as human being

### Repositories: Optional

- `brave browser` - Chromium-based secure browsing alternative
- `dockbarx` - DockBarX is a lightweight taskbar
- `enpass` - Password Manager
- `grub-customizer` - customize black screen to something useful
- `insync` - Googledrive & Onedrive Linux Client
- `linuxuprising` - Extra Ubuntu / Linux Mint Applications
- `neofetch` - A command-line system information tool written in bash 3.2+
- `noobslab/icons` - Extra icons pack
- `noobslab/themes` - Extra themes pack
- `puppet5` - Puppet5 and PDK for easy module writing
- `skype` - Microsoft's communicator
- `spotify` - Music streaming service
- `sublime text 3` - Alternative text editor
- `trivy` - Container security scanner
- `veeam` - Veeam Agent for Linux
- `veracrypt` - Device encryption utility
- `wepupd8` - packages from webupd8 team

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
| Datree|Kubernetes validator |[https://github.com/datreeio/datree](https://github.com/datreeio/datree)|
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
| Gping|Ping with a graph|[https://github.com/orf/gping](https://github.com/orf/gping)|
| Hadolint| Docker linter|[https://github.com/hadolint/hadolint](https://github.com/hadolint/hadolint)|
| Helm | Package manager for Kubernetes |[https://helm.sh/](https://helm.sh/)|
| k3d |k3d creates containerized k3s clusters|[https://k3d.io/](https://k3d.io/)|
| k3s |Lightweight Kubernetes 5 less than k8s|[https://k3s.io/](https://k3s.io/)|
| k9s |Kubernetes CLI Manager|[https://github.com/derailed/k9s](https://github.com/derailed/k9s)|
| Keepass | Password Manager| [https://keepass.info/](https://keepass.info/)|
| Kubeconform| Kubernetes config validator|[https://github.com/yannh/kubeconform](https://github.com/yannh/kubeconform)|
| Kubent| Kubernetes-no-trouble|[https://github.com/doitintl/kube-no-trouble](https://github.com/doitintl/kube-no-trouble)|
| Kubernetes| Production-Grade Container Orchestration|[https://kubernetes.io/](https://kubernetes.io/)|
| Kustomize|Kubernetes customiser |[https://github.com/kubernetes-sigs/kustomize](https://github.com/kubernetes-sigs/kustomize)|
| Lens| Kubernetes IDE| [https://k8slens.dev/](https://k8slens.dev/)|
| Minikube | Run Kubernetes locally |[https://github.com/kubernetes/minikube](https://github.com/kubernetes/minikube)|
| Packer | Image creator |[https://www.packer.io/](https://www.packer.io/)|
| Packetsender|Packet Sender can send and receive UDP, TCP, and SSL on the ports of your choosing|[https://packetsender.com/](https://packetsender.com/)|
| Palemoon | Browser alternative (Java_+Flash)| [https://www.palemoon.org/](https://www.palemoon.org/)
| Polaris|Validation of best practices in your Kubernetes clusters|[https://www.fairwinds.com/polaris](https://www.fairwinds.com/polaris)|
| RamboxOS |Multi IM|[https://github.com/TheGoddessInari/hamsket](https://github.com/TheGoddessInari/hamsket)|
| Rancher Desktop|Rancher Desktop runs Kubernetes and container management on your desktop| [https://rancherdesktop.io/](https://rancherdesktop.io/)|
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
|||

### Packages: Optional (not complete list)

|Software|Type|Link|
|------------------|--------|---------------------|
| Brave Browser| Browser alternative|[https://brave.com/](https://brave.com/)|
| DockbarX|Panel|[https://github.com/M7S/dockbarx](https://github.com/M7S/dockbarx)|
| Enpass | Password manager | [https://www.enpass.io/](https://www.enpass.io/)|
| GIMP | GNU Image Manipulation Program | [https://www.gimp.org/](https://www.gimp.org/)|
| Insync|Googledrive & Onedrive linux client|[https://www.insynchq.com/](https://www.insynchq.com/)|
| Kodi | Open Source Home Theater| [https://kodi.tv/](https://kodi.tv/)|
| Neofetch |A command-line system information tool written in bash 3.2+| [https://github.com/dylanaraps/neofetch](https://github.com/dylanaraps/neofetch)|
| PDK/Puppet Agent | Puppet Development Kit | [https://puppet.com/docs/pdk/1.x/pdk.html](https://puppet.com/docs/pdk/1.x/pdk.html)|
| Pinta | Drawing/Image Editing| [https://pinta-project.com/pintaproject/pinta/](https://pinta-project.com/pintaproject/pinta/)|
| Skype for Linux | Communicator | [https://www.skype.com](https://www.skype.com)|
| Spotify | Music Player| [https://www.spotify.com/pl/download/linux/](https://www.spotify.com/pl/download/linux/)|
| Steampipe| select * from cloud| [https://steampipe.io/](https://steampipe.io/)|
| Sublime Text 3 | Text Editor | [https://www.sublimetext.com/3](https://www.sublimetext.com/3)
| Thunderbird | Email client | [https://www.thunderbird.net](https://www.thunderbird.net)|
| Trivy |A Simple and Comprehensive Vulnerability Scanner for Containers, Suitable for CI|[https://github.com/aquasecurity/trivy](https://github.com/aquasecurity/trivy)
| Veeam Agent for Linux | Backup tool| [https://www.veeam.com](https://www.veeam.com)|
| Veracrypt | Source disk encryption | [https://www.veracrypt.fr/en/Home.html](https://www.veracrypt.fr/en/Home.html)|
| WoeUSB | USB Image writer | [https://github.com/slacka/WoeUSB](https://github.com/slacka/WoeUSB)|
|||

### Packages: Flatpak

|Software|Type|Link|
|------------------|--------|---------------------|
|Postman|The Collaboration Platform for API Development|[https://www.getpostman.com/](https://www.getpostman.com/)|
|Obsidian|Knowledge base and note seystem|[https://obsidian.md/](https://obsidian.md/)|
|||

### Packages: npm

|Software|Type|Link|
|------------------|--------|---------------------|
|Dockerfilelint|Dockerfile linter|[https://github.com/replicatedhq/dockerfilelint](https://github.com/replicatedhq/dockerfilelint)|
|||

## Tasks

|Task|Description|Link|
|----|-----------|----|
|install_yubico_software|Install keys, repositories, packages and dekstop files for Yubico infrastructure|[https://yubico.com](https://yubico.com)|
|configure_zsh|Installs files required by zsh, `oh-my-zsh` and `powerlevel10k`|[https://github.com/ohmyzsh/ohmyzsh](https://github.com/ohmyzsh/ohmyzsh) [https://github.com/romkatv/powerlevel10k](https://github.com/romkatv/powerlevel10k)|
|steampipe_plugins.yaml|Install steampipe plugins | [https://steampipe.io/](https://steampipe.io/)|
|||

## Startup applications

Some applications are copied to `autostart` folder

- Remmina
- Diodon
- DockbarX
- Dropbox
- Synapse
- Redshift
- Shutter

### OS Tweaks

- handle *.local domain with avahi
- changes timezone and ntpd settings
- handle mDNS with .local domains
- modifies `sysctl` settings to start use `tcp_congestion_control` set to `bbr`
- modifies `sysctl` settings to decrease default swappiness
- changes `alternatives` for EDITOR
- initial `Timeshift` launch
- change fstrim schedule to `hourly`
- installs popular Microsoft Visual Studio Code extensions
- change `dconf` settings

## Q&A

- Q: Will it work with specific version WSL/Ubuntu/PidgeonOS?
- A: Don't know, don't care. Do your own variables.yml and check

- Q: What will happen if I'll run it multiple times?
- A: I hope - your applications will be upgraded, same for repos and keys. But, due to DEB/APT dependency you have to look for possible `downgrade` related errors. See `Known Issues` for it.

- Q: Can i check this in Ubuntu
- A: Yes, but be prepared to create your own `variables.yml` and pass it as a parameter

- Q: Can I participate?
- A: Yes, but please create your own branch and do PR. Do not merge to master. Please keep master branch clean.

- Q: I don't know how to do the above
- A: Then don't do it ;)

- Q: Why there is so many Ubuntu:Bionic/Xenial, not so many LinuxMint:Tara repositories?
- A: Tara is built over Bionic packages, so rarely it requires to have specific repo.

## To Do

- better download file versioning (switch to latest where possible, separate version from URL, use separate folder for downloads)
- better docs
- add Vagrant plugins
- manual handle 3rd party deb files - pre-download and re-usage on demand
- configure neofetch
- add cloud-tools section, for people to choose cloud they are using
- ~~better archive handle~~
- ~~services handling part (by default in Ubuntu/Debian, installed service is set to `enabled/started`)~~
- ~~more idempotency~~
- ~~fix Bionic's broken apps like Asbru-CM~~
- ~~more OS tweaks (i/o scheduler)~~
- ~~add AWS/GCE repositories for their tools~~
- ~~add Visual Studio Code extra extensions~~
- ~~continue to use tagging~~
- ~~add Flatpak packages handling~~
- ~~convert single sysctl values into whole section~~
- ~~better grub defaults handing~~

## Known issues

- Due to how deb packages are treated by apt, we should find a way to install always 'latest' version not specific version. If (after initial run) we'll upgrade package outside this script, next time deb part will fail trying to 'downgrade' package.
- Downloading & installing all packages can be time consuming, depending on your Internet connection speed (aprox 40-60 minut)
- pip - `no module named _internal`

  ```bash
  sudo curl https://bootstrap.pypa.io/get-pip.py -o get-pip.py && sudo python2.7 get-pip.py --force-reinstall
  ```

- Playbook exits with a message `Could not import python modules: apt, apt_pkg. Please install python3-apt package`
  - Resolution: set `ansible_python_interpreter=/usr/bin/python3`

- Older distros have problem with some repositories, using PKI part that wasn't part of a ca-certificates.
  - Resolution: Before continuing you're encouraged to install/upgrade `ca-certificates` package. Playbook is doing that as one of first steps, but this doesn't always works properly.
- Step `apt_initial_refresh` can fail due to several reasons:
  - problems with ca-certificates written above
  - duplicate entries found in `/etc/apt/sources.list.d` files
  - expired keys/certificates for repositories
- Step `reset_dconf_values` can fail in Linux Mint 20.x due to python-psutil package being too new.
- `Insync` package strange behavior.
  Installing packages can fail as `Insync` ignores entries in it's own insync.list file and adds new ones. This can lead to mutliple sources being added, thus apt is doomed to fail. In rare cases Insync also tries to add new repos codenames before they exist on their side. Currently there is no workaround for this.

