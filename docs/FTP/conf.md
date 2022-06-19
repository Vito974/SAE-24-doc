# Configuration de base vsftpd
## Instalation
Installer vsftpd depuis yum 
```sh
sudo yum install vsftpd
```

Démarer vsftpd

```sh
sudo systemctl start vsftpd
```
```sh
sudo systemctl enable vsftpd
```

## Désactivation de l'utilisateur anonyme
Ouvrer le fichier de configuration de vsftpd 
```sh
sudo nano /etc/vsftpd/vsftpd.con
```
Ajouter les lignes suivantes 
```bash
#Allow anonymous FTP? (Beware - allowed by default if you comment this out).
anonymous_enable=NO
```

## Activer FTPS
Créer le certificat avec la commande openssl

```bash
openssl req -x509 -nodes -days 365 -newkey rsa:2048 -keyout /etc/vsftpd/vsftpd.pem -out /etc/vsftpd/vsftpd.pem
```
Puis dans  /etc/vsftpd/vsftpd.conf ajouter les lignes suivantes 

```bash linenums="1"
rsa_cert_file=/etc/vsftpd/vsftpd.pem
rsa_private_key_file=/etc/vsftpd/vsftpd.pem
ssl_enable=YES
```


## Activer le mode passif 
Ouvrer le fichier de configuration de vsftpd 
```sh
sudo nano /etc/vsftpd/vsftpd.con
```

Puis dans  /etc/vsftpd/vsftpd.conf ajouter les lignes suivantes 

```bash linenums="1"
pasv_enable=YES
pasv_min_port=30000
pasv_max_port=31000
```
