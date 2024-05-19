# Repertorio

Repertorio est une méthode qui permet de générer une page web listant – pour chaque morceau de la fanfare – des vidéos d'initiation aux thèmes.

Ceci est un guide pour générer la-dite page web. 

## Installation préalable

Sur votre ordinateur, vous devez [installer Python](https://www.python.org/downloads/), [pip](https://pip.pypa.io/en/stable/installation/) puis [Blub](https://github.com/16arpi/blup).

## Edition du fichier `repertoire.json`

Ce fichier concentre toutes les informations à connaître sur le repertoire de la fanfare. Dans chaque morceau, on retrouve une partie intrumentale avec – pour chaque – un *clip* pouvant être :

* une vidéo
* un fichier joint
* une photo

### Racine du fichier 

La racine du fichier concerne le nom de la fanfare, les pupitres présents et les morceaux.

```json
{
  "fanfare": "La Locomotive",
  "pupitres": [
      "trompette",
      "trombone",
      "bois",
      "percussions",
      "basse"
  ],
  "morceaux": [
    ...
  ]
}
```

### Morceau

Un morceau a un nom, un identifiant (en minuscule sans accent) et la liste des partie.

```json
{
  "nom": "24000 baci",
  "id": "24000",
  "parties": [
    ...
  ]
}
```

### Partie d'un morceau

Une partie d'un morceau a un nom, son pupitre associé (respectant les pupitres listés à la racine du fichier) et un clip.

```json
{
    "nom": "Theme 1",
    "pupitre": "trombone",
    "clip": {
        ...
    }
}
```

### Clip possibles pour une partie

Clips disponibles :

**video** 

```json
"clip": {
    "type": "video",
    "content": "./videos/24000/intro.mp4"
}
```

**image** 

```json
"clip": {
    "type": "image",
    "content": "./image/quelquechose.jpg"
}
```

**fichier** 

```json
"clip": {
    "type": "fichier",
    "content": "./partition.pdf"
}
```

## Génération de la page HTML

Une fois le fichier `repertoire.json` prêt, vous pouvez génerer la page web à l'aide de blup et du fichier `template.html` :

```bash
$ blup template.html repertoire.json -o output.html
```
