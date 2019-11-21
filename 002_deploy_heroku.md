# Utilisation de Heroku pour de futures productions

## S'inscrire sur Heroku

https://heroku.com

## Création d'un Dynamic Port Binding

**Dans le fichier *index.js* :**

Ajout de la ligne de code :
```javascript
//The new line
const PORT = process.env.PORT || 5000;

app.listen(PORT); // Change 5000 to PORT
```
Cette nouvelle ligne va permettre a Heroku de choisir le port qui sera utilisé lors du déploiement. Ce port aura été fixé dans la gestion des variables d'environnement pour le projet créé sur Heroku. \
Si on est pas sur Heroku, le port 5000 sera choisi par défaut.

## Spécifier l'environnement de Node

**Dans le fichier *package.json* :**\
On rajoute les versions de Node et npm qui seront à utiliser. Elles sont décrites avec **engines**.\
Rajouter **engines** entre **main** et **scripts** :

```json
"main": "index.js",
"engines": {
    "node": "8.1.1",
    "npm": "5.0.3"
},
"scripts": {
    "test": "echo \"Error: no test specified\" && exit 1"
}
```
Les versions de node et npm sont à définir pour votre projet.

## Spécifier le script de démarrage du serveur
Pour démarrer le serveur, Heroku a besoin d'une commande de lancement qui sera décrite dans la partie **scripts** du fichier *package.json*.\
Effacer la ligne avec *"test"* et renseigner par la ligne suivante :

```json

"scripts": {
    "start": "node index.js"
}
```

## Mettre en place un .gitignore pour les dépendances
Toujours dans le répertoire *server*, ajouter le fichier *.gitignore* :
```
touch .gitignore
```
Ecrire à l'intérieur : \
**node_modules**\
\
Ainsi lors des commits, les dépendances ne seront pas push sur le serveur Heroku. De plus Heroku réalisera lui même la gestion des dépendances que l'on a déclarées.


## Envoyer vers Heroku
### Installer Heroku sur la machine :
Via la commande :
```
sudo snap install --classic heroku
```
Contrôler l'installation avec :
```
heroku -v
```

### Mettre en place la gestion de version avec git
Initialiser le répertoire du projet avec la commande :
```
git init
```

Ajouter les modifications :
```
git add .
```
### Se logger avec Heroku
```
heroku login
```
Suivre les instructions qui suivent.

### "Créer" le nom de domaine du serveur hébergé par Heroku
Heroku permet de créer un nom de domaine temporaire pour retrouver l'application déployer sur le web.\
Cette création se réalise via la commande :
```
heroku create
```
On obtient ainsi via cette commande :
- Une adresse où l'on peut utiliser l'application sur le web\
ex: https://bullshit-link-77761.herokuapp.com/ 

- L'adresse d'un dépôt git hébergé sur Heroku\
ex: https://git.heroku.com/bullshit-link-77761.git

**Conserver les**.

### Ajouter les fichier et/ou les modifications sur le dépôt Heroku
Utilisation de la commande :
```
git remote add heroku https://git.heroku.com/bullshit-link-77761.git
```

Normalement le message d'erreur suivant devrait apparaître :
```
fatal: remote heroku already exist
```

Cela signifie que le dépôt a déjà été généré sur Heroku. Tout est bon.

### Pusher sur le serveur

```
heroku push heroku master
```
On push la branch master sur le dépôt Heroku.

### Tester le fonctionnement :

```
heroku open
```
Ouverture d'une page web montrant le message :
```
{"hi":"there"}
```
On se retrouve à la page web https://bullshit-link-77761.herokuapp.com/

### Voir les logs
Avec la commande :
```
heroku logs
```