# Instructions
---


## Install craft files

1. Create a folder named ```code```

2. Download the latest craft and extract it to the ```code``` directory you just created
   [v3](https://craftcms.com/latest-v3.tar.gz)
   [v4](https://craftcms.com/latest-v4.tar.gz)

3. Do a ```sudo chown -R www-data code``` to change the permission so that nginx and php can access the files

## Change config files
1. Change the ```site.conf``` to what your site is called, something like ```yoursite.conf```
2. Inside the ```.conf```: 
```nginx
server_name YourSiteHere.com; #Change this to whatever your site is called

server_tokens off;

root /code/web;

index index.html index.htm index.php;

charset utf-8; 
```

```nginx
access_log off;

error_log /var/log/nginx/YourSiteHere.com-error.log error; #Rename to your site
```

```nginx

fastcgi_param HTTP_PROXY "";

fastcgi_param HTTP_HOST YourSiteHere.com; # Change this
```


3. Inside the ```docker-compose.yml``` change parameters to fit your needs 
 

4. Open up ```code/.env``` and apply the database settings from the ```docker-compose.yml``` to match. :warning: Make sure that CRAFT_DB_SERVER is set to ```db```
```
CRAFT_DB_DRIVER=mysql
CRAFT_DB_SERVER=db
CRAFT_DB_PORT=3306
CRAFT_DB_DATABASE=craft
CRAFT_DB_USER=craftuser
CRAFT_DB_PASSWORD=craft
```


5. You also have to make a Security Key for the craft instance. You can do this in tons of ways, but one of them is by running the command: ```openssl rand -hex 16``` and take the output and put it in ```CRAFT_SECURITY_KEY=```


## Start the container
1. ```docker compose up -d```

2. Now navigate to ```yourSite.com/admin/``` and complete the installation
