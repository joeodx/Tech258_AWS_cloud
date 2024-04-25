# Azure

![](https://pendulum-it.com/wp-content/uploads/2020/05/Azure-logo-blue.jpg)
**************************************

## What is Azure?

* Azure is a cloud computing platform and service created by Microsoft. It provides a wide range of cloud services, including computing, storage, networking, databases, analytics, machine learning, artificial intelligence (AI), Internet of Things (IoT), and more.
*  Azure allows users to build, deploy, and manage applications and services through Microsoft-managed data centers located worldwide. It supports various programming languages, frameworks, and operating systems, providing flexibility for developers and businesses.
*   Azure's pay-as-you-go model enables users to scale resources up or down based on demand, making it suitable for startups, enterprises, and everything in between

## What are Azure regions?

![](https://media.licdn.com/dms/image/C5612AQEcGGBoDtX6rA/article-cover_image-shrink_600_2000/0/1631791147534?e=2147483647&v=beta&t=zx-rVPxTo4s7VCffuEwSpEXVcEQzKio8oz_YcfoaliA)

* Azure regions are geographically distributed data center locations where Microsoft Azure services are deployed and hosted. 
* These regions are interconnected through a high-speed network backbone to provide low-latency access and redundancy.
* Each region is independent, with its own set of data centers, power, cooling, and networking infrastructure. 
  
## What are avalaibilty zones?

![](https://techcommunity.microsoft.com/t5/image/serverpage/image-id/384721i3E9AD27F395754BC/image-size/original?v=v2&px=-1)

* Availability zones are unique physical locations within an Azure region, each made up of one or more data centers equipped with independent power, cooling, and networking. The purpose of availability zones is to provide resiliency and high availability for applications and data by distributing them across multiple zones within a region
* By spreading resources across multiple availability zones, Azure ensures that if one zone goes down due to a failure, the services and applications hosted in other zones remain unaffected. This design helps to minimize the risk of downtime and data loss.

## How is Azure structured?

Azure provides four levels of management: management groups, subscriptions, resource groups, and resources. 
<br>

![](https://learn.microsoft.com/en-us/azure/cloud-adoption-framework/ready/azure-setup-guide/media/organize-resources/scope-levels.png)

* Management groups help you manage access, policy, and compliance for multiple subscriptions. All subscriptions in a management group automatically inherit the conditions that are applied to the management group.
* Subscriptions logically associate user accounts with the resources that they create. Each subscription has limits or quotas on the amount of resources that it can create and use. Organizations can use subscriptions to manage costs and the resources that are created by users, teams, and projects.
* Resource groups are logical containers where you can deploy and manage Azure resources like virtual machines, web apps, databases, and storage accounts.
* Resources are instances of services that you can create in a resource group, such as virtual machines, storage, and SQL databases.

## What type of services does Azure provide?

Azure provides a vast array of cloud services across multiple categories to cater to various computing needs. Here are some of the types of services offered by Azure:

* Compute Services:
Virtual Machines (VMs)
Azure Kubernetes Service (AKS)

* Storage Services:
Blob Storage (object storage)
File Storage (managed file shares)

* Networking Services:
Virtual Network (VNet)
Azure Load Balancer

* Database Services:
Azure SQL Database (relational database)
Azure Cosmos DB (globally distributed NoSQL database)

## How can we access Azure services?

There are several ways to access and interact with Azure services, depending on your needs and preferences. Here are some common methods:

* Azure Portal:
The Azure Portal is a web-based user interface that provides a centralized dashboard for managing and monitoring Azure resources. You can use the portal to create, configure, and manage Azure services through a graphical interface.

* Azure CLI (Command-Line Interface):
Azure CLI is a command-line tool that allows you to manage Azure resources from a terminal or command prompt. It provides a set of commands for performing various tasks, such as creating VMs, managing storage, deploying applications, and more.

* Azure PowerShell:
Azure PowerShell is a scripting environment built on top of Windows PowerShell that enables you to automate and manage Azure resources using PowerShell cmdlets. It offers similar functionality to Azure CLI but with PowerShell syntax.

* Azure Management Libraries:
Azure Management Libraries are client libraries provided by Microsoft for popular programming languages like .NET, Java, Python, and Node.js. These libraries abstract the Azure REST API and provide higher-level constructs for managing Azure resources programmatically.

## What is the differnce between Azure and Azure DevOps

Azure is Microsoft's cloud computing platform, providing various cloud services. Azure DevOps, on the other hand, is a set of collaboration tools for software development, covering the entire DevOps lifecycle. Azure is for hosting applications, while Azure DevOps is for managing the development process.

## Why should you use the Azure Pricing calcualtor?

 You should use the Azure Pricing Calculator to plan and estimate the cost of Azure services before deploying them. This helps in budgeting, optimizing spending, and avoiding unexpected expenses by providing insights into the pricing of different services and configurations. Additionally, it allows for comparison of pricing options and adjustments to fit your specific needs, ensuring cost-effectiveness and resource optimization.

 ![](https://learn.microsoft.com/en-us/azure/cost-management-billing/costs/media/pricing-calculator/product-picker.png)


 ********************************************************