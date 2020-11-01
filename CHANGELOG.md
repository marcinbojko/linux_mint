# Changelog "linux_mint"

## Version 2.1.0 [2020-11-01]

* [APPLICATION] upgraded `helm3` to version 3.4.0
* [APPLICATION] upgraded `minikube` to version 1.14.2
* [APPLICATION] upgraded `angryip` to version 3.7.3
* [APPLICATION] upgraded `hadolint` to version 1.18.2
* [APPLICATION] upgraded `packer` to version 1.6.5
* [APPLICATION] upgraded `terraform` to version 1.13.5
* [APPLICATION] upgraded `tflint` to version 0.20.3
* [APPLICATION] upgraded `vault` to version 1.5.5
* [APPLICATION] upgraded `wpsoffice` to version 11.1.0.9719
* [APPLICATION] upgraded `ctop` to version 0.7.4

## Version 2.0.9 [2020-10-18]

* wrong architecture binary for `packer`

## Version 2.0.8 [2020-10-17]

* [BREAKING_CHANGE] remove RamboxOS from list. Replaced by (name change) Hamsket. Please remember to remove RamboxOS package manually
* [APPLICATION] upgraded `hamsket` to version 0.6.0
* [APPLICATION] upgraded `docker-compose` to version 1.27.4
* [APPLICATION] upgraded `k3s` to version 1.19.3
* [APPLICATION] upgraded `lens` to version 3.6.7
* [APPLICATION] upgraded `minikube` to version 1.14.0
* [APPLICATION] upgraded `rke` to version 1.2.1
* [APPLICATION] upgraded `amass` to version 3.10.5
* [APPLICATION] upgraded `packer` to version 1.6.4
* [APPLICATION] upgraded `terraform` to version 0.13.4
* [APPLICATION] upgraded `vault` to version 1.5.4

## Version 2.0.7 [2020-09-24]

* [APPLICATION] upgraded `tflint` to version 0.20.2
* [APPLICATION] upgraded `amass` to version 3.10.4
* [APPLICATION] upgraded `minikube` to version 1.13.1
* [APPLICATION] upgraded `lens` to version 3.6.4
* [APPLICATION] upgraded `helm3` to version 3.3.4
* [APPLICATION] upgraded `k3s` to version 1.19.2
* [APPLICATION] upgraded `wps-office` to version 11.1.0.9662

## Version 2.0.6 [2020-09-18]

* workaround in case where future tasks add proper gpg keys (timesyncd install will fail)
* [APPLICATION] upgraded `etcher` to version 1.5.109
* [APPLICATION] upgraded `terraform` to version 0.13.3
* [APPLICATION] upgraded `lens` to version 3.6.3
* [APPLICATION] upgraded `helm` v3 to version 3.3.2
* [APPLICATION] upgraded `docker-compose` to version 1.27.3
* [APPLICATION] upgraded `k3s` to version 1.18.9

## Version 2.0.5 [2020-09-14]

* [APPLICATION] upgraded `minikube` to version 1.13.0
* [APPLICATION] upgraded `amass` to version 3.10.3
* [APPLICATION] upgraded `helm` v3 to version  3.3.1
* [APPLICATION] upgraded `terraform` to version 0.13.2
* [APPLICATION] upgraded `packetsender` to version 7.0.5
* [APPLICATION] upgraded `rke` to version 1.1.7
* [APPLICATION] upgraded `boostnote` to version 0.16.1
* [APPLICATION] upgraded `tflint` to version 0.20.1
* [APPLICATION] upgraded `etcher` to version 1.5.108
* [APPLICATION] upgraded `docker-compose` to version 1.27.2
* [APPLICATION] upgraded `lens` to version 3.6.0
* [VSCODE] remove obsoleted extensions

## Version 2.0.4 [2020-08-26]

