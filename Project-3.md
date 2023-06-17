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

<img width="1159" alt="image" src="https://github.com/Nosa213/Devops_Project-3/assets/125190958/649c359f-19fc-4dcd-9616-a9f2a4595a15">




<img width="1276" alt="volumues" src="https://github.com/Nosa213/Devops_Project-3/assets/125190958/a04b2b3d-c3d3-4034-8b6d-f6abd7c520a2">




<img width="1255" alt="image" src="https://github.com/Nosa213/Devops_Project-3/assets/125190958/21215757-d775-438b-8ed4-d9eeefd39ef8">


3* **Attach all three volumes one by one to your Web Server EC2 instance.**


<img width="1207" alt="image" src="https://github.com/Nosa213/Devops_Project-3/assets/125190958/4aa7a162-228d-4b32-9186-8df6ac583928">






<img width="668" alt="image" src="https://github.com/Nosa213/Devops_Project-3/assets/125190958/9dec29e5-8b03-4733-9887-6a3ea3fe4c53">


**Next** Open up the Linux terminal to begin configuration


```
lsblk
```
Use lsblk command to inspect what block devices are attached to the server. Notice names of your newly created devices. All devices
in Linux reside in /dev/ directory. Inspect it with ls /dev/ and make sure you see all 3 newly created block devices there – their 
names will likely be xvdf, xvdh, xvdg.


<img width="499" alt="image" src="https://github.com/Nosa213/Devops_Project-3/assets/125190958/7195be65-90f1-4323-ba73-b0c80e9a2dc0">

```
df -h 
```
<img width="421" alt="image" src="https://github.com/Nosa213/Devops_Project-3/assets/125190958/ed22c539-c181-45ea-91f3-d07cb46eb1c8">

```
sudo gdisk /dev/xvdf
```

<img width="526" alt="image" src="https://github.com/Nosa213/Devops_Project-3/assets/125190958/8ede0148-f2a6-4677-bac1-4ced980e03dc">



```
sudo gdisk /dev/xvdg
```


<img width="493" alt="image" src="https://github.com/Nosa213/Devops_Project-3/assets/125190958/a41f24f6-86f0-4d27-a9fa-c4c8a8861ea4">


```
sudo gdisk /dev/xvdh
```

<img width="550" alt="image" src="https://github.com/Nosa213/Devops_Project-3/assets/125190958/1dd07136-3da3-4554-9421-5384454f6429">


* **We will use the command below to view the newly configured partition on each of the 3 disks**


```
lsblk
```

<img width="395" alt="image" src="https://github.com/Nosa213/Devops_Project-3/assets/125190958/6c29a94b-5d97-4019-8431-5ddf9ea75d33">

* **We use this command to check for available storage for Logical Volume Manager (LVM)**

```
sudo lvmdiskscan
```

<img width="341" alt="image" src="https://github.com/Nosa213/Devops_Project-3/assets/125190958/51fac7a6-688b-49e1-a52d-85ed6856db71">

* **Use vgcreate utility to add all 3 PVs to a volume group (VG). Name the VG webdata-vg**


```
sudo vgcreate webdata-vg /dev/xvdh1 /dev/xvdg1 /dev/xvdf1
```

<img width="384" alt="Screenshot 2023-06-11 213522" src="https://github.com/Nosa213/Devops_Project-3/assets/125190958/addcd69e-a239-41c2-aab3-08d0faf2ebbe">

* **Use vgcreate utility to add all 3 PVs to a volume group (VG). Name the VG webdata-vg**


```
sudo vgcreate webdata-vg /dev/xvdh1 /dev/xvdg1 /dev/xvdf1
```


```
sudo pvs
```

<img width="433" alt="image" src="https://github.com/Nosa213/Devops_Project-3/assets/125190958/3d754076-1608-42ee-a719-38b77c774850">



* **Use vgcreate utility to add all 3 PVs to a volume group (VG). Name the VG webdata-vg**


```
sudo vgcreate webdata-vg /dev/xvdh1 /dev/xvdg1 /dev/xvdf1
```

<img width="520" alt="image" src="https://github.com/Nosa213/Devops_Project-3/assets/125190958/c7f1f84a-3f7b-4842-9a89-382cad28b5aa">


* **Verify that your VG has been created successfully by running**


```
sudo vgs
```
<img width="362" alt="image" src="https://github.com/Nosa213/Devops_Project-3/assets/125190958/e10ba705-aa2a-4535-a419-7824f886b7f3">



* **Use lvcreate utility to create 2 logical volumes. apps-lv (Use half of the PV size), and logs-lv Use the remaining space of the PV size. NOTE: apps-lv will be used to store data for the Website while, logs-lv will be used to store data for logs.**


```
sudo lvcreate -n apps-lv -L 14G database-vg
sudo lvcreate -n logs-lv -L 14G database-vg
```



