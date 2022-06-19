# Configurer MariaDB
## Installation
Installer mariadb depuis yum 

```bash
sudo yum install mariadb-server
```
Démarer le service 


```bash
sudo systemctl start mariadb.service
```
Sécuriser l'installation 

```bash
sudo mysql_secure_installation
```
## Déployer la base de donné 

Créer un fichier vide d'extension .sql et copier coller les lignes suivantes 

```sql title="script.sql" linenums="1"
CREATE TABLE `Employe`(
    `id_employe` INT(10) UNSIGNED NOT NULL AUTO_INCREMENT PRIMARY KEY,
    `nom` CHAR(255) NOT NULL,
    `prenom` CHAR(255) NOT NULL,
    `sexe` CHAR(255) NOT NULL,
    `date_naissance` DATE NOT NULL,
    `num_tel` CHAR(11) NOT NULL,
    `email` CHAR(255) NOT NULL,
    `categorie` CHAR(255) NOT NULL,
    `anciennete` INT NOT NULL,
    `salaire` INT NOT NULL,
    `sanction` CHAR(255) NOT NULL,
    `date_sanction` DATE NOT NULL,
    `formation` CHAR(255) NOT NULL
);
CREATE TABLE `Groupe`(
    `id_groupe` INT(10) UNSIGNED NOT NULL AUTO_INCREMENT PRIMARY KEY,
    `id_employe` INT(10) UNSIGNED NOT NULL
);
CREATE TABLE `Client`(
    `id_client` INT(10) UNSIGNED NOT NULL AUTO_INCREMENT PRIMARY KEY,
    `nom` CHAR(255) NOT NULL,
    `prenom` CHAR(255) NOT NULL,
    `adresse` CHAR(255) NOT NULL,
    `num_tel` CHAR(11) NOT NULL,
    `email` CHAR(255) NOT NULL
);
CREATE TABLE `Materiel`(
    `id_materiel` INT(10) UNSIGNED NOT NULL AUTO_INCREMENT PRIMARY KEY,
    `nom_materiel` CHAR(255) NOT NULL,
    `prix_unitaire` INT NOT NULL,
    `quantite` INT NOT NULL,
    `quantite_total` INT NOT NULL
);
CREATE TABLE `Fournisseur`(
    `id_fournisseur` INT(10) UNSIGNED NOT NULL AUTO_INCREMENT PRIMARY KEY,
    `nom_fournisseur` CHAR(255) NOT NULL,
    `id_materiel` INT UNSIGNED NOT NULL
);
CREATE TABLE `Prestation`(
    `id_prestation` INT(10) UNSIGNED NOT NULL AUTO_INCREMENT PRIMARY KEY,
    `adresse` CHAR(255) NOT NULL,
    `cout` INT NOT NULL,
    `date_commande` DATE NOT NULL,
    `date_fin` DATE NOT NULL,
    `id_client` INT(10) UNSIGNED NOT NULL,
    `id_groupe` INT(10) UNSIGNED NOT NULL,
    `id_materiel` INT(10) UNSIGNED NOT NULL,
    `type_prestation` CHAR(255) NOT NULL,
    `demande` TEXT NOT NULL
);
ALTER TABLE
    `Groupe` ADD CONSTRAINT `groupe_id_employe_foreign` FOREIGN KEY(`id_employe`) REFERENCES `Employe`(`id_employe`);
ALTER TABLE
    `Prestation` ADD CONSTRAINT `prestation_id_groupe_foreign` FOREIGN KEY(`id_groupe`) REFERENCES `Groupe`(`id_groupe`);
ALTER TABLE
    `Fournisseur` ADD CONSTRAINT `fournisseur_id_materiel_foreign` FOREIGN KEY(`id_materiel`) REFERENCES `Materiel`(`id_materiel`);
ALTER TABLE
    `Prestation` ADD CONSTRAINT `prestation_id_client_foreign` FOREIGN KEY(`id_client`) REFERENCES `Client`(`id_client`);
ALTER TABLE
    `Prestation` ADD CONSTRAINT `prestation_id_materiel_foreign` FOREIGN KEY(`id_materiel`) REFERENCES `Materiel`(`id_materiel`);
```

Exécuter ensuite la commande suivante

```bash
mysql -u username -p password database_name < filename.sql
```