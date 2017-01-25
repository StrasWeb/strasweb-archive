# Initiation au HTML5

## Simplification

HTML5 simplifie un certain nombre de choses comme le *doctype*, la déclaration d'encodage

|HTML5|HTML 4.01|
|-----|---------|
|`<!Doctype HTML>`|`<!DOCTYPE HTML PUBLIC "-//W3C//DTD HTML 4.01//EN" "http://www.w3.org/TR/html4/strict.dtd">`|
|`<meta charset="UTF-8" />`|`<meta http-equiv="Content-Type" content="text/html;charset=utf-8">`|
|`<script src="script.js"></script>`|`<script src="script.js" type="text/javascript"></script>`|
|`<link rel="stylesheet" href="style.css" />`|`<link rel="stylesheet" href="style.css" type="text/css">`|

## Canevas

La balise `<canvas>` permet de définir une surface vide sur laquelle on peut dessiner grâce à une API JavaScript. On peut y placer des images, du texte, des formes géométriques et les animer.

## Audio

La balise `<audio>` permet de lire un fichier audio (au format MP3 ou OGG selon les navigateurs). L'attribut *controls* fait apparaître une interface permettant de contrôler la lecture. Elle peut également être contrôlée par JavaScript.

On peut utiliser la balise *source* pour spécifier plusieurs fichiers dans des formats différents :

    <audio>
        <source src="audio.mp3" type="audio/mp3">
        <source src="audio.ogg" type="audio/ogg">
    </audio>

Le navigateur choisira alors le format qui lui convient.

## Vidéo

La balise `<video>` fonctionne comme la balise `<audio>`. Elle permet de s'affranchir des plugins comme Flash ou QuickTime pour la lecture des vidéos. De plus, les vidéos sont contrôlables par JavaScript et modifiables par CSS. Le format recommandé pour une compatibilité maximum est [WebM](http://www.webmproject.org/).

## Formulaires

HTML5 ajoute plusieurs types à la balise `<input>` :

* *search* : Un champ imitant le champ de recherche du système
* *e-mail* : Champ pour un e-mail (le navigateur vérifiera si cela ressemble bien à une adresse e-mail)
* *range* : Une glissière
* *number* : Pour des nombres uniquement (avec des boutons *+* et *-* dans certains navigateurs)
* *date* : Un calendrier
* *color* : Un sélecteur de couleur (au format hexadécimal)

Il ajoute également de nouveaux attributs :

* *autofocus* : Le champ est sélectionné automatiquement à l'ouverture de la page
* *placeholder* : Un texte à afficher tant que le champ n'est pas rempli
* *required* : Il faut remplir ce champ pour pouvoir valider le formulaire

## Balises sémantiques

HTML5 ajoute des balises qui fonctionnent comme des `<nowiki><div></nowiki>` mais ont une valeur sémantique supplémentaire (elles permettent de donner des indications sur la structure de la page) :

* *header* : En-tête de la page ou d'une section
* *footer* : Pied de page
* *nav* : Menu de navigation
* *section* : Une section d'un document (généralement avec son propre en-tête)
* *article* : Un article ou un contenu qui se suffit à lui-même
* *aside* : Un contenu indirectement relié au contenu principal de la page

Il ajoute également quelques éléments sémantiques en ligne (qui agissent comme des `<nowiki><span></nowiki>`) :

* *time* : Permet d'indiquer une date et son équivalent au format ISO (via l'attribut *datetime*)
* *mark* : Permet de surligner un mot-clef mis en avant comme un résultat de recherche

## Géolocalisation

La fonction `navigator.geolocation.getCurrentPosition` permet d'obtenir les coordonnées de l'utilisateur, ce qui permet, par exemple, de les afficher sur une carte.

Pour déterminer la localisation, le navigateur utilise, selon ce qui est disponible :

* L'adresse IP ;
* Une triangulation avec les réseaux wi-fi ;
* Une triangulation avec les bornes GSM.

## Stockage local

L'objet JavaScript *localStorage* permet de stocker des chaînes (voire des objets plus complexes si on les convertit en JSON) avec d'enregistrer des informations sur l'utilisateur, des préférences, un historiques

L'avantage de cette fonctionnalité, par rapport à d'autres technologies comme les cookies, est de pouvoir fonctionner hors-ligne.

## Pages hors ligne

La variable `navigator.onLine` permet de vérifier si le navigateur est connecté à Internet et, dans le cas contraire, de travailler localement en attendant de pouvoir synchroniser les données avec le serveur.

Il est également possible de stocker toute une application localement avec un [manifeste de cache](https://developer.mozilla.org/en-US/docs/HTML/Using_the_application_cache).

## Micro-données

Les micro-données permettent de donner des indications supplémentaires aux moteurs de recherche sur le contenu de la page. On utilise pour cela des propriétés issues d'un vocabulaire commun. Le vocabulaire le plus utilisé est celui de [Schema.org](http://schema.org/).

## Historique

La fonction `history.pushState` permet d'ajouter des éléments factices à l'historique du navigateur. Ces éléments peuvent être utilisés pour revenir à différents états d'une application web.

## Liens utiles

* [html5shiv](http://code.google.com/p/html5shiv/)
* [Modernizr](http://modernizr.com/)
* [Can I use...](http://caniuse.com/)
* [HTML5 sur le site de Mozilla](https://developer.mozilla.org/en-US/docs/HTML/HTML5)
* [La spécification HTML 5.1](http://www.w3.org/TR/html51/)

## Bibliographie

* Keith, Jeremy, *HTML5 for Web Designers*
* Pilgrim, Mark, *HTML5: Up and Running*
* Pilgrim, Mark, *[Dive Into HTML5](http://diveintohtml5.info/)*
