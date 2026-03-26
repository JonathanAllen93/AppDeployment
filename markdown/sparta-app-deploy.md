# sparta app depoloyment guide


### step 1: setting up


1. Log in to aws console with correct crediantials
2. navigae to the "ec2" service
3. click the "Launch istance" button

### step 2: create a Ec2 instance


fill out the presented form with the following values:

1. Name=" se-yourname-node20-sparta-app"

AMI= "ubuntu 24.04 LTS" (Long time serivce)

Instance type= "t3.mircro"

key pair= "se-your-key-pair.pem"

#### network settings

VCP- defualt
submet_ default
Enabale public IP adress=enebale

eable public ip address=enebalen

security gorup must have port 22(SSH) open port 80 open(HTTP) and port 300 (spart app)

vonfigure storgage = 8 GIB

advanched details s=none

whe doen and revied click "Lanuch Instance" ( i was in ireland)"


### Long in and run delpoy scrip

1. Open "instance summary" page- should look like a link




2. Click the "Connect" button

3. At the bottom of the connect page, copy the example SSH command provided

4. Open GitBash session

5. `cd` into your `.ssh` folder

6. Run the copied command to log in via SSH

7.Make sure to type "yes" when prompte

8. copy the contents of the following bash scrips


cd 

cd. ssh

``` bash
#!/bin/bash

# update packages

sudo apt update -y

 

# upgrade packages

sudo apt upgrade -y

 

# install git if it's not there

sudo apt install git -y

 

# get the app code

git clone https://github.com/LSF970/se-sparta-test-app.git

 

# install nginx

 

sudo apt install nginx -y

 

# restart nginx

sudo systemctl restart nginx

 

# enable --> makes the process a startup process

sudo systemctl enable nginx

 

# install curl

sudo apt install curl -y

 

# download nodejs 20.x

sudo bash -c "curl -fsSL https://deb.nodesource.com/setup_20.x | bash -"

 

# install nodejs 20

sudo apt install nodejs -y

 

# cd into repo

cd se-sparta-test-app

 

# cd into app folder

cd app

 

# npm install

sudo npm install

 

# start the app

npm start app.js
```

9. create a new file in your Ec2 instance ui
sing :

    1. ' sudo nanp app-deploy.shh

    2. pasete the script contents into this file

    10. same and close the file 

    1.  `Ctrl + X` to exit

    2.  `y` to save

    3.  `Enter` to overwrite current contents


    11. now run the cript with the command 

    - ' source app-deploy.shh
    
    - wait for the scrip th finish running

    -
. If it is successful you should see the message:

    1.  "Your app is ready and listening on port 3000"

14. Check your EC2 instance public IP with `:3000` on the end. You should see the Sparta App Homepag





![ssh folder path ](../images/spartaapp.png)
