# PhpNuxbill-Ubuntu-20.04
PhpNuxbill di Ubuntu Server 20.04


## Install For Ubuntu Server 20.04

Masuk Ke SUPER USER
```bash
sudo su
```
Update sistem
```bash
sudo apt update
```
Install Plugin Php Mysql-Server Mysql-Client
```bash
sudo apt  install php mysql-server mysql-client
```
Install Plugin Phpmyadmin
```bash
sudo apt install phpmyadmin
```

<br>

<h3>PopUp 1</h3>
<p>
  Jika Muncul Pop-Up "Configuring phpmyadmin" <br>
  "Web Server to reconfigure automatically" <br>
  Pilih <strong> Apache2 </strong>
</p>
<br>
<h3>PopUp 2</h3>
<p>
  Jika Muncul Pop-Up "Configuring phpmyadmin" <br>
  "Configure database for phpmyadmin with dbconfig-common?" <br>
  Pilih <strong> YES </strong>
</p>
<br>
<h3>PopUp 3</h3>
<p>
  Jika Muncul Pop-Up "Configuring phpmyadmin" <br>
  Isi Password ( Yang Mudah Di Pahami ) <br>
</p>
<br>

Instalasi Database
```bash
mysql -u root -p
```
```bash
create user 'arthasa'@'localhost'identified by'081212';
```
```bash
CREATE DATABASE phpnuxbill;
```
```bash
grant all on phpnuxbill.* to 'arthasa'@'localhost';
```
```bash
EXIT;
```
Install PHP dan beberapa ekstensi yang diperlukan
```bash
sudo apt install php libapache2-mod-php php-mysql php-xml php-mbstring php-zip php-curl mariadb-server -y
```
Navigasi ke direktori web root Apache
```bash
cd /var/www/
```
Clone PHPNuxBill 
```bash
sudo git clone https://github.com/hotspotbilling/phpnuxbill.git
```
Masuk Directory PhpNuxbill
```bash
cd phpnuxbill
```
Konfigurasi folder permission
```bash
sudo chown -R www-data:www-data /var/www/phpnuxbill 
sudo chmod -R 755 /var/www/phpnuxbill 
```
Masuk Ke Directory Host Apache2
```bash
cd /etc/apache2/sites-available/
```
konfigurasi virtual host baru untuk PHPNuxBill
```bash
sudo nano phpnuxbill.conf
```
Isi file, Lalu Save ( CTRL + X ) Ketik "Y" Enter.
```bash
<VirtualHost *:80>
    ServerAdmin admin@example.com
    DocumentRoot /var/www/phpnuxbill
    ServerName example.com
    <Directory /var/www/phpnuxbill/>
        Options Indexes FollowSymLinks
        AllowOverride All
        Require all granted
    </Directory>
    ErrorLog ${APACHE_LOG_DIR}/error.log
    CustomLog ${APACHE_LOG_DIR}/access.log combined
</VirtualHost>

```
Aktifkan virtual host dan mod rewrite
```bash
sudo a2ensite phpnuxbill.conf
sudo a2dissite 000-default.conf
sudo a2enmod rewrite
```
Restart Apache
```bash
sudo systemctl restart apache2
systemctl status apache2
```



## Donate
- [Saweria](https://saweria.co/arthasyarif)
- <img src="https://github.com/arthasa28/PhpNuxbill-Ubuntu-20.04/blob/master/qris.jpg?raw=true" alt="Deskripsi gambar" width="300" height="200"/>


