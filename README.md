# Nethunter-GUI
Instalador da interface gráfica no nethunter rootless

### Instalar a CLI nano
Obs! Escolha a versão `nano` ou `minimal`
```
apt update && apt install wget -y && wget -O install-nethunter-termux https://offs.ec/2MceZWr && bash install-nethunter-termux
```

### Instalar a GUI

Conceder acesso a internet ao nethunter:
```
echo 'nameserver 8.8.8.8' >> /etc/resolv.conf
```

Execute o nethunter: `nh`
```
sudo apt update && sudo apt full-upgrade -y && sudo apt autoremove -y && sudo apt install udisks2 -y && sudo apt install xfce4 xfce4-whiskermenu-plugin qterminal dbus-x11 firefox-esr tigervnc-standalone-server kali-themes -y
```

Criar vncstart:
```
cat ->> /usr/bin/vncstart <<- EOF
vncserver -geometry 1360x720 -xstartup /usr/bin/xfce4-session
EOF
```

Criar vncstop:
```
cat ->> /usr/bin/vncstop <<- EOF
vncserver -kill :1
pkill dbus-launch
pkill ssh-agent
pkill gpg-agent
pkill xiccd
EOF
```

Permissôes:
```
chmod +x /usr/bin/vncst*
```

Execute:
```
vncstart
```
