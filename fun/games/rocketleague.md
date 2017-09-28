**The game is failing in linux (at least fedora 26), as a work around create steam_appid.txt file:**

```bash
echo 252950 > ~/.local/share/Steam/steamapps/common/rocketleague/Binaries/Linux/steam_appid.txt
```

**To run the game:**
```bash
~/.local/share/Steam/steamapps/common/rocketleague/Binaries/Linux/RocketLeague
```

**Create a desktop shortcut**
```bash
su -

echo '#!/usr/bin/env xdg-open
[Desktop Entry]
Name=Rocket League
Type=Application
Exec=/home/YOUR_USERNAME/.local/share/Steam/steamapps/common/rocketleague/Binaries/Linux/RocketLeague
Icon=/home/YOUR_USERNAME/.steam/steam/steamapps/common/rocketleague/TAGame/Splash/Linux/Splash.bmp
Terminal=false' > /usr/share/applications/rocket_league.desktop
```

**ERROR: Not logged in to Rocket League Servers**

Based on: this [question](https://steamcommunity.com/app/252950/discussions/0/350542145709647928/)

```bash
# FIX: on fedora
su -
ln -s /etc/ssl/certs/ca-bundle.crt /etc/ssl/certs/ca-certificates.crt
```
