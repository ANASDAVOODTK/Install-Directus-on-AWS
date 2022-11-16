# Install-Directus-on-AWS

## 1 ) Log in to your server as the default ubuntu user:   

> 💡 TIP

> In the future, each time you log into your EC2 server, you will need to add the path to the .pem file and add the IP address for your EC2 instance at the end, e.g. ssh -i ~/.ssh/ec2-strapi-key-pair.pem ubuntu@1.2.3.4.

ssh -i ~/.ssh/ec2-strapi-key-pair.pem ubuntu@1.2.3.4

Welcome to Ubuntu 22.04.2 LTS (GNU/Linux 4.15.0-1032-aws x86_64)

...

To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

`ubuntu@ip-1.2.3.4:~$`

## 2) Install Node.js with npm:
  The following steps will install Node.js onto your EC2 server.
  
```
cd ~
curl -sL https://deb.nodesource.com/setup_14.x | sudo -E bash -
...
sudo apt-get install nodejs
...
node -v && npm -v
```

## 3) Create and change npm's default directory.

The following steps are based on how to resolve access permissions from npmjs.com (opens new window):

Create a .npm-global directory and set the path to this directory for node_modules
```
cd ~
mkdir ~/.npm-global
npm config set prefix '~/.npm-global'
```
    
Create (or modify) a ~/.profile file:
```
sudo nano ~/.profile
```
    
Add these lines at the bottom of the ~/.profile file.

set PATH so global node modules install without permission issues
```
export PATH=~/.npm-global/bin:$PATH
 ```
    
Lastly, update your system variables:
```
source ~/.profile
```
# 4. Installation


Run the following command in your terminal and follow the prompts.


```
npm init directus-project example-project
```
Choose SQLite from the list. Use up/down arrow keys to select the SQL type.

```
? Choose your database client SQLite
```
After that a file path for data.db, your database, will be suggested. Hit the enter key to stick with the default path.

```
? Database File Path: <file-path>/example-project/data.db
```
Next you'll set your username/email and password.

```
Create your first admin user:
? Email: admin@example.com
? Password: ********
```
After that, you're all set!

```
Your project has been created at <file-path>/example-project.
The configuration can be found in <file-path>/example-project/.env
```
Once the installation is complete, you can start Directus by navigating to your project folder (in this case example-project) and running:

```
npx directus start
```
After that, you will see this message:

```
✨ Server started at http://localhost:8055
```

 

