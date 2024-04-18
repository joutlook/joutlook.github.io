+++
title = 'postman_install_pop'
date = 2024-04-18T16:58:01+08:00
draft = false
tags = ['Linux']
comments = true
+++
## Installing Postman

__Step 1__

If any version of postman is installed we need to remove it
```sh
sudo rm -rf /opt/Postman
```

__Step 2__

This will install postman to `/tmp` directory and move it to `/opt/` directory.
```sh
tar -C /tmp/ -xzf <(curl -L https://dl.pstmn.io/download/latest/linux64) && sudo mv /tmp/Postman /opt/
```

__Step 3__

Create a desktop file
```sh
sudo tee -a /usr/share/applications/postman.desktop << END
[Desktop Entry]
Encoding=UTF-8
Name=Postman
Exec=/opt/Postman/Postman
Icon=/opt/Postman/app/resources/app/assets/icon.png
Terminal=false
Type=Application
Categories=Development;
END
```
