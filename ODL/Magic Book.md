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

# Install WIndows

## EK80

## Conda

## NetCDF tools

##screeshots / video recording
Windows+ shift + S
# ODL
## VPN

IP maison de location:176.145.120.87
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

# Connect to servors:
## Connection
### Get external IP
```bash
curl ifconfig.co
```
### Notebook access (jupyter / marimo)
On remote machine:
* start Jupyter
```bash
jupyter lab --port=9876 --ip=127.0.0.1 --no-browser
```
* start Marimo
```bash
 marimo edit --host 0.0.0.0 --port 9877
```
On local machine:
```bash 
ssh -L 9876:localhost:9876 -L 9877:localhost:9877 alfheim
```
Open the server on the local machine: http://127.0.0.1:9876/lab
## Datarmor
```
Host datarmor  
        AddressFamily inet  
        HostName datarmor-access  
        User lgaultie  

Host computer101  
        AddressFamily inet  
        HostName compute-101-23 
        User lgaultie  
        ProxyJump datarmor
```
### Create Jupyter Environment
```bash
module load anaconda 
conda create -n skim_plot python=3.9 
conda activate skim_plot 
conda install matplotlib cartopy ... 
# check that condo-env path is in .condarc 
conda install ipykernel 
source deactivate
```

Installed kernelspec s3ng_env in /home/eh/gaultierl/.local/share/jupyter/kernels/s3ng_env
## Jackzilla
## Trex

## Tunnel blick
### Deolen Main
```
##############################################
# Sample client-side OpenVPN 2.0 config file #
# for connecting to multi-client server.     #
#                                            #
# This configuration can be used by multiple #
# clients, however each client should have   #
# its own cert and key files.                #
#                                            #
# On Windows, you might want to rename this  #
# file so it has a .ovpn extension           #
##############################################

# Specify that we are a client and that we
# will be pulling certain config file directives
# from the server.
client
 
# Use the same setting as you are using on
# the server.
# On most systems, the VPN will not function
# unless you partially or fully disable
# the firewall for the TUN/TAP interface.
dev tap
; 00:16:3E:24:E8:80
;dev tun

# Windows needs the TAP-Win32 adapter name
# from the Network Connections panel
# if you have more than one.  On XP SP2,
# you may need to disable the firewall
# for the TAP adapter.
;dev-node MyTap

# Are we connecting to a TCP or
# UDP server?  Use the same setting as
# on the server.
proto tcp-client

;proto udp

# The hostname/IP and port of the server.
# You can have multiple remote entries
# to load balance between the servers.
remote deolen-bouygues.odl.bzh 443
;remote my-server-2 1194
;remote 176.183.165.109 443

# Choose a random host from the remote
# list for load-balancing.  Otherwise
# try hosts in the order specified.
;remote-random
lladdr 00:16:3E:24:E8:80
dhcp-option DNS 192.168.177.247
dhcp-option DNS 1.1.1.1
dhcp-option DNS 1.0.0.1

# Keep trying indefinitely to resolve the
# host name of the OpenVPN server.  Very useful
# on machines which are not permanently connected
# to the internet such as laptops.
resolv-retry infinite

# Most clients don't need to bind to
# a specific local port number.
nobind

# Downgrade privileges after initialization (non-Windows only)
;user nobody
;group nobody

# Try to preserve some state across restarts.
persist-key
;persist-tun

# If you are connecting through an
# HTTP proxy to reach the actual OpenVPN
# server, put the proxy server/IP and
# port number here.  See the man page
# if your proxy server requires
# authentication.
;http-proxy-retry # retry on connection failures
;http-proxy [proxy server] [proxy port #]
  
# Wireless networks often produce a lot
# of duplicate packets.  Set this flag
# to silence duplicate packet warnings.
;mute-replay-warnings
  
# SSL/TLS parms.
# See the server config file for more
# description.  It's best to use
# a separate .crt/.key file pair
# for each client.  A single ca
# file can be used for all clients.
ca odl_ca_cert.pem
cert lgaultier@oceandatalab.com_cert.pem
key lgaultier@oceandatalab.com_key.pem

# Verify server certificate by checking that the
# certicate has the correct key usage set.
# This is an important precaution to protect against
# a potential attack discussed here:
#  http://openvpn.net/howto.html#mitm
#
# To use this feature, you will need to generate
# your server certificates with the keyUsage set to
#   digitalSignature, keyEncipherment
# and the extendedKeyUsage to
#   serverAuth
# EasyRSA can do this for you.
;remote-cert-tls server
  
# If a tls-auth key is used on the server
# then every client must also have the key.

auth SHA512
tls-auth ta.key 1
  
# Select a cryptographic cipher.
# If the cipher option is used on the server
# then you must also specify it here.
# Note that 2.4 client/server will automatically
# negotiate AES-256-GCM in TLS mode.
# See also the ncp-cipher option in the manpage
cipher AES-256-CBC
data-ciphers AES-256-CBC

# Enable compression on the VPN link.
# Don't enable this unless it is also
# enabled in the server config file.
compress lzo

# Set log file verbosity.
verb 3

# Silence repeating messages
mute 10

route-delay 15
up-delay
script-security 1
up "/bin/sh -c '/usr/sbin/ipconfig set $dev DHCP'"
```
### Deolen Loc
```
remote 176.145.120.87 443
```

