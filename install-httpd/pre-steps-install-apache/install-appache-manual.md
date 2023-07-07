### install apache server on ubuntu
1. install apache2
```
sudo apt install apache2
```
```
sudo systemctl restart apache2
```
```
sudo systemctl reload apache2
```
```
sudo systemctl enable apache2
```
### post install configuration 
1. copy html files to source path
2. to copy the complete path
```
cp -r source-path destination-path
```
example
```
cp  -r website/ /var/www/shopping/
```
3. to copy all the files
```
cp source-path/* destination-path/
```
example
```
cp website/* /var/www/shopping/
```
### setting the virtual hosts
1. first we have to create directory for your own website
```
mkdir /var/www/directoryname
```
example
```
mkdir /var/www/shopping
```
2. assign ownership to the own directory
```
sudo chown -R $USER:$USER /var/www/directoryname
```
example
```
sudo chown -R ans_admin:ans_admin /var/www/shopping
```
3. give permission 
```
sudo chmod -R 755 /var/www/directoryname
```
example
```
sudo chmod -R 755 /var/www/shopping
```
4. create a sample index.html
```
sudo vim /var/www/directoryname/index.html
```
example
```
sudo vim /var/www/shopping/index.html
```
5. to conf file
```
sudo vim /etc/apache2/sites-available/directoryname.conf
```
example
```
sudo vim /etc/apache2/sites-available/directoryname.conf
```
6. we have add this contact
```
<VirtualHost *:80>
    ServerAdmin webmaster@localhost
    ServerName directoryname
    ServerAlias www.directoryname
    DocumentRoot /var/www/directoryname
    ErrorLog ${APACHE_LOG_DIR}/error.log
    CustomLog ${APACHE_LOG_DIR}/access.log combined
</VirtualHost>
```
example
```
<VirtualHost *:80>
    ServerAdmin webmaster@localhost
    ServerName shopping
    ServerAlias www.shopping
    DocumentRoot /var/www/shopping
    ErrorLog ${APACHE_LOG_DIR}/error.log
    CustomLog ${APACHE_LOG_DIR}/access.log combined
</VirtualHost>
```
7. enable the file with the a2ensite too
```
sudo a2ensite directoryname.conf
```
example
```
sudo a2ensite shopping.conf
```
8. Disable the default site
```
sudo a2dissite 000-default.conf
```
9. let’s test for configuration errors
```
sudo apache2ctl configtest
```
10. output
```
 syntax=ok
```
11. we have to add 
```
/etc/apache2/apache2.conf
ServerName 127.0.0.1
```
12. restart the apaache2
1.  backup appche html path and code
```
```
### cronjob
1. To create cronjob
```
crontab -e 
```
2. To get run the output for everyday or months
```
min hours date month year comand to execute
```
### tar commands
1. To create tar file
```
tar -czf fliename.tar.gz filename
```
Example
```
tar -czf web-deployment.tar web-deployment
```
1. To open tar file
```
tar -xzf tarfile
```
Example
```
tar -xzf web-deployment.tar
```

