sudo mkdir /var/lib/jenkins
sudo mkdir /var/lib/jenkins/backup
sudo mkdir /var/lib/jenkins/backup/www
sudo mkdir /var/lib/jenkins/backup/conf
sudo mkdir /var/lib/jenkins/backup/mysql
sudo chown -R jenkins:jenkins /var/lib/jenkins
mysql -uroot -e "GRANT ALL PRIVILEGES ON *.* TO 'aaa'@'localhost' IDENTIFIED BY '1' WITH GRANT OPTION"

# Dump MariaDB DB and change name from last to date
sudo mv /var/lib/jenkins/backup/mysql/$(ls -all /var/lib/jenkins/backup/mysql/ | grep aaa_db | awk '{print $9}' | grep last) /var/lib/jenkins/backup/mysql/$(ls -all /var/lib/jenkins/backup/mysql/ | grep aaa_db | awk '{print $9}' | grep last | awk -F. '{print $2}').aaa_db.gz
mysqldump -u aaa -p1 aaa_db |gzip > /var/lib/jenkins/backup/mysql/last.$(date +%y-%m-%d-%H-%M).aaa_db.gz

#Backup www, config nginx and php
sudo mv /var/lib/jenkins/backup/www/$(ls -all /var/lib/jenkins/backup/www/ | grep aaa.lala | awk '{print $9}' | grep last) /var/lib/jenkins/backup/www/$(ls -all /var/lib/jenkins/backup/www/ | grep aaa.lala | awk '{print $9}' | grep last | awk -F. '{print $2}').aaa.lala.tar.gz
sudo tar -cvzf /var/lib/jenkins/backup/www/last.$(date +%y-%m-%d-%H-%M).aaa.lala.tar.gz /var/www/aaa.lala/

sudo mv /var/lib/jenkins/backup/conf/$(ls -all /var/lib/jenkins/backup/conf/ | grep conf.avai | awk '{print $9}' | grep last) /var/lib/jenkins/backup/conf/$(ls -all /var/lib/jenkins/backup/conf/ | grep conf.avai | awk '{print $9}' | grep last | awk -F. '{print $2}').conf.avai.tar.gz
sudo tar -cvzf /var/lib/jenkins/backup/conf/last.$(date +%y-%m-%d-%H-%M).conf_avai.tar.gz /etc/nginx/sites-available/

sudo mv /var/lib/jenkins/backup/conf/$(ls -all /var/lib/jenkins/backup/conf/ | grep conf_nginx | awk '{print $9}' | grep last) /var/lib/jenkins/backup/conf/$(ls -all /var/lib/jenkins/backup/conf/ | grep conf_nginx | awk '{print $9}' | grep last | awk -F. '{print $2}').conf_nginx.conf.tar.gz
sudo tar -cvzf /var/lib/jenkins/backup/conf/last.$(date +%y-%m-%d-%H-%M).conf_nginx.conf.tar.gz /etc/nginx/nginx.conf

sudo mv /var/lib/jenkins/backup/conf/$(ls -all /var/lib/jenkins/backup/conf/ | grep conf_php | awk '{print $9}' | grep last)  /var/lib/jenkins/backup/conf/$(ls -all /var/lib/jenkins/backup/conf/ | grep conf_php | awk '{print $9}' | grep last | awk -F. '{print $2}').conf_php.conf.tar.gz
sudo tar -cvzf /var/lib/jenkins/backup/conf/last.$(date +%y-%m-%d-%H-%M).conf_php.conf.tar.gz /etc/php-fpm.d/
