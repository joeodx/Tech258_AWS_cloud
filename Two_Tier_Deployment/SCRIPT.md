 # Deploy Database first - click to view code
 ************************************
``` 
#!/bin/bash

echo updating...
sudo apt update -y
echo done!

echo upgrade 
sudo DEBIAN_FRONTEND=nonnoninteractive apt upgrade -y
echo done!

echo Install gnupg
sudo apt-get install gnupg curl -y
echo done!

echo Download the Mongodb GPG key
curl -fsSL https://www.mongodb.org/static/pgp/server-7.0.asc | \
   sudo gpg -o /usr/share/keyrings/mongodb-server-7.0.gpg \
   --dearmor
echo done!

echo "deb [ arch=amd64,arm64 signed-by=/usr/share/keyrings/mongodb-server-7.0.gpg ] https://repo.mongodb.org/apt/ubuntu jammy/mongodb-org/7.0 multiverse" | sudo tee /etc/apt/sources.list.d/mongodb-org-7.0.list
sudo apt-get install gnupg curl
echo done

sudo DEBIAN_FRONTEND=noninteractive apt-get update
echo done!

echo Create a list file for MongoDB
curl -fsSL https://www.mongodb.org/static/pgp/server-7.0.asc | \
   sudo gpg -o /usr/share/keyrings/mongodb-server-7.0.gpg \
   --dearmor
echo done!

echo Install Mongo
sudo DEBIAN_FRONTEND=noninteractive apt-get install -y mongodb-org=7.0.6 mongodb-org-database=7.0.6 mongodb-org-server=7.0.6 mongodb-mongosh=2.2.4 mongodb-org-mongos=7.0.6 mongodb-org-tools=7.0.6
echo done!

echo CONFIGURE BINDIP
sudo sed -i 's/bindIp: 127.0.0.1/bindIp: 0.0.0.0/' /etc/mongod.conf
echo done!

echo RESTART mONGOdB 
sudo systemctl restart mongod
sudo systemctl enable mongod
echo done!
```

# Then deploy app- make sure to change ip address and configure settings

```
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

echo install git 
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

echo db_host ENV VAR
export DB_HOST=mongodb://(replace with id)/posts
printenv DB_HOST
echo done!

echo installing app 
npm install
echo done!

echo install npm
sudo npm install
echo done!

echo installing pm2
sudo npm install -g pm2
echo done!

echo start app
sudo pm2 start app.js
echo Done!
```