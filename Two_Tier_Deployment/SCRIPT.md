* Deploy Database first

#!/bin/bash

echo updating...
sudo apt update -y
echo done!

# upgrade 
sudo DEBIAN_FRONTEND=nonnoninteractive apt upgrade -y

# Install gnupg
sudo apt-get install gnupg curl -y

Download the Mongodb GPG key
curl -fsSL https://www.mongodb.org/static/pgp/server-7.0.asc | \
   sudo gpg -o /usr/share/keyrings/mongodb-server-7.0.gpg \
   --dearmor

echo "deb [ arch=amd64,arm64 signed-by=/usr/share/keyrings/mongodb-server-7.0.gpg ] https://repo.mongodb.org/apt/ubuntu jammy/mongodb-org/7.0 multiverse" | sudo tee /etc/apt/sources.list.d/mongodb-org-7.0.list
sudo apt-get install gnupg curl
echo done

sudo DEBIAN_FRONTEND=noninteractive apt-get update

# Create a list file for MongoDB
curl -fsSL https://www.mongodb.org/static/pgp/server-7.0.asc | \
   sudo gpg -o /usr/share/keyrings/mongodb-server-7.0.gpg \
   --dearmor

# Install Mongo
sudo DEBIAN_FRONTEND=noninteractive apt-get install -y mongodb-org=7.0.6 mongodb-org-database=7.0.6 mongodb-org-server=7.0.6 mongodb-mongosh=2.2.4 mongodb-org-mongos=7.0.6 mongodb-org-tools=7.0.6

## CONFIGURE BINDIP
sudo sed -i 's/bindIp: 127.0.0.1/bindIp: 0.0.0.0/' /etc/mongod.conf

## RESTART mONGOdB 
sudo systemctl restart mongod
sudo systemctl enable mongod

*THEN APPLCIATION

#!/bin/bash

echo updating...
sudo apt update -y
echo done!

echo upgrading packages...
sudo DEBIAN_FRONTEND=noninteractive apt upgrade -y
echo done!

echo installing nginx...
sudo DEBIAN_FRONTEND=noninteractive apt install nginx -y < /dev/null
echo done!

# configure reverse proxy
sudo sed -i '51s/.*/\t        proxy_pass http:\/\/localhost:3000;/' /etc/nginx/sites-enabled/default
# changing a config file

echo restarting nginx...
sudo systemctl restart nginx
echo done!

echo enabling nginx...
sudo systemctl enable nginx
echo done!

echo install node js
curl -fsSL https://deb.nodesource.com/setup_20.x | sudo DEBIAN_FRONTEND=noninteractive -E bash - && sudo DEBIAN_FRONTEND=noninteractive apt-get install -y nodejs
echo done!

echocheck js version
note -v
echo done!

echo set DB_HOST env var
export DB_HOST=mongodb://172.31.33.246:27017/posts
echo done!

echo install app folder
git clone https://github.com/joeodx/Sparta_test_app2.git
echo done!

echo cd app folder
cd ~/Sparta_test_app2/app
echo done!

echo install npm
sudo -E npm install
echo done!

echo install pm2
sudo -E npm install -g pm2
echo done!

echo stop app
pm2 stop app
echo done!

echo start app
pm2 start app.js app
echo done!