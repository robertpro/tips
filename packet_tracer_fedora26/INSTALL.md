**Install Packet Tracer 7.1 linux 64**

> Based on this [guide](http://www.bt0.ninja/packettracer-7-in-fedora-26/)

**Install dependencies**

```bash
cat /etc/redhat-release 
Fedora release 26 (Twenty Six)

Log in as root
su -
dnf copr enable bt0dotninja/openssl-lib-compat
dnf install openssl-lib-compat libpng12
```

**Install Packet Tracer**
```bash
mkdir packet_tracer
tar -xzf PacketTracer71_64bit_linux.tar.gz -C packet_tracer
cd packet_tracer
chmod +x install
sudo ./install
```

**Graphical Launcher on Gnome**
```bash
echo '#!/usr/bin/env xdg-open
[Desktop Entry]
Name=Packet Tracer 7.1
Comment=Networking Cisco 
GenericName=PacketTracer 7 
Type=Application
Exec=/opt/pt/packettracer 
Icon=pt7
StartupNotify=true
Terminal=false' > /usr/share/applications/pt7.desktop
```

**Add missing libraries**
_I got those libraries from genymotion..._
```bash
# As user...
mkdir ~/.lib64
wget https://github.com/robertpro/tips/raw/59d14e7b148ebd10698ad3621b4c8a0bad38844b/packet_tracer_fedora26/libicudata.so.52 -O ~/.lib64/libicudata.so.52
wget https://github.com/robertpro/tips/raw/59d14e7b148ebd10698ad3621b4c8a0bad38844b/packet_tracer_fedora26/libicui18n.so.52 -O ~/.lib64/libicui18n.so.52
wget https://github.com/robertpro/tips/raw/59d14e7b148ebd10698ad3621b4c8a0bad38844b/packet_tracer_fedora26/libicuuc.so.52 -O ~/.lib64/libicuuc.so.52

# As user...
sudo sed -i "s|lib|lib:$HOME/.lib64|g" /opt/pt/packettracer
```
