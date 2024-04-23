# Deploying Node.js app on EC2 instance

Before you start make sure you have done the steps listed here : [Link](https://github.com/joeodx/Tech_258_cloud/tree/master/Deploying_Vm_cloud)

## Step 1 - Configure port

* When you are launching your VM in Aws make sure add a custom TCP with the port 3000.
* This is the port for node.js 

![55.jpg](..%2Fpictures%2F55.jpg)

## Step 2 - Configure port

* When you are launching your VM in Aws make sure add a custom TCP with the port 3000.
* This is the port for node.js


## Step 3 - Open Ubuntu terminal 

* SSH into your Ubuntu server and add the following commands

![33.jpg](..%2Fpictures%2F33.jpg)

## Step 4 - Upgrade and Upgrade Packages

```python
sudo apt update =y
sudo DEBIAN_FRONTEND=noninteractive apt upgrade -y
```
## Step 5 - Install nginx

* Install Nginx 

```python
sudo DEBIAN_FRONTEND=noninteractive apt install nginx 
```

## Step 6 - Restarting nginx

```python
sudo systemctl restart nginx
```

## Step 7 - Enabiling nginx

```python
sudo systemctl enable nginx
```

## Step 8 - Install node version 20

```python
curl -fsSL https://deb.nodesource.com/setup_20.x | sudo DEBIAN_FRONTEND=noninteractive -E bash - &&\ sudo DEBIAN_FRONTEND=noninteractive apt-get install -y nodejs
```

## Step 9 - Check the node.js version.

```python
node -v
```

## Step 10 - Create a apps folder then CD

```python
mkdir apps cd apps
```
## Step 11 - Clone the folder containing the app

```python
git clone https://github.com/joeodx/Sparta_test_app2
```
## Step 12 - CD into app folder

```python
cd ~/apps/tech258_sparta_test_app/app
```

## Step 13 - Create a apps folder then CD

```python
mkdir apps cd apps
```
## Step 14 - sudo npm install

```python
git clone https://github.com/joeodx/Sparta_test_app2
```
## Step 15 - sudo npm install -g pm2

```python
cd ~/apps/tech258_sparta_test_app/app
```
## Step 16 - Stop all processes that pm2 is running

```python
sudo pm2 stop all
```
## Step 17 - Start app.js using pm2

```python
sudo pm2 start node app.js
````
**************************************************************





