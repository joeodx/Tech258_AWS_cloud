# A step by step guide to deploying a virtual machine  on AWS using the gui console

![](https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcQWvOCHeqNEMvlfFJGfKoCQvZlwwgFDEo1D43M_yqLGrw&s)

Amazon Web Services (AWS) is a leading cloud computing platform that offers a wide range of services to help businesses and individuals build and manage their IT infrastructure in the cloud. From virtual servers and storage solutions to databases, machine learning, and more, AWS provides scalable and flexible resources that enable organizations to innovate, reduce costs, and scale their applications with ease.

We are going to show you step by step how to deploying a virtual machine (ec2-instance) on AWS using the gui console and how to deploy nginx on it :

### Step 1 - Sign in to the AWS Management Console: 

* Sign in to the AWS Management Console: Go to the AWS Management Console at https://aws.amazon.com/console/ and sign in to your AWS account.
<br>

![](pictures/screenshot1.jpg)

### Step 2 - Navigate to EC2 Dashboard: 

* Once logged in, navigate to the EC2 service by either searching for EC2 in the services search bar or by clicking on the "Services" dropdown menu at the top left corner and selecting EC2 under the "Compute" section.
<br>

![](pictures/screenshot2.jpg)

### Step 3 - Launch Instance

+ Launch Instance: On the EC2 Dashboard, click on the "Launch Instance" button to start the process of creating a new virtual machine.

![](pictures/screenshot3.jpg)

### Step 4 - Name and choose an Amazon Machine Image (AMI): 

* In the name and tags section give your virtual machine a name. Then In the Choose an Amazon Machine Image (AMI)" section, select the AMI that corresponds to the operating system and software configuration you want for your virtual machine. AWS provides a variety of pre-configured AMIs for different purposes, such as Amazon Linux, Ubuntu, Windows Server, etc. 
 In our case we are going to choose amazon Linux free tier option
<br> 


* *Machine images, often referred to as Amazon Machine Images (AMIs) in the context of AWS, are pre-configured templates that contain the necessary information to launch virtual servers, known as instances, in the cloud.*

![](pictures/screenshot4.jpg)

### Step 5 - Choose an instance type 

* Choose an Instance Type" section, select the instance type that suits your workload requirements. Instance types vary in terms of CPU, memory, storage, and networking capacity.In our case we will choose  After selecting the instance type, click "Next: Configure Instance Details".