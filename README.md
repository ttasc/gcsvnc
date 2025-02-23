## HOW IT WORK

### Initial setup
- Create [ZeroTier Network](https://my.zerotier.com/network/) (you need an account), see [docs](https://docs.zerotier.com/start/)
- On your local machine, install [ZeroTier](https://docs.zerotier.com/releases) and [join](https://docs.zerotier.com/cli) the network you just created
- Log in to your [google cloud shell](https://shell.cloud.google.com/?cloudshell=true&show=terminal) and run: `git clone https://github.com/ttasc/gcsvnc.git`

### Configuration
> This script defaults to using **xfce4** as DE and the default vncserver password is `gcsvnc`

Move to **gcsvnc** folder and open `gcsvnc` file with your editor, then change:
- **Password:** Change the value of `PASS` variable at *line 4*.
- **Pre-install packages:** rewrite `install_packages()` function at *line 9* to install anything you want.
- **Startup:** Change the value of `fxstartup` variable at *line 19*. The value of variable `fxstartup` will be written to the file `~/.vnc/xstartup`. This is the script to start your graphical session and anything else you want to launch on login (like xinitrc).
### Run server
- Inside **gcsvnc** folder, run:
    ```
    chmod +x gcsvnc
    ./gcsvnc setup # setup enviroment before start server
    ./gcsvnc       # start server
    ```
- Then [join](https://docs.zerotier.com/cli) your cloud shell to the network you created above
- Finally, connect to your VNC server by any [VNC viewer](https://wiki.archlinux.org/title/TigerVNC#Connecting_to_vncserver) you want with `server_ip_address:number` (see [here](https://docs.zerotier.com/start#find-the-zerotier-ip-addresses-of-your-devices) to find the ip address). E.g with TigerVNC: `vncviewer 192.168.192.1:1`. Then enter *password `gcsvnc` (default)*
> **Note:**
> - You need to [authenticate](https://docs.zerotier.com/start#authorize-your-device) every time you join a device to a ZeroTier Network if the network you created is private.
> - You can connect many clients to one server by running `gcsvnc` script many times, then connect to server by `server_ip_address:<1,2,3,...>`

### Options
```
gcsvnc [OPTION]      # start VNC server
OPTION:
    setup            # setting up the server
    kill <1,2,3,...> # kill a VNC server running at :<1,2,3,...>
    killall          # kill all VNC server instances
```

## TODO
- **Make it has sound:** cloud shell doesn't use systemd or any linux init system, so can't start a sound server.
