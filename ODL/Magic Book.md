# Tips Linux
## Install ArchLinux
### Fresh Install
* Check the Secure boot disabled
- Verify the boot mode:
    ```bash
    > ls /sys/firmware/efi/efivars  
    ```
- check the name of volume:
    ```bash
    > lsblk -f
    ```
- partition drive with physical volume for boot and the rest
    ```bash
    > gdisk /dev/sda
    ```
    `n` for new partition then `p` to print and `w` to write
- Create boot directory:
    ```bash
    > mkdir /mnt/boot
    ```
- Mount boot partition:
    ```bash
    > mount /dev/sda1 /mnt/boot
    ```
- Create physical volume ssd:
    ```bash
    > vgcreate ssd /dev/sda2
    ```
- create logical volume: root, home, data, env, spare, swap on ssd:
    ```bash
    > lvcreate -L50G ssd -n home
    > lvcreate -L15G ssd -n spare
    > lvcreate -L20G ssd -n swap
    > lvcreate -L10G ssd -n root
    > lvcreate -L10G ssd -n root
    > lvcreate -L15G ssd -n env
    > lvcreate -l+100%FREE ssd -n data
    ```
    > lvcreate -L15G ssd -n spare
- If necessary resize: ex:
    ```bash
    > lvresize -L +10G ssd/spare
    ```
- check that all logical volume are there:
    ```bash
    > lvs
    ```
- Format drive:
    ```bash
    > mkfs.ext4 /dev/mapper/ssd-root
    > mount /dev/mapper/ssd-root /mnt
    > mkswap /dev/mapper/ssd-swap
    > mkfs.ext4 -T news /dev/mapper/ssd-data
    > mount /dev/mapper/ssd-root /mnt/data
    >  mkfs.ext4 /dev/mapper/ssd-home
    >  tune2fs -m0 /dev/mapper/ssd-home
    > mkfs.ext4 /dev/mapper/ssd-env
    ```
- Ensure the system clock is accurate:
    ```bash
    > timedatectl set-ntp true
    ```
- Install the base package, Linux kernel and firmware for common hardware:
    ```bash
    > pacstrap /mnt base linux linux-firmware
    ```
- Generate an `fstab` file (use `-U` to define by UUID):
    ```bash
    > genfstab -U /mnt >> /mnt/etc/fstab
    ```
- Change root into the new system:
    ```bash
    > arch-chroot /mnt
    ```
- Set the time zone:
    ```bash
    > ln -sf /usr/share/zoneinfo/Europe/Paris /etc/localtime
    ```
- generate `/etc/adjtime`:
    ```bash
    > hwclock
    ```
- Generate the locales by running:
    ```bash
    > locale-gen
    ```
- Create the `/etc/locale.conf` file, and set the `LANG` variable accordingly: `LANG=en_US.UTF-8`
- If you set the keyboard layout, make the changes persistent in `/etc/vconsole.conf`: `KEYMAP=de-latin1`
- Create the `/etc/hostname` file: `myhostname`
- Add matching entries to /etc/hosts:
    ```bash
    127.0.0.1	localhost
    ::1		localhost
    127.0.1.1	myhostname.localdomain	myhostname
    ```

### System package
    
    - [ ] xorg-server
    - [ ] i3 dmenu
    - [ ] redshift
    - [ ] mesa
    - [ ] xorg-xinit
    - [ ] xorg-app
    - [ ] vi vim
    - [ ] ttf-dejavu gsfonts ttf-liberation
    - [ ] xterm
    - [ ] tmux

### Other package in pacman

```jsx
 pacman -S ...
```

