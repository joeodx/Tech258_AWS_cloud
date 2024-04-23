#!/bin/bash

echo updating
sudo apt update -y
echo done!

echo upgrading packages
sudo DEBIAN_FRONTEND=noninteractive apt upgrade -y 
echo done!

echo installing nginx
sudo DEBIAN_FRONTEND=noninteractive apt install nginx 
echo done!

echo restarting nginx
sudo systemctl restart nginx
echo done!

echo enabling nginx
sudo DEBIAN_FRONTEND=noninteractive systemctl enable nginx
echo done!

install git 
sudo apt install git -y
echo done!

echo get app
git clone https://github.com/joeodx/Sparta_test_app2.git
echo done!

echo install node js
script3.sh
curl -fSSL https://deb.nodesource.com/setup_20.x | sudo -E bash - && sudo DEBIAN_FRONTEND=noninteractive apt-get install -y nodejs 
echo done!

echocheck js version
node -v
echo done!

echo installing app 
npm install

echo install npm
sudo npm install
echo done!

echo installing pm2
sudo npm install -g pm2
echo done

echo start app
sudo pm2 start app.js
echo Done!
