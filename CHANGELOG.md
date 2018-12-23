# Changelog "linux_mint

## Version 1.0.5 - 2018-12-23 Christmas Edition

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
