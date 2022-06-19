# Environement de dévellopement
Le site GEORUN utilisant ReactJs il faut un environnement de dévellopement spécifique pour le modifier 
## Installer NodeJs
Télécharger node version manager.

```bash
curl https://raw.githubusercontent.com/creationix/nvm/master/install.sh | bash
```
Ajoutez ensuite les variables d'environnement pour NVM dans le .bashrc

```bash
source ~/.bashrc
```

Installation de Node.js avec NVM.

```bash
nvm install 16.5.1
```

## Cloner le repertoire
Cloner le code souce du site GEOREUN 

```bash
git clone https://github.com/Vito974/SAE24-Front-end.git
```

## Lancer le serveur de dévellopement
Déplacez vous dans le répertoire
```bash
cd SAE24-Front-end
```

Lancer le serveur de test 

```bash
npm run dev 
```

Entrer http://localhost:3000/ dans votre navigateur 