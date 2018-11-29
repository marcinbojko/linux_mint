# Changelog "linux_mint"

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
