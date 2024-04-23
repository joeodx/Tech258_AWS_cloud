# DEPLOY YOUR APP TO AN E2 INSTANCE AND CONNECT TO E2 DATBASE 

* Make sure you are logged into your two e2 instances on aws and have two termional s pen one inside your ubuntu deployed app VM
* And the other in your deployed app vm 

The following commands go in that VM : 

## Step 1: Update package lists
```
sudo apt update -y
```

##  Step 2: Upgrade installed packages
```
sudo DEBIAN_FRONTEND=noninteractive apt upgrade -y 
```
##  Step 3: Install Nginx web server
```
sudo DEBIAN_FRONTEND=noninteractive apt install nginx 
```
##  Step 4: Restart Nginx
```
sudo systemctl restart nginx
```
##  Step 5: Enable Nginx to start on boot
```
sudo DEBIAN_FRONTEND=noninteractive systemctl enable nginx
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