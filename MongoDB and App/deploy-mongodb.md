



#!/bin/bash - you need to copy that as code 

sudo apt update -y

sudo apt upgrade -y

# Add the GPG key - GNU Privacy Guard, makes sure pacakage is from Mongodb

# -fsSL fail silently, silent mode, show errors, follow redirects

curl -fsSL https://www.mongodb.org/static/pgp/server-7.0.asc | \

   sudo gpg -o /usr/share/keyrings/mongodb-server-7.0.gpg \

   --dearmor


   echo "deb [ arch=amd64,arm64 signed-by=/usr/share/keyrings/mongodb-server-7.0.gpg ] https://repo.mongodb.org/apt/ubuntu jammy/mongodb-org/7.0 multiverse" | sudo tee /etc/apt/sources.list.d/mongodb-org-7.0.list



   sudo apt update -y


   # Install Mongodb

sudo apt install -y mongodb-org=7.0.6 mongodb-org-database=7.0.6 mongodb-org-server=7.0.6 mongodb-mongosh=2.1.5 mongodb-org-mongos=7.0.6 mongodb-org-tools=7.0.6




sudo systemctl status mongod


ls 

cd /

ls

cd /etc

/etc

ls


sudo nano mongod.conf

#  the bindIp change from 127.0.0.1 change to 0.0.0.0

cd

sudo systemctl start mongod

# check for error

sudo systemctl status  mongod

### if error do  look for 9 code =exited, status=14)

#try this to fix it 


# Add the GPG key - GNU Privacy Guard, makes sure pacakage is from Mongodb

# -fsSL fail silently, silent mode, show errors, follow redirects

curl -fsSL https://www.mongodb.org/static/pgp/server-7.0.asc | \

   sudo gpg -o /usr/share/keyrings/mongodb-server-7.0.gpg \

   --dearmor


   # Source - https://stackoverflow.com/a/66107451

# Posted by Arman, modified by community. See post 'Timeline' for change history

# Retrieved 2026-03-12, License - CC BY-SA 4.0

 

sudo chown -R mongodb:mongodb /var/lib/mongodb

sudo chown mongodb:mongodb /tmp/mongodb-27017.sock    

sudo service mongod restart

# this should fix it 

#go back on app isntacne termonaterminal 

pm2 kill


##
 export DB_HOST=mongodb://DB-IP-108.131.12.33:27017 # lecture ip
 
 printenv DB_HOST

 cd app

sudo npm install

node seeds/seed.js

pm2 start app.js




#### check whats on your ip adress, it should look like a blog style page with headings and body of text 