* **Verify that your Logical Volume has been created successfully by running**


```
sudo vgs
```

<img width="365" alt="image" src="https://github.com/Nosa213/Devops_Project-3/assets/125190958/ae5a34cc-ae16-444f-b8c6-53cfd9b48929">


* **Use lvcreate utility to create 2 logical volumes. apps-lv (Use half of the PV size), and logs-lv Use the remaining space of the PV size. NOTE: apps-lv will be used to store data for the Website while, logs-lv will be used to store data for logs.**


```
sudo lvcreate -n apps-lv -L 14G webdata-vg
sudo lvcreate -n logs-lv -L 14G webdata-vg
```

<img width="518" alt="image" src="https://github.com/Nosa213/Devops_Project-3/assets/125190958/a6b6f7fb-99a5-4f34-97e9-8cc86a718625">



* **Verify that your Logical Volume has been created successfully**


<img width="595" alt="image" src="https://github.com/Nosa213/Devops_Project-3/assets/125190958/40e3ad6a-dcd1-466a-98e8-22ed5c7f801e">



* **Verify the entire setup**

```
sudo vgdisplay -v #view complete setup - VG, PV, and LV
sudo lsblk 
```

<img width="488" alt="image" src="https://github.com/Nosa213/Devops_Project-3/assets/125190958/adf9eae4-01c0-48a7-9beb-c1ef4f1754a5">


* **Use mkfs.ext4 to format the logical volumes with ext4 filesystem**

```
sudo mkfs -t ext4 /dev/webdata-vg/logs-lv
```

<img width="479" alt="image" src="https://github.com/Nosa213/Devops_Project-3/assets/125190958/06cf92ce-ba31-415a-adbb-fe4bb9df1ec8">

### Create /var/www/html directory to store website files

```
sudo mkdir -p /var/www/html
```

### Create /home/recovery/logs to store backup of log data

```
sudo mkdir -p /home/recovery/logs
```

### Mount /var/www/html on apps-lv logical volume


```
sudo mount /dev/webdata-vg/apps-lv /var/www/html/
```

### Use rsync utility to backup all the files in the log directory /var/log into /home/recovery/logs (This is required before mounting the file system)

```
sudo rsync -av /var/log/. /home/recovery/logs/
```


### Mount /var/log on logs-lv logical volume. (Note that all the existing data on /var/log will be deleted. That is why step 15 above is very important)

```
sudo mount /dev/webdata-vg/logs-lv /var/log
```

### Restore log files back into /var/log directory

```
sudo rsync -av /home/recovery/logs/. /var/log
```


### Update /etc/fstab file so that the mount configuration will persist after restart of the server.


* **The UUID of the device will be used to update the /etc/fstab file;**

```
sudo blkid
```

<img width="530" alt="image" src="https://github.com/Nosa213/Devops_Project-3/assets/125190958/49c7328c-4ad2-4172-a1b0-0166eada023a">


```
sudo vi /etc/fstab
```

<img width="794" alt="image" src="https://github.com/Nosa213/Devops_Project-3/assets/125190958/f55b973c-113e-4b0a-ae13-fe170ee02de4">



### Update /etc/fstab in this format using your own UUID and rememeber to remove the leading and ending quotes.

### Test the configuration and reload the daemon

```
sudo mount -a
sudo systemctl daemon-reload
```

### Verify your setup by running df -h, output must look like this:


```
df -h 
```

<img width="444" alt="image" src="https://github.com/Nosa213/Devops_Project-3/assets/125190958/f143cbb3-5013-42d9-8875-f7f3e1672935">


## Step 2 — Prepare the Database Server

1* **Launch a second RedHat EC2 instance that will have a role – ‘DB Server’**

2* **Create and Attach all three volumes one by one to your DB Server EC2 instance**

3* **Open MobaXterm and connect Ec2 instances using public IP Address and begin configuration**


```
df -h
```
<img width="407" alt="image" src="https://github.com/Nosa213/Devops_Project-3/assets/125190958/8e245ea8-bdfa-4e33-b698-28d7e52d8903">


* **We need to create a single partition on each of the 3 disks we added**

```
sudo gdisk /dev/xvdf
sudo gdisk /dev/xvdg
sudo gdisk /dev/xvdh
```

<img width="485" alt="image" src="https://github.com/Nosa213/Devops_Project-3/assets/125190958/a8ff0ee6-c230-46e3-a4e6-f3cac0afcf3e">

<img width="485" alt="image" src="https://github.com/Nosa213/Devops_Project-3/assets/125190958/70e2424d-8dac-4bdb-a24c-b5005dae1fc3">



<img width="538" alt="image" src="https://github.com/Nosa213/Devops_Project-3/assets/125190958/47e10ffc-8fe2-4fca-a703-a2246fec8c9d">