### Deolen OVH
```
remote deolen.odl.bzh 443
```
# Tips specific to tools
## Overleaf
If not compiling remove package cellspace: \usepackage{cellspace}
## Git
## Tmux

## SEAScope

### Debug on MAC
```bash
⚓ open -a SEAScope --args -f debug
```
vi ~/Library/Logs/com.oceandatalab.SEAScope/seascope.log

### SEAScope movie
Rappel raccourcis clavier:  
  
F plein écran on/off  
H cache l'interface on/off  
L Verrouille le zoom de la worldmap pour qu'elle soit toujours visible entièrement (peu importe la taille de la fenêtre) on/off

 
## Visual Studio Code
To switch between views, **press Ctrl+Shift+V in the editor**. You can view the preview side-by-side (Ctrl+K V) with the file you are editing and see changes reflected in real-time as you edit.

## Screen

```bash
screen -ls
screen -S [new-session]
screen -r [resume-session]
screen -XS [pid] quit
```

# Download data
## Using AWS
### List the files

```bash
aws s3 ls s3://noaa-goes17/ABI-L1b-RadC/2023/004/14/ --no-sign-request
```

### Save the listing to a file

```bash
aws s3 ls s3://noaa-goes17/ABI-L1b-RadC/2023/004/14/ --no-sign-request > file_listing.txt
```

### Download all files in that directory


```bash
aws s3 cp s3://noaa-goes17/ABI-L1b-RadC/2023/004/14/ . --recursive --no-sign-request
```

**Or download to a specific folder:**

bash

```bash
aws s3 cp s3://noaa-goes17/ABI-L1b-RadC/2023/004/14/ ./goes17_data/ --recursive --no-sign-request
```

The `--no-sign-request` flag is key — it lets you access the public bucket without AWS credentials.

If you don't have the AWS CLI installed:

bash

```bash
# On Ubuntu/Debian
sudo apt install awscli

# Or via pip
pip install awscli
```

## Using CMEMS toolbox
```bash
pip install copernicus-marine
```

## 

# Python
## Pip 
```bash
pip cache purge

```


# Deploy application on iOS / Android
## for iOs

### Install
Install Xcode using the App Store
Toolchain

```bash
brew install autoconf automake libtool pkg-config
brew link libtool
```

```bash 
toolchain build hostpython3
toolchain build python3 kivy 
toolchain build numpy
toolchain status
```
### Install dependancies
```bash
toolchain pip install kivy_garden.mapview             
toolchain pip install garmin-fit-sdk
toolchain pip install requests
toolchain build pillow
pip install --force-reinstall cookiecutter
```
## Create app
```bash
toolchain create Windlog /Users/lgaultier/windsurf_app
```

## for Android

### Install 
Install buildozer and its dependencies
Android requires java to compile
```bash
brew install openjdk@17
sudo ln -sfn /opt/homebrew/opt/openjdk@17/libexec/openjdk.jdk /Library/Java/JavaVirtualMachines/openjdk-17.jdk
echo 'export PATH="/opt/homebrew/opt/openjdk@17/bin:$PATH"' >> ~/.zshrc
echo 'export CPPFLAGS="-I/opt/homebrew/opt/openjdk@17/include"' >> ~/.zshrc
```

```bash
pip install buildozer setuptools
brew install git ffmpeg readline sqlite xz zlib 
```
Resole openssl1.1 legacy on android
```bash
brew install openssl@3
export CFLAGS="-I$(brew --prefix openssl@3)/include" 
export LDFLAGS="-L$(brew --prefix openssl@3)/lib" exportGRPC_PYTHON_BUILD_SYSTEM_OPENSSL=1 
export GRPC_PYTHON_BUILD_SYSTEM_ZLIB=1
```

Edit prerequisites.py file:
```bash
find .buildozer -name "prerequisites.py" 
.buildozer/android/platform/python-for-android/pythonforandroid/prerequisites.py
```

### Initialize repo
If no spec file:
```
buildozer init
```
### Configure the `.spec` File

Open `buildozer.spec` in a text editor and update these key fields:
- `title`: Your app's name.
- `package.name`: A unique name (e.g., `myapp`).
- `package.domain`: Usually your website in reverse (e.g., `org.yourname`).
- `requirements`: List every library your app uses. At minimum: `python3, kivy`. If you use others (like `requests` or `pandas`), add them here.
- `source.include_exts`: Ensure `.py`, `.kv`, and any image/asset extensions you use are listed.

### Build the apk
```bash
buildozer android debug
```
to install it, settings > App > Special App Access > Install Unknown apps

### Debug using Wifi

If you hate cables but want the convenience of the `run` command, you can actually connect your phone to Buildozer via Wi-Fi using **ADB** (Android Debug Bridge).

1. Connect via USB _one last time_.
2. Run `adb tcpip 5555`.
3. Disconnect the cable.
4. Run `adb connect [YOUR_PHONE_IP]`.
5. Now, `buildozer android debug deploy run` will work wirelessly!