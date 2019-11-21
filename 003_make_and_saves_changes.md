# Faire des changements et visualiser sur Heroku

## Faire des changements dans un fichier
Dans le fichier *index.js*, changer la ligne :
```javascript
res.send({hi: 'there'});
```
par
```javascript
res.send({bye: 'buddy'});
```

## Ajouter ces changements sur Git
```
git add .
git commit -m "Changed greeting"
```

## Push sur Heroku
```
git push heroku master
```

## Voir les modifications
```
heroku open
```
Ouverture d'une page web montrant le message :
```
{"bye":"buddy"}
```