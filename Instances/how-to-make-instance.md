# Sign in to AWS
1. Go to the AWS Management Console
2. Log in with your AWS account.
3. In the search bar, type EC2 and open Amazon EC2.

# Start Launching an Instance
1. Click “Launch Instance”.
2. Give your instance a name for example "jonathan-instance-2026"




# Choose the Ubuntu Image
## Application and OS Images (AMI)
Select Ubuntu Server 22.04 LTS or the latest Ubuntu LTS.

This AMI is provided by Canonical, the company behind Ubuntu.

# Choose Instance Type
For testing or small projects choose:

- t2.micro (Free Tier eligible)

It has:
- 1 vCPU
- 1 GB RAM

# Create a Key Pair (for SSH login)
1. Click Create new key pair
2. Name it  for example i did was jonathan-key-pair-26.pem
3. Choose `.pem` format for mine for example 
I have kept the same setting as it showns so i chose. RSA and undernith i chosen .pem


"This is the keypair screen" 
![this is keypair](../images/jonathan-key-pair-26.png)




4. Download the file (keep it safe) once downloaded put in a revanet folder, i would personally for this route C:\Users\jonno\.ssh but coulse instead on jonno put your name it and if you have not got a .ssh folder you can always make one 

"file path of my ssh folder" 

![ssh folder path ](../images/ssh-folder-path.png)

 # Temrinate instace

where is says "action" (next to connect)


This key is required to connect to your server. you can use this keypair for things such as making new instance, just scroll down where it says key paired required then looks for yours or if you just type your keypair in the search box then it gradually will show for you to choose 

# Configure Network / Security
## Network Settings
Allow these rules in the security group:

``
SSH (22) → allow only your IP

HTTP (80) → allow 0.0.0.0/0 if it’s a public website

HTTPS (443) → allow 0.0.0.0/0

i also used  as i am using SSH

SSH open to 0.0.0.0/0
``
# configure security 

to make my security i made a security called "jonathana-security" just for an example . i also put a decription about it " this is security" and also made a security group rule.

the first one i made was i want to use port 80 so i type thst in the " port range box". As i am using SHH, on the "souce" box i chosen 0.0.0/0. 

"this is my security key with ports i have chosen "

"This is what a public Ip address looks like "
![tthis is my securit  ](../images/security-key.png)
# Configure Storage
Default is usually enough: this is 8 GB gp3 storage (works fine for Ubuntu)


# Launch Instance
Click **Launch Instance**.

AWS will start the server in about **10–30 seconds**.

# Connect to the Instance
After the instance is running:

1. Go to **Instances**
2. Select your instance
3. Click **Connect**
4. Use SSH command like:


# What happens once you have an instance?
You can deploy things such as apps, databases, and other things
Just say we have done them already so how would we know if they are working ?

1.	Once you instace  and pressed connect to, it you need to go back on the instace page by clicking on top of the left of the page where is says “ EC2,Instances,i-00df1eb46fd89044c, Connect to instance” click on “i-00df1eb46fd89044c”
2.	Once you have done that you need to look for something which says “Public IPv4 address” copy that ip address and there you go!. You may sometimes have working problems this because at the start of the ip address “HTTPS” just get rid of the “S”

"This is what a public Ip address looks like "
![this public Ip address  ](../images/public-ip.png)


you will need to do tese steps again to deloy different thigns but can use same key air if you like but may or can make a diffeernt secutiy key if you need different ports.
 
# terminate instace

where is says "actions" nect to ( connect button" scroll down and simply choose "Terminate instance")


