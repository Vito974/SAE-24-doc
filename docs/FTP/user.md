# Ajouter un utilisateur

# Monter les dossiers
Une fois les utlisateur créer sur le systéme il faut monter leur dossier dans le home des dirigeant et monter les partages commun et du département

Ouvrer le fichier fstab
```bash
sudo nano /etc/fstab
```

Rajouter les lignes suivantes à la fin du fichier 
 
```bash linenums="1" title="/etc/fstab"
/home/centos/partage /home/utilisateur/ftp/partage auto bind,defaults 0 0
/home/centos/partage_departementX /home/utilisateur/ftp/partage_departementX auto bind,defaults 0 0
/home/utilisateur/perso /home/dirigeant1/ftp/perso_employee/perso_utilisateur auto bind,defaults 0 0
/home/utilisateur/perso /home/dirigeant2/ftp/perso_employee/perso_utilisateur auto bind,defaults 0 0
/home/utilisateur/perso /home/dirigeant3/ftp/perso_employee/perso_utilisateur auto bind,defaults 0 0
/home/utilisateur/perso /home/dirigeant4/ftp/perso_employee/perso_utilisateur auto bind,defaults 0 0
/home/utilisateur/perso /home/dirigeant5/ftp/perso_employee/perso_utilisateur auto bind,defaults 0 0
```


# Ajouter l'utilsateur dans le fichier de configuration

Ouvrer le fichier user_list

```bash
sudo nano /etc/vsftp.user_list
```

A la fin de ce fichier rajouter les utilisateurs crées
