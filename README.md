# Instructions
---


## Install craft files

1. 
   Create a folder named ```code```

2. 
   Download the latest craft and extract it to the ```code``` directory you just created
   [v3](https://craftcms.com/latest-v3.tar.gz)
   [v4](https://craftcms.com/latest-v4.tar.gz)

3. 
   Do a ```sudo chown -R www-data code``` to change the permission so that nginx and php can access the files

## Change config files
1. 
   Change the ```site.conf``` to what your site is called, something like ```yoursite.conf```
2. 
   Inside the ```.conf```: 
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


3. 
   Inside the ```docker-compose.yml``` change parameters to fit your needs 
 