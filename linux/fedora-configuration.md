# Fedora Configuration

### Optimize DNF Configuration
```
echo 'max_parallel_downloads=10' | sudo tee -a /etc/dnf/dnf.conf
echo 'fastestmirror=True' | sudo tee -a /etc/dnf/dnf.conf
echo 'deltarpm=true' | sudo tee -a /etc/dnf/dnf.conf
```

### Update-grub
```
sudo grub2-mkconfig -o /etc/grub2-efi.cfg
```

### Install multimedia codecs
```
sudo dnf install gstreamer1-plugins-{bad-\*,good-\*,base} gstreamer1-plugin-openh264 gstreamer1-libav --exclude=gstreamer1-plugins-bad-free-devel
sudo dnf install lame\* --exclude=lame-devel
sudo dnf group upgrade --with-optional Multimedia
```

### Install TLP on notebooks
```
sudo dnf install tlp tlp-rdw
```

### Install other stuffs
```
sudo dnf install fish && sudo usermod --shell /usr/bin/fish $USER
echo 'set -gx fish_prompt_pwd_dir_length 0' | tee -a ~/.config/fish/config.fish
sudo dnf install -y 'google-roboto*' 'mozilla-fira*' fira-code-fonts
sudo dnf install ksnip
sudo dnf install git
```

### OneDrive setup
```
sudo -v ; curl https://rclone.org/install.sh | sudo bash
mkdir ~/OneDrive
rclone config
echo 'rclone --vfs-cache-mode writes mount OneDrive:  ~/OneDrive' > ~/.local/mount-one-drive.sh
chmod +x ~/.local/mount-one-drive.sh
```

