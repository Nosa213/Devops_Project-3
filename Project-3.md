# Web-Solution-With-Wordpress

## WordPress (WP, WordPress.org) is a free and open-source content management system (CMS) written in PHP[4] and paired with a MySQL or MariaDB database. Features include a plugin architecture and a template system, referred to within WordPress as Themes. WordPress was originally created as a blog-publishing system but has evolved to support other web content types including more traditional mailing lists and forums, media galleries, membership sites, learning management systems (LMS) and online stores. 


## To function, WordPress has to be installed on a web server, either part of an Internet hosting service like WordPress.com or a computer running the software package WordPress.org in order to serve as a network host in its own right.


## Three-tier Architecture

### Generally, web, or mobile solutions are implemented based on what is called the Three-tier Architecture.


![image](https://user-images.githubusercontent.com/85270361/134702570-9fe3ec31-4ba7-4545-8f47-1104eda0a93d.png)


## 3-Tier Setup

* A Laptop or PC to serve as a client
* An EC2 Linux Server as a web server (This is where you will install WordPress)
* An EC2 Linux server as a database (DB) server

**Three-tier Architecture** allows any one of the three tiers to be upgraded or replaced independently.

The user interface is implemented on any platform such as a desktop PC, smartphone or tablet as a native application, web app, mobile app, voice interface, etc. It uses a standard graphical user interface with different modules running on the application server.

The relational database management system on the database server contains the computer data storage logic.

The middle tiers are usually multitiered.

Since the three are not physical but logical in nature, they may run in different servers both in on-premises based solutions, as well as in software-as-a-service (SaaS).


## Benefit of a Three-Tier Architecture

* it provides great freedom to development teams who can independently update or replace only specific parts of the application without affecting the product as a whole.

* The application can be scaled up and out rather easily by detaching the front-end application from the databases that are selected according to the individual needs of the customer.

* New hardware, such as new servers, can also be added at a later time to deal with massive amounts of data or particularly demanding services.

* A three-tier-architecture also provides a higher degree of flexibility to enterprises who may want to adopt a new technology as soon as it becomes available.

* Critical components of the application can be encapsulated and retained while the whole system keeps evolving organically.

* Development cycle or upgrade times are significantly improved ensuring minimal disruption in customer’s experience.

* Different teams can work on different sections of the application rather than on the full stack according to their areas of expertise, improving their efficiency and speed.


The Three Tiers in a Three-Tier Architecture

### Presentation Tier

* Occupies the top level and displays information related to services commonly available on a web browser or web-based application in the form of a graphical user interface (GUI).

* It constitutes the front-end layer of the application and the interface with which end-users will interact directly.

* This tier is usually built on web development frameworks, such as CSS or JavaScript, and communicates with other tiers by sending results to the browser and other tiers in the network through API calls.

### Application Tier

* This tier — also called the middle tier, logic tier, business logic or logic tier — is pulled from the presentation tier.

* It controls the application’s core functionality by performing detailed processing and is usually coded in programming languages, such as Python, Java, C++, .NET, etc.

### Data Tier

* Houses database servers where information is stored and retrieved.

* Data in this tier is kept independent of application servers or business logic, and is managed and accessed with programs, such as MongoDB, Oracle, MySQL, and Microsoft SQL Server.


# In this project, We will have the hands-on experience that showcases Three-tier Architecture while also ensuring that the disks used to store files on the Linux servers are adequately partitioned and managed through programs such as gdisk and LVM respectively. The following steps will be followed to achieve our aim and objectives of this project.



# LAUNCH AN EC2 INSTANCE THAT WILL SERVE AS “WEB SERVER”.

## Step 1 — Prepare the Web Server

1* **Launch an EC2 instance that will serve as "Web Server". Create 3 volumes in the same AZ as your Web Server EC2, each of 10 GiB.**

2* **Create and Attach all three volumes one by one to your Web Server EC2 instance**

3* **Open MobaXterm and connect Ec2 instances using public IP Address and begin configuration**


```
# lsblk
```
