# 🚀Key Features

##### Creates a security group for the AWS instance with custom TCP rules, HTTP rule, and SSH rule

##### Launches a new instance of CentOS or Amazon Linux

##### Installs Apache as the web server

##### Creates directories for each website

##### Creates an index.html file and copies it to each website directory

##### Configures the Apache server to listen on multiple ports

##### Configures DNS settings to point to the instance IP address

# Prerequisites

An AWS account with a CentOS or Amazon Linux instance

A Windows terminal with SSH client installed
 
### Step 1: Create a Security Group for the AWS Instance
#### Create a new security group for your AWS instance and add the following rules:

Inbound:
Custom TCP rule: port 81-83

HTTP rule: port 80

SSH rule: port 22

![Screenshot 2024-09-26 231958](https://github.com/user-attachments/assets/90ef9690-8905-40e4-93e2-1ceea812d038)


Outbound:
SSH rule: port 22

All traffic: allow all traffic

![Screenshot 2024-09-26 232058](https://github.com/user-attachments/assets/05ff500a-e4cc-4b9d-898f-3c0abeab32d2)


Security Group Rules



### Step 2: Launch the Instance
#### Launch a new instance of CentOS or Amazon Linux.

![Screenshot 2024-09-26 232659](https://github.com/user-attachments/assets/b6402538-b6bf-49ac-b73d-2693d958c7b7)

Launch Instance

### Step 3: Connect to the Instance using SSH
#### Connect to the instance using SSH from your Windows terminal.

```bash
ssh -i "path/to/your/pem/file" ec2-user@instance-ip-address
```
![Screenshot 2024-09-26 232729](https://github.com/user-attachments/assets/f86fff95-1951-4768-8b58-6894aefedff9)


### Step 4: Update the Instance
#### Update the instance to ensure you have the latest packages

```bash 
sudo yum update -y
```
![Screenshot 2024-09-26 232824](https://github.com/user-attachments/assets/3d84ce74-89c1-4a7b-9946-cd643eb48a6a)


### Step 5: Install the HTTP Server
#### Install the HTTP server (Apache) on the instance.

```bash
sudo yum install httpd -y
```

![Screenshot 2024-09-26 232849](https://github.com/user-attachments/assets/e1c9c2ea-840e-4c4f-9105-c4ec75232305)


### Step 6: Create Directories for Each Website
#### Create directories for each website.

````bash
sudo mkdir -p /var/www/web1 /var/www/web2 /var/www/web3
````
![Screenshot 2024-09-26 233444](https://github.com/user-attachments/assets/a8fd1f62-738c-4161-9ffc-3fc7871b0fd8)


### Step 7: Create an index.html File in the Home Directory
#### Create an index.html file in the home directory.

```bash
sudo nano index.html
```

![Screenshot 2024-09-26 233941](https://github.com/user-attachments/assets/f2e2fcbc-89a6-4a12-b657-28f10a96f8c7)


### Step 8: Copy the index.html File to Each Website Directory
#### Copy the index.html file to each website directory.

```bash 
sudo cp -r ~/index.html /var/www/web1 && sudo cp -r ~/index.html /var/www/web2 && sudo cp -r ~/index.html /var/www/web3
```

![Screenshot 2024-09-26 233941](https://github.com/user-attachments/assets/7bf2a444-a121-4ccc-9a5e-79b583e811a6)


### Step 9: Change Ownership of the Website Directories
#### Change ownership of the website directories to the Apache user.

```bash 
sudo chown -R apache:apache /var/www/web1 /var/www/web2 /var/www/web3
```

![Screenshot 2024-09-27 005426](https://github.com/user-attachments/assets/99353f1e-b30b-45b0-a4ca-39a46170ab5a)


### Step 10: Configure the HTTP Server
#### Configure the HTTP server by editing the httpd.conf file.

```bash 
sudo nano /etc/httpd/conf/httpd.conf
```


##### Add the following content to the file:
```bash 
Listen 81
Listen 82
Listen 83
```
![Screenshot 2024-09-26 233231](https://github.com/user-attachments/assets/e631b6bc-ed3d-4954-9296-cbbc80510da5)


```bash 
<VirtualHost *:81>
    DocumentRoot /var/www/web1
</VirtualHost>

<VirtualHost *:82>
    DocumentRoot /var/www/web2
</VirtualHost>

<VirtualHost *:83>
    DocumentRoot /var/www/web3
</VirtualHost>
```
![Screenshot 2024-09-27 005254](https://github.com/user-attachments/assets/1b0c2c1d-0da0-46c4-a1f5-fdf76f7a19d0)

### Step 11: Start the httpd server 

```bash
sudo systemctl start httpd
```

### Step 12: Configure the DNS Settings
#### Configure the DNS settings to point to the instance IP address.

![Screenshot 2024-09-27 010126](https://github.com/user-attachments/assets/1a463009-659f-4e15-8c14-0e601b35c63a)

DNS Settings

Note: Replace the ServerName directives with your own domain names or IP addresses.

### Step 13: Restart the HTTP server

```bash 
sudo service httpd restart
```
# That's it! 🎉 You now have three websites hosted on a single AWS instance with the help of ports 

![Screenshot 2024-09-27 010143](https://github.com/user-attachments/assets/5c094d06-d7d1-492c-be89-ab5917d5e706)

![Screenshot 2024-09-27 010152](https://github.com/user-attachments/assets/71548e4a-2ecf-4574-971d-fa2b41ae5a74)

![Screenshot 2024-09-27 010159](https://github.com/user-attachments/assets/3c419229-4969-4c7f-aa62-61992b5eb093)



