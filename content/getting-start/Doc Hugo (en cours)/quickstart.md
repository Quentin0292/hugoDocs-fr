+++

title = "Hugo QuickStart"
description = "Avant de se lancer dans la construction d'une documentation... un guide simple pour créer une bibliothèque en ligne."
weight = 2
+++

[Source originale](https://gohugo.io/overview/quickstart/ "Permalink to Hugo - Hugo Quickstart Guide")

## Construire une Bibliothèque

Dans ce guide de démarrage, nous allons construire une bibliothèque qui listera les livres et leurs critiques.

> _Note : Ce guide dépend de fonctionnalités présentées dans la version Hugo v0.15. Si vous avez une version précédente d'Hugo,  [mettez à jour][1] avant de démarrer._

## Étape 1. Installer Hugo

Foncez sur les [Hugo Releases][2] et téléchargez la version qui correspondra à votre système d'exploitation et à votre architecture.

Sauvegardez l'exécutable choisi sous `hugo` (ou `hugo.exe` sur Windows) quelque part dans votre `PATH` car nous devrons l'utiliser pour la prochaine étape.

Des instructions plus détaillées sont disponibles sur [Installing Hugo][1]. (NDT à traduire)

Si vous êtes sous Windows, ce guide de démarrage suppose que vous utilisez [Git Bash][3] (aussi connu comme Git pour Windows). Par conséquent, toutes les commandes démarreront avec le caractère d'invitation Bash (qui est `$`).

Une fois installé `hugo`, assurez-vous de lancer la commande `help` afin de vérifier l'installation de `hugo`. Ci-dessous, vous pouvez voir une partie traduite de l'output de la commande `help`.
    
    
    $ hugo help
    
    hugo c'est la commande principale, utilisée pour construire votre site Hugo.
    
    Hugo est un Générateur de Site Statique (GSS) Rapide et Flexible construit avec amour par spf13 et ses amis en Go.
    
    Une documentation complète est disponible sur http://gohugo.io/.

Vous pouvez vérifier la version de  `hugo` en utilisant la commande en dessous.
    
    $ hugo version
    
    Hugo Static Site Generator v0.15 BuildDate: 2015-11-26T11:59:00+05:30
    

## Étape 2. Échafaudez le site de la Bibliothèque avec Hugo 

Hugo dispose de commmandes qui nous permettent d'échafauder rapidement un site web géré avec Hugo. Naviguez vers un endroit qui vous plaira sur votre système de fichiers, et créez un nouveau site `bibliotheque` en exécutant la commande qui suit : 
    
    
    $ hugo new site bibliotheque
    
Changez de répertoire vers `bibliotheque` 

    $ cd bibliotheque 

lancez la commande `tree -a` pour visualiser  l'arbre de votre répertoire :


    $ tree -a
    
    .
    ├── archetypes
    │   └── default.md
    ├── config.toml
    ├── content
    ├── data
    ├── layouts
    ├── static
    └── themes
    
    6 directories, 2 files    

Comme précisé dans la commande, le dossier `bibliotheque` comprend 6 sous-dossiers et 2 fichiers. Jetons un oeil à chacun d'eux.

* **archetypes** : Vous pouvez créer de nouveaux fichiers de contenu dans Hugo en utilisant la commande `hugo new`. Quand vous lancez cette commande, elle ajoute de nouvelles propriétés de configuration au post comme la date et le titre. L'[archétype][4] vous permet de définir vos propres propriétés de configuration qui seront ajoutées à l'en-tête (front matter) de votre post à chaque fois que la commande `hugo new` sera utilisée. 
* **config.toml** : Chaque site web devrait avoir un fichier de configuration à sa racine. Par défaut, le fichier de configuration utilise le format `TOML` mais vous pouvez aussi utiliser tout aussi bien les formats `YAML` ou `JSON`. [TOML][5] est le format minimal de fichier de configuration qui reste facile à lire. Les réglages de configuration cités dans le `config.toml` s'appliquent à l'ensemble  du site. Ces réglages de configuration comprennent les URLs de base et titre (`baseURL` et `title`) du site web.
* **content** : C'est là où vous stockerez le contenu du site web. Dans le dossier `content`, vous créerez des sous-répertoires pour différentes sections. Supposons que votre site web dispose de trois sections  – `blog`, `articles` et `tutoriel`. Vous aurez alors trois dossiers de sections différentes  pour chacune d'entre elles à l'intérieur du dossier `content`. Le nom de la section, à savoir `blog`, `articles`, ou `tutoriel` sera utilisé par Hugo pour s'appliquer à une mise en page (layout) spécifique applicable à cette section.
* **data** : Ce dossier est utilisé pour stocker les fichiers de configuration pouvant être utilisés par Hugo au moment de générer votre site web. Vous pouvez écrire ces fichiers en format YAML, JSON, ou TOML.
* **layouts** : Le contenu dans ce dossier est utilisé pour spécifier comment votre contenu sera converti à l'intérieur du site web statique.
* **static** : Ce dossier s'utilise pour stocker tout le contenu statique dont aura besoin votre site web comme des images, CSS, JavaScript ou tout autre contenu statique.
* **themes** : C'est l'endroit où vous stockerez les thèmes utilisés par votre site. Les thèmes fournissent la mise en page et les modèles qui restituent le contenu. Il existe une grande variété de thèmes open-source disponibles que vous vous pouvez télécharger et utiliser mais rien ne vous empêche de créer le vôtre.

## Étape 3. Ajouter du Contenu

Ajoutons maintenant un post à notre site  `bibliotheque`. Nous utiliserons la commande `hugo new` pour ajouter un post. En janvier, j'ai lu le livre [Good To Great][6], aussi nous commencerons par la création d'un billet pour ce livre. **Assurez-vous de bien être dans le dossier `bibliotheque`.**



    $ hugo new post/good-to-great.md
    
    /Users/xtof/Sites/Tuto-Quickstart-Hugo/bibliotheque/content/post/good-to-great.md created

La commande au-dessus crée un nouveau dossier `post` à l'intérieur du dossier  `bibliotheque/content` et crée à l'intérieur un fichier `good-to-great.md`.
    
    
    $ tree -a content
    
    content
    └── post
    └── good-to-great.md
    
    1 directory, 1 file
    

Le contenu à l'intérieur du fichier `good-to-great.md` ressemble à ce qui s'affiche en dessous : 


    ---
    title: "Good To Great"
    date: 2017-07-01T14:31:19+02:00
    draft: true
    ---


Le contenu placé entre les signes `+++` est la configuration TOML du billet. Cette configuration s'appelle le **front matter**. Il vous permet de définir la configuration de votre billet avec son contenu. Par défaut, chaque billet aura les trois propriétés de configuration présentées au-dessus. 

* **title** spécifie le titre du billet.
* **date** spécifie la date et l'horaire à laquelle le billet a été créé.
* **draft** spécifie que ce post n'est pas prêt pour la publication, il n'apparaîtra donc pas dans le fichier généré.

Ajoutons une petite critque pour le livre **Good to Great** :     

    ---
    title: "Good To Great"
    date: 2017-07-01T14:31:19+02:00
    draft: true
    ---


    
    J'ai lu **Good to Great en janvier 2016**. Une analyse merveilleuse décrivant avec acuité comment les grandes sociétés enchantent le monde.
    

## Étape 4. Servir le contenu

Hugo a un serveur intégré qui peut servir le contenu de votre site web afin que vous puissiez le prévisualiser. Vous pouvez aussi utiliser le serveur intégré d'Hugo en production. Pour servir le contenu, lancez la commande suivante à l'intérieur de votre répertoire `bibliotheque` :
    
    
    $ hugo server
    
    Started building sites ...
    Built site for language en:
    0 of 1 draft rendered
    0 future content
    0 expired content
    0 regular pages created
    6 other pages created
    0 non-page files copied
    0 paginator pages created
    0 tags created
    0 categories created
    total in 14 ms
    Watching for changes in /Users/xtof
    Sites/Tuto-Quickstart-Hugo/bibliotheque
    {data,content,layouts,static}
    Serving pages from memory
    Web Server is available at http://localhost:1313/ (bind address 127.0.0.1)
    Press Ctrl+C to stop

Cette commande lancera le serveur sur le port port `1313`. Vous pourrez regarder votre blog à l'adresse <http://localhost:1313/>. Vous allez sur le lien et ne verrez rien ! Deux raisons à cela : 

1. Comme vous pouvez le voir dans la sortie de commande `hugo server`, Hugo n'a pas produit le draf. Hugo ne produira les drafts (ébauches) que si vous passez le flag `buildDrafts` sur la commande `hugo server`.
2. Nous n'avons pas spécifié comment le contenu Markdown devrait être produit. Nous devons spécifier un thème à utiliser par Huto. Nous ferons ça à l'étape suivante.

Pour produire les drafts (ébauches), relancez le serveur avec la commande ci-dessous : 
    
    `$ hugo server --buildDrafts
    
    Started building sites ...
    Built site for language en:
    1 of 1 draft rendered
    0 future content
    0 expired content
    1 regular pages created
    8 other pages created
    0 non-page files copied
    0 paginator pages created
    0 tags created
    0 categories created
    total in 6 ms
    Watching for changes in /Users/xtof/Sites/Tuto-Quickstart-Hugo/bibliotheque/{data,content,layouts,static}
    Serving pages from memory
    Web Server is available at http://localhost:1313/ (bind address 127.0.0.1)
    Press Ctrl+C to stop

Si vous tapez l'adresse <http://localhost:1313/>, vous ne verrez encore ein car nous n'avons pas toujours spécifié de thème à utiliser par Hugo.

## Étape 5. Ajoutez un thème

Les thèmes fournissent la mise en page et les modèles qui seront utilisés par Hugo pour la production de votre site Web. Il existe de nombreux thèmes open-source disponibles que vous pouvez utiliser sur <https://themes.gohugo.io/>.

> **Hugo n'est toujours pas livré à ce jour avec un thème `default`, permettant à l'utilisateur de choisir le thème qui conviendra le mieux à son projet.**

Les thèmes doivent être ajoutés dans le dossier `themes` à l'intérieur de la racine de votre dossier.

Lancez la commande :     
    
    $ cd themes

Désormais, vous pouvez cloner un ou plusieurs thèmes à l'intérieur de votre dossier `themes`. Nous utiliserons ici le thème `robust`, mais avec un point d'arrêt (dans son historique) qui fonctionne pour ce guide de démarrage rapide.
  
    $ git clone https://github.com/dim0627/hugo_theme_robust.git
    $ (cd hugo_theme_robust; git checkout b8ce466)
    

Oubliez les détails pour le moment de la fenêtre du terminal et quittez le dossier `themes`.

Lancez la commande : 

    $ cd ..
    

Redémarrez le serveur 
    
    
    $ hugo server --theme=hugo_theme_robust --buildDrafts
    
    
    Started building sites ...
    Built site for language en:
    1 of 1 draft rendered
    0 future content
    0 expired content
    1 regular pages created
    8 other pages created
    0 non-page files copied
    2 paginator pages created
    0 tags created
    0 categories created
    total in 8 ms
    Watching for changes in /Users/xtof/Sites/Tuto-Quickstart-Hugo/bibliotheque/{data,content,layouts,static,themes}
    Serving pages from memory
    Web Server is available at http://localhost:1313/ (bind address 127.0.0.1)
    Press Ctrl+C to stop    

> _Note : Si Hugo ne trouve pas le thème spécifié dans le dossier `themes`, il lancera une exception comme affiché en-dessous._

>     FATAL: 2016/02/14 Unable to find theme Directory: /Users/xtof/bibliotheque/themes/robust

Pour voir votre site web, rendez-vous maintenant sur <http://localhost:1313/>. Vous verrez ce qui s'affiche ci-dessous.

![][7]

Essayons de comprendre la mise en forme du thème. Un thème comporte les éléments suivants :

* **theme.toml** est le fichier de configuration du thème qui vous donne l'information sur le thème comme le nom et la description du thème, les détails de l'auteur et la licence du thème.
* **images** est un dossier qui comprend deux images – `screenshot.png` et `tn.png`. `screenshot.png` est l'image de la vue en liste et `tn.png` est la visualisation d'eun billet unique..
* **layouts** est le dossier qui contient difféentes vues pour différents types de contenus. Chaque type de contenu devrait avoir deux fichiers `single.html` et `list.html`. `single.html` s'utilise pour produire un morceau unique de contenu. `list.html` s'utilise pour visualiser une liste d'items de contenus. Par exemple, vous utilisez `list.html` pour voir tous les posts qui ont le tag `programmation`.
* **static** est le dossier qui stocke tous les actifs statiques utilisés par le modèle. Les bibliothèques JavaScript comme  jQuery ou les styles CSS ou les images, ou tout autre contenu statique. Ce dossier sera copié à l'intérieur du site final au moment de la production.

## Étape 6. Utilisez plusieurs thèmes

Vous pouvez facilement tester différentes configurations en alternant entre différents thèmes. Supposons que nous voulions essayer le thème `bleak`. Nous clonons le thème `bleak` dans le répertoire `bibliotheque/themes`.

Replacez-vous dans le dossier `themes`

    cd themes
    
Et clonez le thème `bleak` :

    $ git clone https://github.com/Zenithar/hugo-theme-bleak.git
    

Redémarrez le serveur en utilisant le thème `hugo-theme-bleak` comme affiché ci-dessous 
    
    $ cd ..
    $ hugo server --theme=hugo-theme-bleak --buildDrafts
    

Désormais, le site web utilise le thème `bleak` et s'affiche différemment comme ci-dessous 

![Bibliothèque avec le thème Bleak](https://monosnap.com/file/rSwnbQN1sEzIPE450E3KQ9oOH4opHl.png)

## Étape 7. Mise à jour de config.toml et rechargement live en action

Maintenant, arrêtez si besoin (Ctrl + C) pour redémarrer le serveur avec le thème `robust`, car nous allons l'utiliser pour ce guide démarrage rapide.
        
    $ hugo server --theme=hugo_theme_robust --buildDrafts
    

Le site web utilise les valeurs stupides spécifiées dans le fichier de configuration `bibliotheque/config.toml`. Mettons à jour la configuration.
    
    
    baseURL = "http://exemple.org/"
    languageCode = "fr-fr"
    title = "Critiques de Livres par Shekhar Gulati"
    
    [Params]
      Author = "Shekhar Gulati"
    

Hugo supporte le rechargement en live. Par conséquent, dès que nous sauvegardons nos modifications, elles s'appliqueront et rechargeront la page web. Vous verrez les modifications s'afficher en dessous.

![Fichier config.toml mis à jour. (titre du site et nom de l'auteur)](https://monosnap.com/file/UbJoG3jvblTgmwRk1fO7Ymc8dLIg7l.png)

Outre la visualisation, vous retrouverez la même chose renvoyée dans les journaux du serveur Hugo. Dès que vous avez modifié le fichier de configuration, Hugo a appliqué ces modifications aux pages concernées     
    
    Config file changed: /Users/xtof/Sites/Tuto-Quickstart-Hugo/bibliotheque/config.toml
    Started building sites ...
    Built site for language en:
    1 of 1 draft rendered
    0 future content
    0 expired content
    1 regular pages created
    8 other pages created
    0 non-page files copied
    2 paginator pages created
    0 tags created
    0 categories created
    total in 24 ms    

## Étape 8. Personnaliser le thème robust

Le thème `robust` est un bon départ pour notre bibliothèque en ligne mais nous voulons le personnaliser afin de le rapprocher de nos besoins pour une bibliothèque. Hugo facilite la personnalisation des thèmes. Vous pouvez aussi créer vos propres thèmes, mais nous ne le ferons pas aujourd'hui. Si vous souhaitez créer votre propre thème, vous devriez vous référer à la [documentation Hugo documentation] [10].

La première modification à produire, c'est d'utiliser une image par défaut différente de celle utilisée dans le thème. L'image par défaut du thème utilisée dans la liste et de la page de visualisation unique se trouve à l'intérieur de `themes/hugo_theme_robust/static/images/default.jpg`. Nous pouvons facilement l'annuler en créant une structure de répertoire simple dans le répertoire `static` du dossier.

Créez un dossier `images`dans le répertoire `bibliotheque/static` et copiez une image avec le nom `default.jpg`. Nous utiliserons par défaut l'image affichée en dessous.

![image `default.jpg` à copier dans votre dossier `bibliotheque/static/images`][11]

Hugo synchronisera les modifications et rechargera le site web pour utiliser cette nouvelle image comme affichée en dessous.

![Nouvelle image par défaut](https://monosnap.com/file/VsZKPzYi4vydK1787jnuwRBTexV7yE.png)

Maintenant, nous devons modifier le layout de la page index afin que seules les images soient affichées au lieu du texte. Le fichier `index.html` dans le dossier layouts du thème fait référence au partiel `li` qui produit la vue en liste ci-dessous.    
    
    <article class="li">
      <a href="" class="clearfix">
        <div class="image" style="background-image: url({{ $.Site.BaseURL }}images/{{ with .Params.image }}{{ . }}{{ else }}default.jpg{{ end }});"></div>
        <div class="detail">
          <time>{{ with .Site.Params.DateForm }}{{ $.Date.Format . }}{{ else }}{{ $.Date.Format "Mon, Jan 2, 2006" }}{{ end }}</time>
          <h2 class="title">{{ .Title }}</h2>
          <div class="summary">{{ .Summary }}</div>
        </div>
      </a>
    </article>
    

Créez un nouveau fichier li.html à l'intérieur du dossier  `bibliotheque/layouts/_default`. Copiez le contenu affiché en dessous dans le fichier `li.html`. Nous y avons enlevé les détails du livre, aussi seule l'image s'affiche.
    
    
    <article class="li">
      <a href="" class="clearfix">
        <div class="image" style="background-image: url({{ $.Site.BaseURL }}images/{{ with .Params.image }}{{ . }}{{ else }}default.jpg{{ end }});"></div>
      </a>
    </article>
    

Maintenant, le site web ressemblera à ce qui s'affiche en-desous 

![... image sans détails.](https://monosnap.com/file/GgqLdZrcGQu87neTAWQQGN4VBxLjOl.png)

Ensuite, nous voulons retirer l'information présente en pied de page conceranant le thème. Pour faire ainsi, créez un nouveau dossier `partials` à l'intérieur de `bibliotheque/layouts`. Dans ce dossier, créez un nouveau fichier, `default_foot.html` avec le contenu copié à partir du `layouts/partials/default_foot.html` du thème. Remplacez la section footer avec celle en dessous.
    
    
     <footer class="site">
         <p>{{ with .Site.Copyright | safeHTML }}{{ . }}{{ else }}&copy; {{ $.Site.LastChange.Year }} {{ if isset $.Site.Params "Author" }}{{ $.Site.Params.Author }}{{ else }}{{ .Site.Title }}{{ end }}{{ end }}</p>
         <p>Motorisé par <a href="http://gohugo.io" target="_blank" rel="nofollow">Hugo</a></p>
     </footer>
    
Nous devons aussi enlever la barre latérale à droite. Copiez le fichier `index.html` dans le dossier `layouts` du thème vers le dossier `bibliotheque/layouts`. Retirez la section en rapport avec la barre latérale du HTML :

    <div class="col-sm-3">
      {{ partial "sidebar.html" . }}
    </div>

À ce stade, nous utilisons l'image par défaut, mais nous aimerions utiliser l'image du livre que nous pourrions relier au livre. Chaque critique de livre définira un réglage de configuration dans son front matter. Mettez à jour l'article  `good-to-great.md` comme indiqué ci-dessous.
    
    +++
    date = "2017-07-01T16:11:58+05:30"
    draft = true
    title = "Good to Great Book Review"
    image = "good-to-great.jpg"
    +++
    
    J'ai lu **Good to Great en janvier 2016**. Une analyse merveilleuse décrivant avec acuité comment les grandes sociétés enchantent le monde.
    

Piquez quelque part (légal SVP) une image, appelez-la `good-to-great.jpg`, et placez-la dans le dossier `bibliotheque/static/images`.

Après avoir ajouté quelques autres livres à notre étagère de bibliothèque, voic à quoi ressemble l'ensemble. Quelques livres que j'ai lus durant l'année. 

![image à refaire en français](https://d33wubrfki0l68.cloudfront.net/e03165bd6db7ba50f0bb728074b50809562fb050/ae4e7/img/quickstart/bookshelf.png)

## Étape 9. Rendre les posts publics

À ce stade, tous les posts que nous avons écrits sont en statut draft (ébauche). Afin de faire qu'un draft soit public, vous pouvez soit lancer une commande ou modifier manuellement le statut draft dans le post en `false`.

Lancez la commande     

    $ hugo undraft content/post/good-to-great.md

Maintenant, vous pouvez lancer le serveur sans l'option `buildDrafts`.

    $ hugo server --theme=hugo_theme_robust

Disqus vous permet d'intégrer des commentaires dans votre blog statique. Pour activer Disqus, il suffit de définir `disqusShortname` dans votre fichier de configuration `config.toml comme indiqué ci-dessous.

    [Params]
      Author = "votre prenom et nom"
      disqusShortname = <votre nomutilisateur Disqus>

Maintenant, le commentaire sera activé sur votre blog.

![commentaire Disqus](https://monosnap.com/file/AsSseCEoy7WDogFwmyof1OVgTK2uta.png)

## Étape 11. Générer le Site Web

Pour générer la source du site web Hugo, vous pouvez utiliser pour déployer votre site web le service GitHub Pages. Modifiez d'abord dans votre fichier de configuration `bibliotheque/config.toml`, la ligne `baseURL` en :

    baseURL = "https://<votre nomutilisateur GitHub>.github.io/bibliotheque/"

Puis lancez la commande suivante.

    $ hugo --theme=hugo_theme_robust
    
    Started building sites ...
    Built site for language en:
    0 draft content
    0 future content
    0 expired content
    1 regular pages created
    8 other pages created
    0 non-page files copied
    2 paginator pages created
    0 tags created
    0 categories created
    total in 10 ms


Après avoir lancé la commande `hugo`, un répertoire  `bibliotheque/public` est créé contenant la source du site web généré.

P.S. En passant, (si vous avez essayé), le site web n'est pas accessible proprement via le protocole `file:///`.

## Étape 12. Déployez le site bibliotheque sur GitHub pages

Lançons le contôle de version de votre bibliotheque : 

    $ git init
    $ echo "/public/" >> .gitignore
    $ echo "/themes/" >> .gitignore
    $ git add --all
    $ git commit -m "Initial commit"
    

Maintenant les repos Git sous `bibliotheque/themes` ne rentreront plus en conflit avec votre repo `bibliotheque`, et c'est aussi le cas pour un repo Git dans `bibliotheque/public`.

Créez un nouveau repository sur GitHub appelé `bibliotheque` (sans  README). Une fois que c'est fait, créez un nouveau repo Git sur votre système local dans `bibliotheque/public` et ajoutez remote :

    $ cd public
    $ git init
    $ git remote add origin git@github.com:<votre-nomutilisateur-github>/bibliotheque.git

Puis créez et checkout une nouvelle branche `gh-pages`

    $ git checkout -b gh-pages
    Switched to a new branch 'gh-pages'
    

Ajoutez tous les fichiers (dans `bibliotheque/public`) à l'index, commitez-les, et poussez les modifications sur GitHub.

    $ git add --all
    $ git commit -m "bibliotheque added"
    $ git push -f origin gh-pages


Dans quelques minutes, votre site web sera vivant sur `https://<github-nomutilisateur>.github.io/bibliotheque/`.

A tout moment, vous pouvez régénérer votre site avec : 

    $ (cd ..; hugo --theme=hugo_theme_robust)
    $ git add --all
    $ git commit -m "<some change message>"
    $ git push -f origin gh-pages
    

* * *

Ce tutoriel rapide a été initialement écrit par [Shekhar Gulati][16] dans sa série de blog [52 Technologies in 2016][17].

[1]: https://gohugo.io/overview/installing/
[2]: https://github.com/gohugoio/hugo/releases
[3]: https://git-for-windows.github.io/
[4]: https://gohugo.io/content/archetypes/
[5]: https://github.com/toml-lang/toml
[6]: http://www.amazon.com/Good-Great-Some-Companies-Others/dp/0066620996/
[7]: https://d1ro8r1rbfn3jf.cloudfront.net/ms_35590/CPzNqsm7sTlNQvQkjipd39Nr8Sfxap/My%2BNew%2BHugo%2BSite-theme-robust.png?Expires=1499000968&Signature=hn3OOZ4lAQcizvR-NXOnJUVuift1Lchg2RGP4zrl9XUzQFKEjGcPtW6JZOFhlZCGM1w4~A2tBJSzU2se8JiuWoEv46sMPZU9Am7UGzxXV2eyemeVFng0Nze9bq~FNDCAQt920Khpk7tM5lGCzjc3MmTckVp4qkSsxA1l-lCjelJKoRExP5dttNIp84Z7BzZUaP23shWEF40hcfSYkfbTRv4LRwJ6-eQeCqHOml4l9Cd~btaJ4oTRkOXk6YNH13lbQe~~FwwYbCMnVUhzIld2jOuFcPOpQTR16KzWgrMd0kHsC18q3nQzW1lh9CA-p8ZOSKy1FrgjeQ0wFAJo8npgLg__&Key-Pair-Id=APKAJHEJJBIZWFB73RSA
[8]: loudfront.net/e1f909506901b95bb95c7b1e59055658eadc5641/0f5ca/img/quickstart/bookshelf-bleak-theme.png
[9]: https://d33wubrfki0l68.cloudfront.net/08d0677e03a918c95c5bb5060f66165e09c1e8d3/7a5b5/img/quickstart/bibliotheque-updated-config.png
[10]: https://gohugo.io/themes/creation/
[11]: https://d33wubrfki0l68.cloudfront.net/447347fbf1133963df95f6509f7c54176431106d/8613d/img/quickstart/default.jpg
[12]: https://d33wubrfki0l68.cloudfront.net/23f0d937f891116d0838edc3567d59e9e21bf949/de922/img/quickstart/bibliotheque-new-default-image.png
[13]: https://d33wubrfki0l68.cloudfront.net/2892039ba375a68aa7797e1c41e8daebccf7a3e4/525e1/img/quickstart/bibliotheque-only-picture.png
[14]: https://d33wubrfki0l68.cloudfront.net/e03165bd6db7ba50f0bb728074b50809562fb050/ae4e7/img/quickstart/bibliotheque.png
[15]: https://d33wubrfki0l68.cloudfront.net/befcde2ffdd91d30376565731957739cf6fd615c/ce533/img/quickstart/bibliotheque-disqus.png
[16]: https://twitter.com/shekhargulati
[17]: https://github.com/shekhargulati/52-technologies-in-2016
