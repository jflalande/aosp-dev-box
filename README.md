# AOSP Development Box

Vagrant to build and develop Android AOSP.

JFL: Adapted for building SONY XPeria open devices.

## Set Up

Install Vagrant and VirtualBox.

### OSX

Install with Homebrew or manually.

```
brew update
brew cask install virtualbox
brew cask install virtualbox-extension-pack
brew cask install vagrant
```

## Vagrant Usage

To build the VM do

```
vagrant up
```

Use the VM GUI or ssh in with

```
vagrant ssh
```

See the [Vagrant Command-Line Interface docs](https://www.vagrantup.com/docs/cli) for more information.

## VirtualBox Guest Additions

Guest Additions are needed to have a good experience using the VM GUI. There are multiple ways to install Guest Additions.

### Vagrant Plugin

If you use the [Vagrant plugin](https://github.com/dotless-de/vagrant-vbguest) then Guest Additions will be installed and updated automatically, even when you upgrade VirtualBox.

```
vagrant plugin install vagrant-vbguest
```

This is the preferred approach but isn't currently working with VirtualBox 5.2.0 and the bento/ubuntu-16.04 base box we are using. See the [VirtualBox download page](https://www.virtualbox.org/wiki/Downloads) for any Guest Additions updates.

### Scripted During Provisioning

If you copy VBoxGuestAdditions.iso from your VirtualBox installation into shared/VBoxGuestAdditions.iso then it will be installed automatically during provisioning.

```bash
cp /Applications/VirtualBox.app/Contents/MacOS/VBoxGuestAdditions.iso shared/
# or
wget https://www.virtualbox.org/download/testcase/VBoxGuestAdditions_5.2.1-118918.iso -O share/VBoxGuestAdditions.iso
```

### Manually

In your VM menu choose Devices -> Insert Guest Additions CD image

## Tools

### Android NDK

The [Android NDK](https://developer.android.com/ndk/index.html) contains all the tools needs to build the Android Linux kernel and native code. It is installed in /opt/android/ndk.