* [APPLICATION] upgraded `minikube` to version 1.12.2
* [APPLICATION] upgraded `lens` to version 3.5.3
* [APPLICATION] upgraded `terminus alfa` to version 1.0.120
* [APPLICATION] upgraded `tflint` to version 0.19.1
* [APPLICATION] upgraded `vault` to version 1.5.3
* [APPLICATION] upgraded `amass` to 3.9.1
* [APPLICATION] upgraded `wps-office` to version 11.1.0.9615.XA
* [APPLICATION] upgraded `etcher` to version 1.5.102
* [APPLICATION] upgraded `terraform` to version 0.12.29
* [APPLICATION] upgraded `polaris` to version 1.2.1
* [APPLICATION] upgraded `k3s` to version 1.18.8
* [APPLICATION] upgraded `dockle` to version 0.3.1
* [APPLICATION] upgraded `etcher` to version 1.5.106
* [APPLICATION] upgraded `packer` to version 1.6.2
* [APPLICATION] upgraded `vagrant` to version 2.2.10
* [APPLICATION] upgraded `helm` to version 3.3.0
* [PACKAGES] added `clusterssh`
* [APPLICATION] added `kubeval` - [https://github.com/instrumenta/kubeval](https://github.com/instrumenta/kubeval)
* fixes in `mode` for created files

## Version 2.0.3 [2020-07-17]

* more test for Linux Mint 19=>20 upgrade scenario
* [EXPERIMENTAL] added section in README.md how to get rid of python 2
* [DCONF] added shortcuts for `Synapse` and `Diodon` applications
* [APPLICATION] upgraded `etcher`to 1.5.101
* [APPLICATION] upgraded `amass` to 3.7.4
* [APPLICATION] upgraded `terraform` to version 0.12.28
* [APPLICATION] upgraded `wps-office` to version 11.1.0.9604.XA
* [APPLICATION] upgraded `k3s` to version 1.18.6
* [APPLICATION] upgraded `rke` to version 1.1.4
* [APPLICATION] upgraded `minikube` to version 1.12.0
* [APPLICATION] added `Key Store Explorer` in version 5.4.3
* [PACKAGES] upgraded `dotnet-sdk` to version 3.1 for Linux Mint 19
* [PACKAGES] added `zsh`
* [PACKAGES] added `netcat`

## Version 2.0.2 [2020-07-03]

* `CHANGELOG.md` changed

## Version 2.0.1 [2020-07-03]

* [REPOSITORY] added `libreoffice` ppa
* [BREAKING_CHANGE] introduced `custom` variable files for easier config separation - more in README.md
* [APPLICATION] upgraded `docker-compose` to version 1.26.2
* [APPLICATION] upgraded `lens` to version 3.5.1

## Version 2.0.0 [2020-06-28]

* [MINT] addedd experimental support for Linux Mint 20 `Ulyana`. After reaching stability support for Linux Mint 19 will be removed.
* variables are now separated by major distribution version and used accordingly
* [BREAKING_CHANGE] Linux Mint 20 doesn't offer support for `powershell` other than a snap
* [BREAKING_CHANGE] Linux Mint 20 by default uses python3.
* [BREAKING_CHANGE] Linux Mint 20 `ansible` ppa is removed in favour of system packages
* [BREAKING_CHANGE] Linux Mint 20 `git-lfs` ppa is removed in favour of system packages
* [BREAKING_CHANGE] Linux Mint 20 `woeusb` package is removed
* [BREAKING_CHANGE] Linux Mint 20 `zenmap` package is removed
* [APPLICATION] upgraded `rke` to version 1.1.3
* [APPLICATION] upgraded `amass` to version 3.7.3
* [APPLICATION] upgraded `tflint` to version 1.17.0

## Version 1.4.1 [2020-06-23]

* [APPLICATION] upgraded `packer` to version 1.6.0
* [APPLICATION] upgraded `k3s` to version 1.18.4
* [APPLICATION] upgraded `etcher` to 1.5.100
* [APPLICATION] upgraded `helm3` to version 3.2.4
* [APPLICATION] upgraded `amass` to version 3.7.2
* [APPLICATION] upgraded `polaris` to version 1.1.0
* [PIP] added `gittyleaks` [https://github.com/kootenpv/gittyleaks](https://github.com/kootenpv/gittyleaks)
* fixes in `applications` desktop files section [https://github.com/marcinbojko/linux_mint/pull/4](https://github.com/marcinbojko/linux_mint/pull/4)
* removed duplicate packages [https://github.com/marcinbojko/linux_mint/pull/4](https://github.com/marcinbojko/linux_mint/pull/4)

## Version 1.4.0 2020-06-09

* [APPLICATION] upgraded `packer` to version 1.5.6
* [APPLICATION] upgraded `minikube` to version 1.11.0
* [APPLICATION] upgraded `rke` to version 1.1.2
* [APPLICATION] upgraded `docker-compose` to version 1.26.0
* [APPLICATION] upgraded `angryip` to version 3.7.2
* [APPLICATION] upgraded `hadolint` to version 1.18.0
* [APPLICATION] upgraded `etcher` to version 1.5.97
* [APPLICATION] upgraded `tflint` to version 0.16.2
* [APPLICATION] added `hashcat`
* [APPLICATION] added `polaris` [https://github.com/FairwindsOps/polaris](https://github.com/FairwindsOps/polaris)
* [APPLICATION] added `amass` [https://github.com/OWASP/Amass](https://github.com/OWASP/Amass)
* [APPLICATION] added `helm` with version 3. It will coexist with helm version 2, using name `helm3`
* [VSCODE] replaced depreciated extension `mauve.terraform` with `hashicorp.terraform`
* [VSCODE] replaced depreciated extension `ms-vscode.go` with `golang.go`
* download and unarchive is now handled by separate task: `/tasks/download_files.yml`. New section in mint19.yml variables list has been created: `unpack`. No longer is needed to check how many levels we do want to flatten extracted files.

## Version 1.3.9 2020-05-29

* [BREAKING_CHANGE] `mint19.yml` renamed to `mint19.yaml` to keep same naming convention
* linting and aligning with playbook and variables file.
* [APPLICATION] added `ffluf` [https://github.com/ffuf/ffuf](https://github.com/ffuf/ffuf)
* [APPLICATION] upgraded `etcher` to version 1.5.94
* [APPLICATION] upgraded `terminus alpha` to version 1.0.112
* [APPLICATION] upgraded `terraform` to version 0.12.26
* [APPLICATION] upgraded `tflint` to version 0.16.1
* [APPLICATION] upgraded `vault` to version 1.4.2
* [VSCODE] replaced depreciated extension `jpogran.puppet-vscode` in favor of `puppet.puppet-vscode`
* [PIP] added `jsonlint`
* [PIP] added `jmespath`

## Version 1.3.8 2020-05-20

* [BREAKING_CHANGE] changed `variables.yml` into `mint19.yml` to prepare for future releases
* [APPLICATION] added `dockle` - container image linter [https://github.com/goodwithtech/dockle](https://github.com/goodwithtech/dockle)
* [APPLICATION] upgraded `angryip` to version 3.7.1
* [APPLICATION] upgraded `etcher` to version 1.5.90
* [APPLICATION] upgraded `tflint` to version 0.16.0
* [APPLICATION] upgraded `terraform` to version 0.12.25

## Version 1.3.7 2020-05-13

* [APPLICATION] upgraded `wps-office` to 11.1.0.9505
* [APPLICATION] upgraded `k3s` to version 1.17.5
* [APPLICATION] upgraded `lens` to version 3.4.0
* [APPLICATION] upgraded `rke` to version 1.1.1
* [APPLICATION] upgraded `boostnote` to version 0.15.3
* [APPLICATION] upgraded `balena-etcher` to version 1.5.88
* [APPLICATION] upgraded `hadolint` to version 1.17.6p
* [APPLICATION] upgraded `tflint` to version 1.15.5
* [APPLICATION] upgraded `vagrant` to version 2.2.9
* [APPLICATION] upgraded `vault` to version 1.4.1
* [APPLICATION] upgraded `minikube` to version 1.10.1
* [APPLICATION] upgraded `terminus alpha` to version 1.0.111
* updated `README.md`
* added extra checks for active_user [https://github.com/marcinbojko/linux_mint/pull/1](https://github.com/marcinbojko/linux_mint/pull/1)

## Version 1.3.6 2020-04-14

* [APPLICATION] upgraded `docker-compose` to version 1.25.5
* [APPLICATION] upgraded `Lens` to version 3.2.0
* [APPLICATION] upgraded `minikube` to version 1.9.2
* [APPLICATION] upgraded `rke` to version 1.1.0
* [APPLICATION] upgraded `terminus alpha` to version 1.0.106
* [APPLICATION] upgraded `tflint` to version 0.15.4
* [APPLICATION] upgraded `vault` to version 1.4.0

## Version 1.3.5 2020-03-28

* [PACKAGES] added `goaccess` to optional packages
* [APPLICATION] upgraded `k3s` to version 1.17.4
* [APPLICATION] upgraded `minikube` to version 1.9.0
* [APPLICATION] upgraded `angryip` to 1.9.0
* [APPLICATION] upgraded `boostnote` to 0.15.2
* [APPLICATION] upgraded `balena-etcher` to version 1.5.80
* [APPLICATION] upgraded `packer` to version 1.5.5
* [APPLICATION] upgraded `terminus alpha` to version 1.0.105
* [APPLICATION] upgraded `terraform` to version 0.12.24
* [APPLICATION] upgraded `tflint` to version 0.15.3
* [APPLICATION] upgraded `rke` to version 1.0.5
* Added application `Lens` for K8S cluster management
* Added possibility to add *.desktop files for AppImage applications

## Version 1.3.4 2020-03-09

* [APPLICATION] upgraded `virtuabox` to version 6.1
* [APPLICATION] upgraded `tflint` to version 0.15.1
* [APPLICATION] upgraded `wps-office` to version 11.1.0.9216
* [APPLICATION] upgraded `boostnote` to version 0.15.0
* [APPLICATION] upgraded `vault` to version 1.3.3
* [APPLICATION] upgraded `terraform` to version 0.12.23
* [APPLICATION] upgraded `terminus alpha` to version 1.0.104
* [APPLICATION] added `balena-etcher` version 1.5.79 [https://www.balena.io/etcher/](https://www.balena.io/etcher/)
* [REPOSITORY] added `insync` Mint repoitory
* [KEYS] added 'insync` GPG key

## Version 1.3.3 2020-02-21

* [KEYS] removed section `keys+pgp`. All keys should be added as files now
* [APPLICATION] upgraded `dive` to version 0.9.2
* [APPLICATION] upgraded `docker-compose` to version 1.25.4
* [APPLICATION] upgraded `minikube` to version 1.7.3
* [APPLICATION] upgraded `terminus alpha` to version 1.0.103
* [APPLICATION] upgraded `packer` to version 1.5.4
* [APPLICATION] upgraded `terraform` to version 0.12.21

## Version 1.3.2 2020-02-02

* [APPLICATION] upgraded `k3s` to version 1.17.2
* [APPLICATION] upgraded `rke` to version 1.0.4
* [APPLICATION] upgraded `hadolint` to version 1.17.5
* [APPLICATION] upgraded `terminus alpha` to version 1.0.101
* [APPLICATION] upgraded `vagrant` to version 2.2.7
* [APPLICATION] upgraded `tflint` to version 1.14.0
* [ANSIBLE] added `callback_whitelist` to display tasks length
* [VSCODE] added `ext install medo64.render-crlf`
* [SYSCTL] added network tweaks
* [SYSCTL] added memory tweaks
* [PIP] added `ansible-lint`

## Version 1.3.1 2020-01-24

* [APPLICATION] upgraded `terminus alpha` to version 1.0.100
* [APPLICATION] upgraded `docker-compose` to version 1.25.3
* [APPLICATION] upgraded `rke` to version 1.0.2
* [APPLICATION] upgraded `terraform` to version 0.12.20
* [APPLICATION] upgraded `vault` to version 1.3.2
* [APPLICATION] upgraded `hadolint` to version 1.17.4
* [APPLICATION] added `teams` - Microsoft Teams Client for Linux

## Version 1.3.0 2020-01-14

* [APPLICATION] added `hadolint` in files section [https://github.com/hadolint/hadolint](https://github.com/hadolint/hadolint)
* [APPLICATION] upgraded `docker-compose` to version 1.25.1
* [APPLICATION] upgraded `terraform` to version 0.12.19
* [APPLICATION] upgraded `k3s` to version 1.17.0
* [APPLICATION] upgraded `tflint` to version 0.13.4
* [VSCODE] added `exiasr.hadolint`
* [APPLICATION] upgraded `wps-office` to version 11.1.0.9080
* added `keys_remove` section in variables
* switched instal_mitogen to false by default

## Version 1.2.9 2020-01-07

* [APPLICATION] upgraded `terminus alpha` to version 1.0.98
* Added support for Linux Mint 19.3 `Tricia`

## Version 1.2.8 2020-01-04 Birthday Edition

* [APPLICATION] changed link for WPS Office (same version)
* [APPLICATION] upgraded `k3s` to version 1.0.1
* [APPLICATION] upgraded `terraform` to version 0.12.8
* [APPLICATION] upgraded `docker-compose` to version 1.25.0
* [APPLICATION] upgraded `terminus` to version 1.0.97
* [APPLICATION] upgraded `minikube` to version 1.6.2
* [APPLICATION] upgraded `boostnote` to version 0.14.0
* [APPLICATION] upgraded `packer` to version 1.5.1
* [APPLICATION] upgraded `vault` to version 1.3.1
* [APPLICATION] upgraded `ctop` to version 0.7.3
* [APPLICATION] removal of helm3 package as it conflicts with helm2 - need to rethink it
* [PACKAGES] added `tlpui` for TLP graphical management
* [REPOSITORY] removal of `compholio` repository - obsoleted
* [REPOSITORY] removal of `forticlient` repository - bloated
* [REPOSITORY] `shutter` moved from optional to basic repos
* [REPOSITORY] added `linuxuprising/apps` to repos

## Version 1.2.7 2019-11-16

* [APPLICATION] upgraded dive to version 0.9.1
* [APPLICATION] upgraded `boostnote` to version 0.13.0
* [APPLICATION] upgraded `vault` to version 1.3.0
* [APPLICATION] upgraded `terraform` to version 0.12.15
* [APPLICATION] added Helm 3.0 as `helm3` in downloaded files
* deleted `enable_bbr` and `modify_grub` variables
* introduced `change_sysctl` variable,, defaults to true
* removed `modify grub` section, on kernel 5.0 it is useless
* new variables section `sysctl`
* moved `bbr congestion control` and `vm.swappiness` from standalone settings into `sysctl` section
* allowed 3-rd party deb applications to fail during install - due to possible internet connection problems when handling big files

## Version 1.2.6 2019-11-09

* [PACKAGES] added `multitail`
* [PACKAGES] added `shellcheck`
* [PACKAGES] added `dconf-cli`
* [PACKAGES] added `dconf-editor`
* [APPLICATION] upgraded `packer` to version 1.4.5
* [APPLICATION] upgraded `dive` to version 0.9.0
* [APPLICATION] upgraded `vault` to version 1.2.4
* [APPLICATION] added `brave-browser`
* [REPOSITORY] added `brave-browser`
* [VSCODE] added `timonwong.shellcheck` extension
* [DCONF] added `dconf` section in variables and playbook - settings related with dconf are now possible
* [PIP] added `psutil`
* [FLATPAK] added possibility to install flatpak files
* [FLATPAK] added `postman`
* [MITOGEN] upgraded `mitogen` to support ansible 2.9

## Version 1.2.5 2019-11-02

* [APPLICATION] upgraded `rke` to version 0.3.2
* [APPLICATION] upgraded `terraform` to version 0.12.13
* [APPLICATION] removed `franz` - for its bloatware/adaware policy and paid service
* [APPLICATION] added `Rambox-OS - Hamsket` [https://github.com/TheGoddessInari/hamsket/releases/download/0.5.20/Rambox_0.5.20_amd64.deb](https://github.com/TheGoddessInari/hamsket/releases/download/0.5.20/Rambox_0.5.20_amd64.deb)
* [APPLICATION] upgraded `minikube` to version `1.5.2`
* [APPLICATION] added `k3s` to downoaded as files
* [PACKAGES] added `ioping` to packages
* [PACKAGES] added `dstat` to packages
* [PACKAGES] added `rclone` to packages

## Version 1.2.4 2019-10-16

* fixed mitogen strategy path for ansible
* update `README.md`

## Version 1.2.3 2019-10-16

* increased requirements for free space on / to 15 GB
* added section `ansible` - changes in ansible config.
* [APPLICATION] upgraded `angryip` to version 3.6.2
* [APPLICATION] upgraded `terminus alfa` to version 1.0.92
* [APPLICATION] upgraded `terraform` to version 0.12.10
* [APPLICATION] removed `rancher` as obsolete package
* [APPLICATION] upgraded `tflint` to version 0.12.1
* [APPLICATION] upgraded `vagrant` to version 2.2.6
* [PACKAGES] added `dos2unix`
* [PACKAGES] added `python3-gpg`
* [GLOBAL_ENV] changed default editor to `mcedit`
* [VARIABLE] added `config_ansible` boolean type. When set to true [default] changes ansible options
* [VSCODE] added `vscode` extensions:
  * gep13.chocolatey-vscode
  * ms-vsliveshare.vsliveshare
  * ms-azuretools.vscode-azureterraform
* bumped to ansible 2.8 as minimum version (mitogen)

## Version 1.2.2 2019-09-28

* [APPLICATION] upgraded `ipscan` to version 3.6.1
* [APPLICATION] upgraded `terminus alfa` to version 1.0.90
* [APPLICATION] upgraded `dive` to version 0.8.1
* [APPLICATION] upgraded `terraform` to version 0.12.9
* [APPLICATION] upgraded `tflint` to version 0.11.2
* [APPLICATION] added `packetsender` in version 6.2.3 [https://packetsender.com/](https://packetsender.com/)
* [APPLICATION] upgraded `minikube` to version 1.4.0
* [APPLICATION] added `whois`
* [APPLICATION] upgraded `wps Office` to version 11.1.0.8865
* [APPLICATION] upgraded `franz` to version 5.3.3

## Version 1.2.1 2019-08-24

* [APPLICATION] upgraded `terminus` to version 1.0.88
* [APPLICATION] upgraded `packer` to version 1.4.3
* [APPLICATION] upgraded `vault` to version 1.2.2
* [APPLICATION] upgraded `minikube` to version 1.3.1
* [REPOSITORY] removed `knqyf263/trivy` repository in favor of `auqasecurity/trivy`
* [APPLICATION] upgraded `rke` to version 0.2.8
* [APPLICATION] added `tflint` 0.10.1
* [APPLICATION] upgraded `terraform` to version 0.12.7

## Version 1.2.0 2019-08-12

* tested with Linux Mint Tina 19.2
* [APPLICATION] upgraded `minikube` to version 1.3.0
* [APPLICATION] upgraded `rke` to version 0.2.7
* [APPLICATION] upgraded `helm` to version 2.14.3
* [APPLICATION] upgraded `angryip` to version 3.6.0
* [APPLICATION] upgraded `terraform` to version 0.12.6
* [APPLICATION] upgraded `vault` to version 1.2.1
* [APPLICATION] upgraded `franz` to version 5.2.0
* [PACKAGES] removed `nero-dropbox` from list of packages as it stops apt actions waiting for dropbox download
* [KEYS] added Spotify repository key `4773BD5E130D1D45`
* [VSCODE] added vs-code extensions:
  * ms-python.python
  * ms-vscode.azure-account
  * ms-vscode.azurecli
  * ms-vscode.cpptools
  * ms-vscode.Go
  * ms-vscode.wordcount

## Version 1.1.9 2019-07-26

```txt
 _____             ___      _           _       _      ______
/  ___|           / _ \    | |         (_)     ( )     |  _  \
\ `--. _   _ ___ / /_\ \ __| |_ __ ___  _ _ __ |/ ___  | | | |__ _ _   _
 `--. \ | | / __||  _  |/ _` | '_ ` _ \| | '_ \  / __| | | | / _` | | | |
/\__/ / |_| \__ \| | | | (_| | | | | | | | | | | \__ \ | |/ / (_| | |_| |
\____/ \__, |___/\_| |_/\__,_|_| |_| |_|_|_| |_| |___/ |___/ \__,_|\__, |
        __/ |                                                       __/ |
       |___/                                                       |___/
 _____  _____  __   _____
/ __  \|  _  |/  | |  _  |
`' / /'| |/' |`| | | |_| |
  / /  |  /| | | | \____ |
./ /___\ |_/ /_| |_.___/ /
\_____/ \___/ \___/\____/
```

* [REPOSITORY] added `trivy` repository and key [https://github.com/knqyf263/trivy#debianubuntu](https://github.com/knqyf263/trivy#debianubuntu)
* [APPLICATION] upgraded `WPS Office for Linux` to version 11.1.0.8722
* [APPLICATION] upgraded `helm` to version 2.14.2
* [APPLICATION] upgraded `terraform` to version 0.12.5
* [GLOBAL_ENV] added section in variables.yml for adding global environments in /etc/environment
* [APPLICATION] upgraded `rke` to version 0.2.6
* [APPLICATION] upgraded `boostnote` to version 0.12.1-1
* [APPLICATION] upgraded `terminus alpha` to version 1.0.87
* [APPLICATION] upgraded `vault` to version 1.1.4
* [PACKAGES] added `sshfs`

## Version 1.1.8 2019-07-01

* [APPLICATION] upgrade `trivy` to version 0.1.3
* [APPLICATION] upgrade `minikube` to version 1.2.0
* [APPLICATION] upgrade `docker-compose` to version 1.24.1
* [APPLICATION] upgrade `terraform` to version 0.12.3
* [APPLICATION] upgrade `vagrant` to version 2.2.5
* [APPLICATION] upgrade `packer` to version 1.4.2

## Version 1.1.7 2019-06-23

* [APPLICATION] upgrade `minikube` to version 1.1.1
* [APPLICATION] upgrade `boostnote` to version 0.11.17
* [APPLICATION] upgrade `terminus alpha` to version 1.0.82
* [APPLICATION] upgrade `terraform` to version 0.12.2
* [APPLICATION] upgrade `vault` to version 1.1.3
* [PIP] added `yamllint`
* [PACKAGES] added `httpie`
* [PACKAGES] added `ngrep`
* [PACKAGES] added `hping3`
* [PACKAGES] added `siege`
* [PACKAGES] switch `openjdk-8-jre` to `openjdk-11-jre`
* [VSCODE] change name of `PeterJausovec.vscode-docker` exyension into `ms-azuretools.vscode-docker`
* [VSCODE] added `p1c2u.docker-compose` extension

## Version 1.1.6 2019-06-06

* [APPLICATION] upgraded `terminus alpha` to version 1.0.79
* [APPLICATION] upgrade `rke` to version 0.2.4
* [APPLICATION] upgrade `helm` to version 2.4.1
* [APPLICATION] upgrade `terraform` to version 0.12.1
* [APPLICATION] added `trivy` to optional applications [https://github.com/knqyf263/trivy/releases/download/v0.1.2/trivy_0.1.2_Linux-64bit.deb](https://github.com/knqyf263/trivy/releases/download/v0.1.2/trivy_0.1.2_Linux-64bit.deb)
* change apt upgrade parameter from `yes` to `"yes"` - [https://github.com/ansible/ansible/issues/56788](https://github.com/ansible/ansible/issues/56788)
* [OS] added possibility to change alternatives using `variables.yml`

## Version 1.1.5 2019-05-25

* [APPLICATION] upgraded `boostnote` to version 0.11.6
* [APPLICATION] upgraded `terraform` to version 0.12  - please read terraform's releases notes
* [APPLICATION] upgraded `minikube` to version 1.1.0

## Version 1.1.4 2019-05-18

* [APPLICATION] upgraded `terminus alpha` to version 1.0.77
* change `fstrim.timer` to run on hourly basis instead of daily
* [APPLICATION] upgraded `packer` to version 1.4.1
* [APPLICATION] upgraded `helm` to version 2.14.0
* [APPLICATION] upgraded `terraform` to version 0.11.14
* [APPLICATION] upgraded `vault` to version 1.1.2
* [APPLICATION] upgraded `franz` to version 5.1.0

## Version 1.1.3 2019-04-30

* [APPLICATION] upgraded `terminus alpha` to version 1.0.76
* [APPLICATION] upgraded `WPS office` to version 11.1.0.8392
* [APPLICATION] upgraded `Franz` to version 5.0.1
* [APPLICATION] upgraded `minikube` to version 1.0.1
* [APPLICATION] downgrade `rke` to version 0.1.18 as 0.2.x branch is too unstable
* [APPLICATION] upgraded `docker-compose` to version 1.24.0
* [APPLICATION] upgrade `vault` to version 1.1.1
* [APPLICATION] added `dive` to applications - [https://github.com/wagoodman/dive](https://github.com/wagoodman/dive)

## Version 1.1.2 2019-03-27

* [APPLICATION] upgraded `terraform` to version 0.11.13
* [APPLICATION] upgraded `WPS Ofice` to version 10.1.0.6758
* [APPLICATION] upgraded `helm` to version 2.13.1
* [APPLICATION] upgraded `vault` to version 1.1.0
* [APPLICATION] upgraded `rancher` to version 2.2.0
* [APPLICATION] upgraded `rke` to version 0.2.0
* [APPLICATION] upgraded `minikube` to version 1.0.0

## Version 1.1.1 2019-03-12

* [APPLICATION] upgraded `terminus alpha` to version 1.0.73

## Version 1.1.0 2019-03-11

* [REPOSITORY] **Warning** - after switching to 1.0.7 for `veeam-release-deb` filename for repository changes to `veeam.lst` instead `veeam-agent.lst`. To avoid duplicates remove this file `veeam-agent.lst` manually before running playbook.
* [APPLICATION] upgraded `packer` to version 1.3.5
* [APPLICATION] upgraded `helm` to version 2.13
* [APPLICATION] upgraded `vagrant` to version 2.2.4
* [APPLICATION] upgraded `terminus alpha` to version 1.0.72
* [APPLICATION] upgrade `terraform` to version 0.11.12
* [APPLICATION] upgrade `minikube` to version 0.35.0
* [APPLICATION] added `isomaster` to optional packages

## Version 1.0.9 2019-02-25

* [APPLICATION] upgraded `minikube` to version 0.34
* [APPLICATION] upgraded `ipscan` to version 3.5.5
* [APPLICATION] upgrade `Franz` to version 5.0.0. **Warning** - remove Franz beta version before proceeding
* [APPLICATION] upgrade `rancher` to version 2.2.0-rc9
* [APPLICATION] upgrade `ctop` to version 0.7.2
* [APPLICATION] upgrade `rke` to version 0.1.16
* [REPOSITORY] removed `ppa:alexx2000/doublecmd` repository as obsolete
* [REPOSITORY] added `http://download.opensuse.org/repositories/home:/Alexx2000/xUbuntu_18.04/` repository for doublecmd
* added section `repositories_remove` in variables.yml which contains repositories we'd like to remove.
* added option `skip_levels` for unarchive module, which is substituted into `--strip-components=`
* added variable `enable_bbr`, by default set to true. If true, enables TCP BBR congestion control
* [OS] added section to enable TCP BBR congestion control
* [OS] added section to change vm_swappiness to 1
* [OS] changed the way fstrim.timer service works
* [OS] replace ntpd with systemctl-timezoned.

## Version 1.0.8 2019-02-14

* [APPLICATION] upgraded `Boostnote` to version 0.11.15
* [APPLICATION] upgraded `Terminus Alfa` to version 1.0.71
* [APPLICATION] upgraded `packer` to version 1.3.4
* [APPLICATION] upgraded `vault` to version 1.0.3
* [APPLICATION] added 'rancher-cli` in version 2.2.0-rc6
* [APPLICATION] changed `virtualbox 5.2` to `virtualbox-6`
* [BROKEN] added mitogen optional installation `install_mitogen=true` in variables. Not included in this release.
* [PACKAGES] `iotop` added instead of `itop`
* [PACKAGES] added `nfs-client`
* [PACKAGES] added `spotify-client`
* [PACKAGES] added `powertop`
* [PACKAGES] added `gddrescue`
* [PACKAGES] added `testdisk`
* [PACKAGES] added `partclone`
* [PACKAGES] added `rdesktop`
* [PACKAGES] removed `cairo-dock` as not active anymore. Replaced with DockbarX
* [PACKAGES] added `dockbarx` as default dock in the system
* [PACKAGES] upgraded `dotnet-runtime` to version 2.2
* [PACKAGES] upgraded `dotnet-sdk` to version 2.2

## Version 1.0.7 2019-01-23

* [APPLICATION] upgrade `helm` to version 2.12.3
* [APPLICATION] upgrade `minikube` version to 0.33.1
* [APPLICATION] upgrade `vault` to version 1.0.2
* [APPLICATION] upgrade `docker-compose` to version 1.23.2
* [APPLICATION] added `rke` Rancher Kubernetes Engine in version 0.1.15

## Version 1.0.6 2019-01-15

* fixed copying autostart files . Now it doesn't override these already existing
* fixed inproper dist name in forticlient repository
* [APPLICATION] - added `ctop` as application available in `bin_path`
* [REPOSITORY] - added `gcsfuse` repository [https://github.com/GoogleCloudPlatform/gcsfuse](https://github.com/GoogleCloudPlatform/gcsfuse)
* [PACKAGES] - upgrade `vagrant` to version 2.2.3
* verification of existence of `bin_path` added

## Version 1.0.5 - 2018-12-23 Christmas Edition

```txt
             *
           _/ \_
          \     /
          /_' '_\
           /  @\
          /@  . \
         / -'   .\
        /+      . \
       /--@ @.o .o \
      / '''. +@.o+ @\
     /.'+ - *o-  *-- \
    /. @.   o**  . -  \
    *------------------*
         [_______]
          \_____/
```

* [REPOSITORY] - added `ppa:mozillateam/ppa`
* [APPLICATION] - upgrade `Franz` to version 5.0.0-beta22
* [APPLICATION] - upgrade `minikube` to version 0.32.0
* [APPLICATION] - upgrade `helm` to version 2.12.1
* [KEYS] - added key to `Forticlient` repository
* [REPOSITORY] - added `Forticlient` repository
* [VARIABLE] - added variable `modify_grub` defaults to (false) - modify grub settings or not
* General cleaning
  * removing spaces from task names
  * adding rest of missing tags
* Tested with `Linux Mint 19.1 Tessa`

## Version 1.0.4 - 2018-12-18

* [PACKAGES] added `traceroute`
* [APPLICATION] upgraded `terraform` to versiob 0.11.11
* [APPLICATION] `vault` upgraded to 1.0.1
* [APPLICATION] upgrade  `Boostnote` to version 0.11.12

## Version 1.0.3 - 2018-12-10

* [APPLICATION] upgrade  `Boostnote` to version 0.11.11
* [KEYS] update `Pale Moon` repository key to 18.04
* [APPLICATION] upgrade `packer` to version 1.3.3

## Version 1.0.2 - 2018-12-04

* [APPLICATION] upgraded `Vault` to version 1.0.0
* [VSCODE] added section to install required vscode extensions
* [PACKAGES] added `iperf3`
* [VARIABLE] added `install_vscode_extensions`, defaults to `true`

## Version 1.0.1 - 2018-11-29

* [PACKAGES] added `zenmap`
* [PACKAGES] addedd missing `redshift-gtk`
* [APPLICATION] upgraded `Vagrant` to 2.2.2
* [APPLICATION] upgraded `Terminus Alpha` to version 1.0.1
* [APPLICATION] experimental support for minikube's deb package instead of file
* [REPOSITORY] add `puppet5` repository manually instead of package
* [KEYS] removed redundand key for packages.microsoft.com
* added more memberships in groups
* switch to copy desktop files instead of presenting content in `variables.yml`
* Fixes in README.md

## Version 1.0.0 - 2018-11-22

* First public appearance
* [REPOSITORY] added `Google Cloud SDK` repository
* [APPLICATION] added `google-cloud-sdk`
* [APPLICATION] added `awscli`

## Version 0.8.5 - 2018-11-21

* [APPLICATION] added `Team Viewer` to external applications
* [APPLICATION] added `WPS Office` to external applications
* added packages:
  * network-manager-fortisslvpn
  * openfortivpn
  * network-manager-vpnc
  * network-manager-openconnect

## Version 0.8.4 - 2018-11-21

* [APPLICATION] added `Veracrypt` repository and package (optional)
* [APPLICATION] added `git-lfs` repository and package
* [APPLICATION] upgraded `Terminus Alpha` to `1.0.0-alpha-63`
* changed `fstrim.timer` to run daily instead of weekly

## Version 0.8.3 - 2018-11-18

* [PACKAGES] added `ntp` as first step to make sure time and date are set properly
* [APPLICATION] upgraded `Vagrant` to 2.2.1
* [APPLICATION] upgraded `Vault` to 0.11.5
* [APPLICATION] added `WoeUSB` 3.2.10
* [PIP] Added `pypsrp`

## Version 0.8.2 - 2018-11-13

* adding `active_user` to visudo

## Version 0.8.1 - 2018-11-13

* [APPLICATION] added Boostnote
* [APPLICATION] added Terminus Alpha
* [APPLICATION] added Franz
* [OS] module for changing avahi config for `.local` domains
* [OS] module for changing `nsswitch.conf` mDNS settings
* [OS] added `elevator=deadline` to grub default for SSD drives

## Version 0.8.0 - 2018-11-12

* inital Version
