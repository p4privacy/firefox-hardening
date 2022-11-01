# <img src="https://user-images.githubusercontent.com/114076168/199189876-ff5f49f8-975d-43fd-b040-9bee0b25f323.png" width="33" height="35"> Firefox Hardening Guide [![Hits](https://hits.seeyoufarm.com/api/count/incr/badge.svg?url=https%3A%2F%2Fgithub.com%2Fp4privacy%2Ffirefox-hardening&count_bg=%230000ff&title_bg=%23555555&icon=&icon_color=%23E7E7E7&title=hits&edge_flat=false)](https://hits.seeyoufarm.com)

This guide is about how to install Firefox on Linux via APT package manager and harden it to make your browsing as safe as possible

## Menu

* [Install Firefox via APT as DEB package](#install-firefox-via-apt-as-deb-package)
    - [Remove Firefox from Snap](#remove-firefox-from-snap)
    - [Add Mozilla Team Repository](#add-mozilla-team-repository)
    - [Set the deb version as preferred](#set-the-deb-version-as-preferred)
    - [Set automatic Updates](#set-automatic-updates)
    - [Install the package via apt](#install-the-package-via-apt)
* [User Configuration File](#user-configuration-file)
    - [Download Link](#download-link)
    - [Extract the files](#extract-the-files)
* [Recommended Extensions](#recommended-extensions)

## Install Firefox via APT as DEB package

### Remove Firefox from Snap

On your computer open a terminal and type:
```bash
sudo snap remove firefox
```

### Add Mozilla Team Repository

Run the following command in the same Terminal window:
```bash
sudo add-apt-repository ppa:mozillateam/ppa
```

## Set the deb version as preferred

We will alter the Firefox package priority to ensure the PPA/deb/apt version of Firefox is preferred
```bash
echo '
Package: *
Pin: release o=LP-PPA-mozillateam
Pin-Priority: 1001
' | sudo tee /etc/apt/preferences.d/mozilla-firefox
```

## Set automatic Updates

To have future Firefox upgrades to be installed automatically type:
```bash
echo 'Unattended-Upgrade::Allowed-Origins:: "LP-PPA-mozillateam:${distro_codename}";' | sudo tee /etc/apt/apt.conf.d/51unattended-upgrades-firefox
```

## Install the package via apt
```bash
sudo apt install firefox
```

## User Configuration File

### Download Link

The file user.js-xxx.zip can be downloaded from this repository: [https://github.com/arkenfox/user.js](https://github.com/arkenfox/user.js)

### Extract the files

In your Firefox browser tab type:
```bash
about:profiles
```

Copy the profile root directory you want to add the user.js file into
```bash
Example: /home/user/.mozilla/firefox/abcded.profile-name
```

Extract the files from the .zip file:
```bash
unzip -q user.js-xxx.zip
```

Go into the extracted folder:
```bash
cd user.js-xxx/
```
Copy the content of the folder into the profile root directory
```bash
cp *.* /home/user/.mozilla/firefox/abcded.profile-name
```
Now, if you re-open your browser and everything has gone fine, you should see something like a windows opened in a window, this is because the resolution has been spoofed and the reason is to prevent canvas fingerprinter.


## Recommended Extensions

- <img src="https://user-images.githubusercontent.com/114076168/199192811-6b6bed17-2af7-49ea-9cad-0e49dfafeaae.png" width="20" height="20"> uBlock Origin: [link](https://addons.mozilla.org/en-US/firefox/addon/ublock-origin/?utm_source=addons.mozilla.org&utm_medium=referral&utm_content=search)
- <img src="https://user-images.githubusercontent.com/114076168/199192844-f0a42bbd-8d9a-47fc-9f8f-8cc0cc111db4.png" width="20" height="20"> BitWarden Password Manager: [link](https://addons.mozilla.org/en-US/firefox/addon/bitwarden-password-manager/)
- <img src="https://user-images.githubusercontent.com/114076168/199192916-00b00905-273c-4d4c-bfa6-e20bd38929fc.png" width="20" height="20"> Skip Redirect: [link](https://addons.mozilla.org/en-US/firefox/addon/skip-redirect/?utm_source=addons.mozilla.org&utm_medium=referral&utm_content=search)
- <img src="https://user-images.githubusercontent.com/114076168/199192958-a7f47ee3-96e0-48ca-b18a-1cbe52f0e1cb.png" width="20" height="20"> LocalCDN: [link](https://addons.mozilla.org/en-US/firefox/addon/localcdn-fork-of-decentraleyes/?utm_source=addons.mozilla.org&utm_medium=referral&utm_content=search)
- <img src="https://user-images.githubusercontent.com/114076168/199193068-5af38361-5d44-496e-94a2-3c88603c54f1.png" width="20" height="20"> Firefox Multi-Account Container: [link](https://addons.mozilla.org/en-US/firefox/addon/localcdn-fork-of-decentraleyes/?utm_source=addons.mozilla.org&utm_medium=referral&utm_content=search)