* **We will use the command below to view the newly configured partition on each of the 3 disks**


```
sudo lsblk
```

<img width="403" alt="image" src="https://github.com/Nosa213/Devops_Project-3/assets/125190958/a0b8de6a-67d7-4eae-811f-3094329724f9">


* **We use this command to check for available storage for Logical Volume Manager (LVM)**


```
sudo lvmdiskscan
```

<img width="388" alt="image" src="https://github.com/Nosa213/Devops_Project-3/assets/125190958/16d0b83a-cdb7-4b4b-87ac-282012c69e88">

* **Use pvcreate utility to mark each of 3 disks as physical volumes (PVs) to be used by LVM**


```
sudo pvcreate /dev/xvdf1
sudo pvcreate /dev/xvdg1
sudo pvcreate /dev/xvdh1
```


<img width="362" alt="image" src="https://github.com/Nosa213/Devops_Project-3/assets/125190958/f76f3383-6495-4ed7-b22a-253e9e9efceb">


* **Verify that your Physical volume has been created successfully by running**


```
sudo pvs
```

<img width="305" alt="image" src="https://github.com/Nosa213/Devops_Project-3/assets/125190958/f16c2f30-c73d-4b51-a431-fa9bec028655">


* **Use vgcreate utility to add all 3 PVs to a volume group (VG). Name the VG database-vg**


```
sudo vgcreate vg-database /dev/xvdh1 /dev/xvdg1 /dev/xvdf1
```


<img width="540" alt="image" src="https://github.com/Nosa213/Devops_Project-3/assets/125190958/848aa4eb-7d47-4c99-92be-13e92a5745b6">



* **Verify that your VG has been created successfully by running**


```
sudo vgs
```

<img width="323" alt="image" src="https://github.com/Nosa213/Devops_Project-3/assets/125190958/ab126b4b-443b-479b-883e-7a061ef26286">


* **Use lvcreate utility to create 2 logical volumes. apps-lv (Use half of the PV size), and logs-lv Use the remaining space of the PV size. NOTE: apps-lv will be used to store data for the Website while, logs-lv will be used to store data for logs.**


```
sudo lvcreate -n db-lv -L 20G vg-database
```

<img width="441" alt="image" src="https://github.com/Nosa213/Devops_Project-3/assets/125190958/f8685954-e7cb-436f-acfa-4bb4fafbdd4f">


* **Verify that your Logical Volume has been created successfully**

```
sudo lvs
```

<img width="491" alt="image" src="https://github.com/Nosa213/Devops_Project-3/assets/125190958/4aee2308-f993-4da7-8154-527302b2f290">

* **Verify the entire setup**


<img width="454" alt="image" src="https://github.com/Nosa213/Devops_Project-3/assets/125190958/e09bc931-09a4-4c01-aaa5-e13d9d7df1c9">


* **Use mkfs.ext4 to format the logical volumes with ext4 filesystem**

```
sudo mkfs -t ext4 /dev/vg-database/db-lv
```

<img width="557" alt="image" src="https://github.com/Nosa213/Devops_Project-3/assets/125190958/5fa78b78-97f9-4640-93dd-e28d0f63f569">


* **We need to create /db directory to store our database files**

```
sudo mkdir /db
```


* **We need to create a logical volume**

```
sudo mkfs.ext4 /dev/vg-database/db-lv
```

<img width="502" alt="image" src="https://github.com/Nosa213/Devops_Project-3/assets/125190958/f5d1bb42-bc35-40d0-a3b8-97ad45164c2b">



* **We need to Mount /db on db-lv logical volume**


```
sudo mount /dev/vg-database/db-lv /db
df -h
```
<img width="541" alt="image" src="https://github.com/Nosa213/Devops_Project-3/assets/125190958/472a63f1-eb07-44a8-89b4-732c8a8b0347">

### Update /etc/fstab file so that the mount configuration will persist after restart of the server.


* **The UUID of the device will be used to update the /etc/fstab file;**

```
sudo blkid
```

<img width="545" alt="image" src="https://github.com/Nosa213/Devops_Project-3/assets/125190958/cf3b46ba-d0b9-4f54-9af9-0fd35e3b6ee4">

```
sudo vi /etc/fstab
```

### Update /etc/fstab in this format using your own UUID and rememeber to remove the leading and ending quotes.

<img width="491" alt="image" src="https://github.com/Nosa213/Devops_Project-3/assets/125190958/a4c59734-03ea-4f2f-bcb7-65c6e3833c1d">

### Test the configuration and reload the daemon

```
sudo mount -a
sudo systemctl daemon-reload
```

### Verify your setup by running df -h, output must look like this:


```
df -h 
```

<img width="449" alt="image" src="https://github.com/Nosa213/Devops_Project-3/assets/125190958/153738b6-91d1-4dfd-96e3-ec051476770b">


