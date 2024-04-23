# Two Tier Deployment

## CONNECTING UP MONGO 7.0G ON UBUNTU

[](https://i.ibb.co/kX3JpCQ/1-b0-Tt-GI6g-WFLlt-L1-Qk-Rx-Vdg.png)

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

##  Step 8: Connect the app and MongoDB instances
* You will need to restart to make sure these changes are working
* We also need to enable the MongoDB service so if we reboot our instance 
```
sudo systemctl restart mongod
sudo systemctl enable mongod
```

##  Step 9: Connect the app and MongoDB instances
* SSH into your application ec2 instance
* Create an environmental variable DB_HOST which will allow for a connection between the App and DB instance.
```
export DB_HOST=mongodb://<db_instance_private_ip>/posts
```

##  Step 10: Change into your app repository

* Run npm install and npm start

```
npm install 
npm start 
```

* These two commands should rerun our app process with the connection string we created stored in the variable DB_HOST
* This will then seed into your database during the npm install process

## Step 11 : Congratulations!

* Type the following command into your browser with your public IP address

```python
app_instance_public_ip:3000/posts
```
* You should get the following page if sucessful : 

![77.jpg](..%2Fpictures%2F77.jpg)

****************************************************************

