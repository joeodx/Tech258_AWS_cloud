# Two Tier Deployment

## CONNECTING UP MONGO 7.0G ON UBUNTU

### Before you start make sure to create a MongoDb instance onb AWS and change the security group to allow traffic on port 27017
### When creating the instance, nake sure tio put in these ports when you edit the security group settings 

* SSH - port 22 (0. 0. 0. 0)
Make sure this connection can be established anywhere.
* Mongo DB - port 27017 (0. 0. 0. 0)
Create a custom TCP port for Mongo Db that also can be established anywhere 


## Step 1: Update package lists
* Run these commands to refresh our local packages using upgrade and update command. 
```
sudo apt update -y
```

##  Step 2: Upgrade installed packages
```
sudo DEBIAN_FRONTEND=noninteractive apt upgrade -y 
```

##  Step 3: Install gnupg and curl packages
* This is to specifically download packages we need for MongoDb but is more of a safe command as we had already installed packages
```
sudo apt-get install gnupg curl -y
```
##  Step 4: Download the MONGODB GPG Key
* This is the key we will use to verify the mongoDb packages that we will install
```
curl -fsSL https://www.mongodb.org/static/pgp/server-7.0.asc | \
   sudo gpg -o /usr/share/keyrings/mongodb-server-7.0.gpg \
   --dearmor
```
##  Step 5: Create a list file for MongoDb
* This is a file for MongoDB t o provide a convenient way for packages like 'apt' to manage the instilisation 
```
echo "deb [ arch=amd64,arm64 signed-by=/usr/share/keyrings/mongodb-server-7.0.gpg ] https://repo.mongodb.org/apt/ubuntu jammy/mongodb-org/7.0 multiverse" | sudo tee /etc/apt/sources.list.d/mongodb-org-7.0.list
```

## Step 6: Install MongoDB 
* We don't want the latest version of MongDB so we have to be specific on what version to download
``` 
sudo DEBIAN_FRONTEND=noninteractive apt-get install -y mongodb-org=7.0.6 mongodb-org-database=7.0.6 mongodb-org-server=7.0.6 mongodb-mongosh=2.2.4 mongodb-org-mongos=7.0.6 mongodb-org-tools=7.0.6
```

## Step 7: Configure BindIP

* We need to allow it to have connections from anywhere. Remember the port (0. 0. 0. 0) that allows this
* We need to edit the variable bindIp in the MongoDB config file. 
* This is located in the etc folder and can use the 'sed' folder
```python
sudo sed -i 's/bindIp: 127.0.0.1/bindIp: 0.0.0.0/' /etc/mongod.conf
```
* use the '-i' flag to edit and save the changes 

##  Step 9: Connect the app and MongoDB instances
* SSH into your application ec2 instance
* Create an environmental variable DB_HOST 
```
curl -fSSL https://deb.nodesource.com/setup_20.x | sudo -E bash - && sudo DEBIAN_FRONTEND=noninteractive apt-get install -y nodejs 
```

##  Step 9: Check Node.js version

```
node -v
```

##  Step 10: Set the DB_HOST environment variable
```
export DB_HOST=mongodb://172.31.33.53/posts
printenv DB_HOST
```

* Remember to change to your ip address

## Step 11: Install application dependencies
```
npm install
```

## Step 12: Install npm dependencies globally
```
sudo npm install
```
## Step 13: Install PM2 process manager globally
```
sudo npm install -g pm2
```
##  Step 14: Start the application using PM2
```
sudo pm2 start app.js