* **We need to backup all the files in the log directory /var/log into /home/recovery/logs (This is required before mounting the file system)**


```
sudo rsync -r /var/log/ /home/recovery/logs/
```


* **We need to Mount /var/log on logs-lv logical volume**


```
sudo mount /dev/dbdata-vg/logs-lv /var/log
```


* **We need to restore log files back into /var/log directory.**


```
sudo cp -r /home/recovery/logs/.* /var/log
```


* **We need to update the /etc/fstab file so that the mount configuration will persist upon restart of the server.**



## Step 3 — Install WordPress on your Web Server EC2


### Install Apache server on Ubuntu
```
sudo apt install apache2
```
<img width="674" alt="image" src="https://github.com/Nosa213/Devops_Project-3/assets/125190958/7866ea0f-321a-4a07-a1ea-2579c83b1631">


## Next Install php runtime and php mysql connector

```
sudo apt install php libapache2-mod-php php-mysql
```


## Install MySQL server
sudo apt install mysql-server 

## Login to MySQL server
sudo mysql -u root

## Change authentication plugin to mysql_native_password (change the password to something strong)
ALTER USER 'root'@'localhost' IDENTIFIED WITH mysql_native_password by 'Testpassword@123';

## Create a new database user for wordpress (change the password to something strong)
CREATE USER 'wp_user'@localhost IDENTIFIED BY 'Testpassword@123';

## Create a database for wordpress
CREATE DATABASE wp;

## Grant all privilges on the database 'wp' to the newly created user
GRANT ALL PRIVILEGES ON wp.* TO 'wp_user'@localhost;

**You should see something like this.**

<img width="572" alt="image" src="https://github.com/Nosa213/Devops_Project-3/assets/125190958/b0b26291-f56c-449d-b94a-e3d0b5683f3a">

## Install Wordpress
cd into the tmp directory
copy the link download link from the wordpress webpage and paste it.
```
wget https://wordpress.org/latest.zip
```


<img width="1256" alt="image" src="https://github.com/Nosa213/Devops_Project-3/assets/125190958/e1eb777a-547e-46d4-a975-647b4f191ca4">

<img width="564" alt="image" src="https://github.com/Nosa213/Devops_Project-3/assets/125190958/1884a8f3-4863-4aca-9bd1-271e1013e83d">


**Next** unzip the file

```
ls
```

```
zip -xvf latest.zip
```

Type ls again and you will find a new folder **wordpress**

<img width="263" alt="image" src="https://github.com/Nosa213/Devops_Project-3/assets/125190958/89f911c2-437c-4c87-9ab8-ccd0d96c0bbd">

**Next** Move the folder to the document root of apache


<img width="460" alt="Screenshot 2023-06-12 100227" src="https://github.com/Nosa213/Devops_Project-3/assets/125190958/fc1a52d3-4236-41a6-b0d9-51535c9a4f1b">


**Next** Go back to your browser and add /wordpress to your IP address and click enter

<img width="628" alt="image" src="https://github.com/Nosa213/Devops_Project-3/assets/125190958/4eaf8995-ea43-410b-9456-883dac080bda">

<img width="1007" alt="image" src="https://github.com/Nosa213/Devops_Project-3/assets/125190958/94d5434a-d9d9-4baa-9db7-470b2adcfd4d">

**Next** click on **let's go** and fill in the details


<img width="944" alt="Screenshot 2023-06-12 100608" src="https://github.com/Nosa213/Devops_Project-3/assets/125190958/ae8a7cda-e73d-46b6-99bf-4bc9615b7fc6">

Unable to write to wp-config.php file.

You can create the wp-config.php file manually and paste the following text into it.

**Configuration rules for wp-config.php**: 

<img width="959" alt="image" src="https://github.com/Nosa213/Devops_Project-3/assets/125190958/42d75ad9-230e-467e-8650-c92da4367015">

**Next cd into wordpress**
```
/var/www/html$ cd wordpress/
/var/www/html/wordpress$ vi wp-config.php
```

<img width="419" alt="image" src="https://github.com/Nosa213/Devops_Project-3/assets/125190958/58aa8206-daad-4c0d-9fd0-0796dabfebd3">

**copy and paste**

<img width="488" alt="image" src="https://github.com/Nosa213/Devops_Project-3/assets/125190958/cf323fed-341c-45f9-ac7a-d6c3f66716c3">

**save and exit**

**Next** input your information and click on Install WordPress below

<img width="588" alt="image" src="https://github.com/Nosa213/Devops_Project-3/assets/125190958/9869161a-72f2-4dee-ae59-fda659ea4cdd">


**CONGRATULATIONS WORDPRESS HAS BEEN INSTALLED**

<img width="612" alt="image" src="https://github.com/Nosa213/Devops_Project-3/assets/125190958/6baa28ed-d837-4222-bd55-8484f8af4e62">





























