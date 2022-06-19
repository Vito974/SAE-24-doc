# Configurer Apache
Documentation sur le serveur web déployé 

## Instalation

En cas de souscis technique il peut etre necessaire de réinstaller httpd avec la commande suivante :

```sh
sudo yum install httpd
```


## Ouverture des ports 
Après installation il faut créer une règle de parfeu avec SELinux pour autoriser la connexion 


```zsh
firewall-cmd --permanent --zone=public --add-service=http 
firewall-cmd --permanent --zone=public --add-service=https
firewall-cmd --reload
```



## Auto générer le certificat 
Pour auto générer le certificat https utiliser la commande openssl

```bash
sudo openssl req -x509 -nodes -days 365 -newkey rsa:2048 -keyout /etc/ssl/private/httpd-selfsigned.key -out /etc/ssl/certs/httpd-selfsigned.crt
```
## Configurer le chiffrement SSl 
Pour activer https il faut activer le module ssl

```bash
sudo a2enmod ssl
```
Redémarer apache

```bash
sudo systemctl restart httpd
```

Modifier la configuration de apache pour utiliser https 

```bash
sudo nano /etc/httpd/conf.d/ssl.conf 
```

et modifier ces lignes 

```bash
<VirtualHost *:443>
   ServerName your_domain_or_ip
   DocumentRoot /var/www/your_domain_or_ip

   SSLEngine on
   SSLCertificateFile /etc/ssl/certs/httpd-selfsigned.crt
   SSLCertificateKeyFile /etc/ssl/private/httpd-selfsigned.key
</VirtualHost>
```

