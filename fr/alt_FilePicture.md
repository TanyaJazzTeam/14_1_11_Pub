Premier en-tête | Deuxième en-tête
--- | ---
Cellule de contenu | Cellule de contenu
Cellule de contenu | Cellule de contenu

Premier en-tête | Deuxième en-tête
--- | ---
Cellule de contenu | Cellule de contenu
Cellule de contenu | Cellule de contenu

![Citadelle](https://vignette.wikia.nocookie.net/masseffect/images/d/d7/MassEffect2Citadel.jpg/revision/latest?cb=20100721191415)

Aligné à gauche | Aligné au centre | Aligné à droite
:-- | :-: | --:
la col 3 est | un texte verbeux | **1600 $**
la col 2 est | centré | 12 $
rayures zébrées | sont soignés | ~~$1~~

Dillinger est un éditeur HTML5 Markdown optimisé pour le cloud, prêt pour le mobile, pour le stockage hors ligne et alimenté par AngularJS.

- Tapez du Markdown sur la gauche
- Voir HTML à droite
- la magie

# vrai

- Importez un fichier HTML et regardez-le se convertir comme par magie en Markdown
- Faites glisser et déposez des images (nécessite que votre compte Dropbox soit lié)

Vous pouvez également:

- Importez et enregistrez des fichiers depuis GitHub, Dropbox, Google Drive et One Drive
- Faites glisser et déposez les fichiers Markdown et HTML dans Dillinger
- Exporter des documents au format Markdown, HTML et PDF

Markdown est un langage de balisage léger basé sur les conventions de formatage que les gens utilisent naturellement dans les e-mails. Comme [John Gruber] l'écrit sur le [site Markdown][df1]

> L'objectif primordial de la conception de la syntaxe de formatage de Markdown est de la rendre aussi lisible que possible. L'idée est qu'un document au format Markdown doit être publiable tel quel, en texte brut, sans donner l'impression qu'il a été balisé avec des balises ou des instructions de formatage.

Ce texte que vous voyez ici est *en fait* écrit en Markdown ! Pour avoir une idée de la syntaxe de Markdown, tapez du texte dans la fenêtre de gauche et regardez les résultats dans la droite.

### faux

Dillinger utilise un certain nombre de projets open source pour fonctionner correctement :

- [AngularJS] - HTML amélioré pour les applications Web !
- [Ace Editor] - éditeur de texte génial basé sur le Web
- [markdown-it] - Analyseur Markdown bien fait. Rapide et facile à étendre.
- [Twitter Bootstrap] - excellent passe-partout d'interface utilisateur pour les applications Web modernes
- [node.js] - E/S événementielles pour le backend
- [Express] - framework d'application réseau node.js rapide [@tjholowaychuk]
- [Gulp] - le système de construction en continu
- [Breakdance](https://breakdance.github.io/breakdance/) - Convertisseur HTML en Markdown
- [jQuery] - euh

Et bien sûr, Dillinger lui-même est open source avec un [dépôt public][dill] sur GitHub.

### Installation

![Ilos](https://lh3.googleusercontent.com/proxy/DDV8a7sLIWurhJtW8Ego9bq-JlwpfFFoR0tkLJQKKYXEXoWHB6ZUP5jGKD2VcYt3z1QVsgcn6L3GoU1ns8m9fvi3U51GzddA70ZUMHgzHvjl4-i7YOJY9cShBPrfjUhMQhxaJ97WFBp612XmjMXVGypfGkiBarN4PWxhiHkiYYNW7HGbtTpOcyt9GQ4Q23C2noxLTWFXZMcQZhRpQA_qzu2n6_H6CPViBnhSHpEl4JZAPaGCSJqgZg)

Dillinger nécessite [Node.js](https://nodejs.org/) v4+ pour s'exécuter.

Installez les dépendances et devDependencies et démarrez le serveur.

```sh
$ cd dillinger
$ npm install -d
$ node app
```

Pour les environnements de production...

```sh
$ npm install --production
$ NODE_ENV=production node app
```

### Plugins

Dillinger est actuellement étendu avec les plugins suivants. Les instructions sur la façon de les utiliser dans votre propre application sont liées ci-dessous.

Brancher | LISEZMOI
--- | ---
Boîte de dépôt | [plugins/dropbox/README.md][PlDb]
GitHub | [plugins/github/README.md][PlGh]
Google Drive | [plugins/googledrive/README.md][PlGd]
OneDrive | [plugins/onedrive/README.md][PlOd]
Moyen | [plugins/support/README.md][PlMe]
Google Analytics | [plugins/googleanalytics/README.md][PlGa]

### Développement

## autre

Les métriques qui composent Core Web Vitals [évolueront](#evolving-web-vitals) au fil du temps. L'ensemble actuel pour 2020 se concentre sur trois aspects de l'expérience utilisateur ( *chargement* , *interactivité* et *stabilité visuelle* ) et comprend les mesures suivantes

Vous voulez contribuer ? Super!

Dillinger utilise Gulp + Webpack pour un développement rapide. Effectuez une modification dans votre dossier et visualisez instantanément vos mises à jour !

Ouvrez votre terminal préféré et exécutez ces commandes.

Premier onglet :

```sh
$ node app
```

Deuxième onglet :

```sh
$ gulp watch
```

(facultatif) Troisième :

```sh
$ karma test
```

#### Construire pour la source

Pour la version de production :

```sh
$ gulp build --prod
```

Génération d'archives zip prédéfinies pour la distribution :

```sh
$ gulp build dist --prod
```

### Docker

Dillinger est très facile à installer et à déployer dans un conteneur Docker.

Par défaut, le Docker exposera le port 8080, alors modifiez-le dans le Dockerfile si nécessaire. Lorsque vous êtes prêt, utilisez simplement le Dockerfile pour créer l'image.

```sh
cd dillinger
docker build -t joemccann/dillinger:${package.json.version} .
```

Cela créera l'image dillinger et tirera les dépendances nécessaires. Assurez-vous d'échanger `${package.json.version}` avec la version actuelle de Dillinger.

Une fois cela fait, exécutez l'image Docker et mappez le port sur ce que vous souhaitez sur votre hôte. Dans cet exemple, nous mappons simplement le port 8000 de l'hôte au port 8080 du Docker (ou tout autre port exposé dans le Dockerfile) :

```sh
docker run -d -p 8000:8080 --restart="always" <youruser>/dillinger:${package.json.version}
```

Vérifiez le déploiement en accédant à l'adresse de votre serveur dans votre navigateur préféré.

```sh
127.0.0.1:8000
```

#### Kubernetes + Google Cloud

Voir [KUBERNETES.md](https://github.com/joemccann/dillinger/blob/master/KUBERNETES.md)

### À faire
