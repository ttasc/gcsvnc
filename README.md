# HOW TO

- Create [ZeroTier Network](https://my.zerotier.com/network/) (you need an account), see [docs](https://docs.zerotier.com/start/)
- On your local machine, install [ZeroTier](https://docs.zerotier.com/releases) and [join](https://docs.zerotier.com/cli) the network you just created
- Log in to your [google cloud shell](https://shell.cloud.google.com/?cloudshell=true&show=terminal) and run:
    ```
    git clone https://github.com/TTlaugh/gcsvnc.git
    cd gcsvnc && chmod +x gcsvnc
    ./gcsvnc setup # setup enviroment before start server
    ./gcsvnc       # start server
    ```
- Then [join](https://docs.zerotier.com/cli) your cloud shell to the network you created above
- Finally, connect to your VNC server by any VNC viewer you want with `server_ip_address:5901`. E.g with TigerVNC: `vncviewer 192.168.192.1:5901`
