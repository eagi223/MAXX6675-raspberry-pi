# Raspberry-Pi-Tutorials
Useful Raspberry Pi Tuturials

__This is a very quick and easy way to start Node-Red automatically when your Raspberry Pi boots up without having to do any of the manual scripting legwork.__

*It is assumed that you already have downloaded Node-Red onto your Pi*

* Download the PM2 Node Process Manager:
```bash
sudo npm install -g pm2
```
* Determine where you've installed Node-Red. This command should tell you the location of the executable if it is correctly installed on your Pi.
```bash
which node-red
```

* Add Node-Red to PM2. *Replace /usr/bin/ with the path that the __which node-red__ command gave you if it is different.*
```bash
pm2 start /usr/bin/node-red --node-args="--max-old-space-size=128" -- -v
```

* Generate the startup script.
```bash
pm2 save
pm2 startup
```
