# Création d'un projet

## Installation de nodeJS et npm
Installer la version de nodeJs et npm
https://nodejs.org/fr/

## Création des dossiers et fichiers

**Dans le dossier du projet :**

- Création du dossier *name_project* qui va contenir l'ensemble du name_project
```
mkdir name_project
cd name_project
```

- Création du fichier *package.json* pour gérer le projet (scripts, dépendances...) avec la commande :
```
npm init
```

- Installation de la bibliothèque **express**
```
npm install --save express
```

- Création du fichier index.js
```
touch index.js
```

- Ajouter le code à l'intérieur :
```javascript
const express = require('express');

const app = express();

app.get('/', (req, res) => {
    res.send({hi: 'there' });
});

app.listen(5000);

```

- Lancer le test de fonctionnement :
```
node index.js
```
Regarder à l'adresse [localhost:5000](http://localhost:5000) le bon fonctionnement avec l'affichage {"hi":"there"}