- [ ] git
- [ ] iwd (wifi)
- [ ] zsh
- [ ] xorgs-fonts-type1 xorg-font-util (anchor)
- [ ] ohmyzsh
- [ ] binutils (makepkg)
- [ ] gcc
- [ ] make
- [ ] dunst
- [ ] ffmpeg
- [ ] openvpn
- [ ] bluez (bluetooth)
- [ ] bluez-utils
- [ ] autorandr
- [ ] rsync
- [ ] xf86-input-synaptics (touchpad)
- [ ] dialog
- [ ] wpa_supplicant
- [ ] nfs-utils (to mount /deolen/data)
- [ ] cifs-utlis (to mount /deolen/share)
- [ ] fuse3 (to mount apfs)
- [ ] meld
- [ ] lftp
- [ ] wget
- [ ] netcdf
- [ ] qiv
- [ ] base-devel
- [ ] xinput-calibrator
- [ ] libnotify (for notification
- [ ] gdal

### Packages in aur

Package from aur can be install using the following procedure

```bash
> git clone <https://aur.archlinux.org/[package].git>
> cd [package]
> makepkg
> sudo pacman -U [package].tar.zst
```

#### Tools netcdf

```bash
> sudo pacman -S netpbm
> git clone <https://aur.archlinux.org/udunits.git>
> cd udunits && makepkg && pacman -U
> git clone <https://aur.archlinux.org/antlr2.git>
> cd antlr2 && makepkg && pacman -U
```

- ncview
    
    ```bash
    > export cc=CC
    > git clone <https://aur.archlinux.org/ncview.git>
    ```
    
- nco
    
    ```bash
    > sudo pacman -S gsl
    > git clone <https://aur.archlinux.org/nco.git>
    ```
    

#### DaVinci resolve (movies)

```bash
> git clone <https://aur.archlinux.org/davinci-resolve.git> 
```

#### 1password

```bash
> git clone <https://aur.archlinux.org/1password.git>
```

#### Mount

- APFS
    
    ```bash
    > sudo pacman -S fuse3
    > git clone <https://aur.archlinux.org/apfs-fuse-git.git>
    ```
    
- Podaac
    
    ```bash
    > git clone <https://aur.archlinux.org/davfs2.git>
    ```
    
    - IFREMER
    
    ```bash
     > git clone <https://aur.archlinux.org/pulse-secure.git>  
     (or get package from NAS)
    ```
    

#### Communication

- Slack
    
    ```bash
    >  git clone <https://aur.archlinux.org/slack-desktop.git>
    ```
    
- Discord
    
    ```bash
    > git clone <https://aur.archlinux.org/discord-canary.git>
    ```
    

#### Sublime
```bash
> git clone https://aur.archlinux.org/sublime-text-4.git
```
## Mounting device

```bash
sudo apfs-fuse -o uid=1000,gid=1000,allow_other /dev/sdf2 /tmp/key
```


## Synchronize

```bash
rsync -rlptD --progress ./geomatics /deolen/data/events/2025_otc/lehmkhul_backup/
```
## External Access
```
# sudo iptables -t nat -vnL
sudo iptables -A INPUT -p tcp --dport 9876 -j ACCEPT
sudo iptables -A TCP -s 192.168.177.0/24 -p tcp -m tcp --dport 9876 -j ACCEPT
sudo iptables -A TCP -s 192.34.177.0/24 -p tcp -m tcp --dport 9876 -j ACCEPT
```
# Tips MacOS
## Install Brew
```bash
> /bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```
```bash
brew install XQuartz 
brew install tmux 
brew install python@3.13 
brew install netcdf # (for ncdump) 
brew install ncview 
brew install openjpeg # (for sentinel2) 
brew install pandoc # (to convert markdown) 
brew install cmake openmpi 
brew install tigervnc-viewer # (to connect to CNES in view mode) 
brew install npm # (for syntool server)
```
## Rebuild Spotlight index
```bash
# Turn Spotlight off
sudo mdutil -a -i off
# Turn Spotlight on
sudo mdutil -a -i on
# Erase the Spotlight index for all volumes, forcing spotlight to rebuild index from scratch
sudo mdutil -E
```

## Backup
### Git and Obsidian
```
 ~/Library/Mobile Documents/iCloud~md~obsidian/Documents/Obsidian
```
## Shortcuts
### Cut / Copy / Paste
## Cut, copy, paste, and other common shortcuts

- **Command-X**: Cut the selected item and copy it to the Clipboard.
- **Command-C**: Copy the selected item to the Clipboard. This also works for files in the Finder.
- **Command-V**: Paste the contents of the Clipboard into the current document or app. This also works for files in the Finder.
- **Command-Z**: Undo the previous command. You can then press Shift-Command-Z to Redo, reversing the undo command. In some apps, you can undo and redo multiple commands.
- **Command-A**: Select All items.
- **Command-F**: Find items in a document or open a Find window.
- **Command-G**: Find Again: Find the next occurrence of the item previously found. To find the previous occurrence, press Shift-Command-G.
- **Command-H**: Hide the windows of the front app. To view the front app but hide all other apps, press Option-Command-H.
- **Command-M**: Minimize the front window to the Dock. To minimize all windows of the front app, press Option-Command-M.
- **Command-O:** Open the selected item, or open a dialog to select a file to open.
- **Command-P**: Print the current document.
- **Command-S**: Save the current document.
- **Command-T**: Open a new tab.
- **Command-W**: Close the front window. To close all windows of the app, press Option-Command-W.
- **Option-Command-Esc**: [Force quit](https://support.apple.com/HT201276) an app.
- **Command–Space bar**: Show or hide the [Spotlight](https://support.apple.com/guide/mac-help/mchlp1008/mac) search field. To perform a Spotlight search from a Finder window, press Command–Option–Space bar. (If you [use multiple input sources](https://support.apple.com/guide/mac-help/type-language-mac-input-sources-mchlp1406/mac) to type in different languages, these shortcuts change input sources instead of showing Spotlight. Learn how to [change a conflicting keyboard shortcut](https://support.apple.com/guide/mac-help/mchlp2864/mac).)
- **Control–Command–Space bar**: Show the Character Viewer, from which you can choose [emoji and other symbols](https://support.apple.com/guide/mac-help/mchlp1560/mac).
- **Control-Command-F**: Use the app in full screen, if supported by the app.
- **Space bar**: Use [Quick Look](https://support.apple.com/guide/mac-help/view-and-edit-files-with-quick-look-mh14119/mac) to preview the selected item.
- **Command-Tab**: Switch to the next most recently used app among your open apps.
- **Command–Grave accent (`):** Switch between the windows of the app you're using. (The character on the second key varies by keyboard. It's generally the key above the Tab key and to the left of the number 1.)
- **Shift-Command-5**: In [macOS Mojave or later](https://support.apple.com/kb/HT201260), take a screenshot or make a screen recording. Or use Shift-Command-3 or Shift-Command-4 for screenshots. [Learn more about screenshots](https://support.apple.com/kb/HT201361).
- **Shift-Command-N:** Create a new folder in the Finder.
- **Command-Comma (,)**: Open preferences for the front app.

### 1password

### Figma

n      
# Tips Datarmor
## Create Jupyter Environment
```bash
module load anaconda 
conda create -n skim_plot python=3.9 
conda activate skim_plot 
conda install matplotlib cartopy ... 
# check that condo-env path is in .condarc 
conda install ipykernel 
source deactivate
```

# Install WIndows

## EK80

## Conda

## NetCDF tools

# ODL

## Caldav

* Username: prénom.nom  
* Location: [https://agenda.oceandatalab.com/odl/indisponibility](https://agenda.oceandatalab.com/odl/indisponibility)
* Location: [https://agenda.oceandatalab.com/odl/meetings](https://agenda.oceandatalab.com/odl/meetings)
* Location: [https://agenda.oceandatalab.com/odl/conges](https://agenda.oceandatalab.com/odl/conges)
* Location: [https://agenda.oceandatalab.com/odl/télétravail](https://agenda.oceandatalab.com/odl/télétravail)
* Location: [https://agenda.oceandatalab.com/odl/maintenance](https://agenda.oceandatalab.com/odl/maintenance)
* Offline Support : à décocher  
* Find Calendars  
* Entrer votre mot de passe pour l'agenda
* Calendar type: CalDAV  
* Subscribe

## Mail

### lg_wont_read
* imap: ex3.mail.ovh.net


### lucile.gaultier
* imap: ssl0.ovh.net
