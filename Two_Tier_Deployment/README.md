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
* This is the jey we will use to verify the mongoDb packages that we will install
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

## Step 6: Install Git version control
``` 
sudo apt install git -y
```

## Step 7: Clone the application repository

```
git clone https://github.com/joeodx/Sparta_test_app2.git
```

##  Step 8: Install Node.js using NodeSource repository
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