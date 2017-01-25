# Initiation au PHP

## Introduction

### Qu'est-ce que PHP

est un langage de programmation créé en 1994 par Rasmus Lerdorf. Il est multiplate-forme. La dernière version est la version 5, mais on trouve encore relativement fréquemment la version 4.

### À quoi ça sert

En théorie, comme la plupart des langages de programmation, PHP peut servir à créer des programmes en ligne de commande, des applications *desktop*. Dans la pratique, il est surtout utilisé pour créer des sites web dynamiques

Il est utilisé par de nombreux sites :

* *unistra.fr*
* *facebook.com*
* *wikipedia.org*

Et par de nombreux :

* WordPress
* Joomla
* SPIP

### Page web statique

Une page statique est une page qui est identique quelle que soit la requête de l'utilisateur. Pour afficher une page statique, le serveur se contente de retourner le contenu du fichier demandé par l'utilisateur. Un site statique oblige donc à avoir autant de fichiers que de pages web, ce qui peut convenir à de petits sites mais devient vite ingérable sur de gros sites.

### Page web dynamique

Dans le cas d'une page dynamique, le serveur va exécuter un programme (ici en PHP) qui va analyser la requête de l'utilisateur (page demandée, mots entrés dans un formulaire) et générer une page adaptée. Cela permet par exemple de lancer une recherche en fonction des mot-clés entrés par l'utilisateur.

### On utilise PHP avec

* Un système d'exploitation : Bien que le système le plus courant pour les ordinateurs personnels soit Windows, on utilise souvent Linux sur les serveurs web.
* Un serveur web : Il s'agit du logiciel qui va s'occuper de recevoir et traiter les requêtes de l'utilisateur, puis de lui renvoyer le contenu demandé. L'un des plus courants est [Apache](http://httpd.apache.org/).
* Une base de données : Il s'agit d'un logiciel permettant de structurer et classifier facilement une grande quantité d'informations. On utilise souvent [MySQL](http://www.mysql.fr/) pour le web.

On parle donc souvent d'environnement LAMP et c'est ce que nous allons étudier ici.

### Utiliser PHP

Comme il peut être fastidieux pour un débutant d'installer Apache, PHP et MySQL séparément, il existe des paquets contenant les trois qui permettent de se lancer rapidement dans le développement. Sur Windows, il existe [EasyPHP](http://www.easyphp.org/) et sur Mac OS, il y a [MAMP](http://www.mamp.info/en/index.html). Sur Linux, il faut généralement installer le paquet *libapache2-mod-php5*.

### Les fichiers PHP

Les fichiers PHP utilisent généralement l'extension *.php*. Ce sont des fichiers textes qui doivent être édité avec un éditeur comme [Notepad++](http://notepad-plus-plus.org/fr/) ou [Geany](http://www.geany.org/). Les fichiers PHP commencent par `<?php` et finissent par `?>`. Ce ne sont pas des programmes en soit, ils doivent d'abord interprétés par un interpréteur PHP (le module PHP d'Apache, par exemple).

### Fonctions

Une fonction est une portion de code qui effectue une tâche. Les fonctions permettent de demander à l'ordinateur d'effectuer une action. En PHP, elles s'utilisent comme suit : `fonction(argument1, argument2);`

On donne tout d'abord le nom de la fonction puis on indique les paramètres entre parenthèses. On remarque qu'une instruction se finit toujours par *;*.

#### La fonction *echo()*

Cette fonction permet d'afficher un message dans le navigateur. Exemple : `echo("Bonjour !");` Cela va afficher dans la page, à l'endroit où se trouve la fonction.

*echo()* est souvent utilisée pour générer des bouts de HTML : `<h1><?php echo("Introduction à PHP"); ?></h1>`

### Commentaires

Les commentaires sont ignorés par l'interpréteur, ils n'ont aucun effet dans le code. Ils servent simplement à donner des indications aux personnes qui liront le code. En PHP, il existe deux types de commentaires :

Les commentaires sur une ligne : `//Blabla`
Les commentaires de plusieurs lignes :

```php
/*Blabla
et
blablabla*/
```

On place souvent des commentaires en début de fichier pour indiquer à quoi sert le fichier, d'où il vient, son auteur :

```php
/**
 * Exemple montrant l'utilisation de PHP dans un fichier HTML
 *
 * PHP Version 5.3.10
 *
 * @category Exemples
 * @package  CoursPHP
 * @author   Pierre Rudloff <foo@strasweb.fr>
 * @license  GNU General Public License http://www.gnu.org/licenses/gpl.html
 * @link     http://rudloff.pro/cours/PHP/
 * */
```

### Variables

Les variables attribuent une valeur à un nom. Elles permettent de manipuler des valeurs qui resteront accessibles dans tout le programme. Elles se notent de cette façon : `$variable=valeur;`

#### Variables de base (ou variables scalaires)

Entiers : Une variable peut contenir un nombre entier (5, 10, 280976).
Nombres décimaux : Une variable peut contenir un nombre décimal (2.54, -56.5).

À noter que les entiers et les décimaux peuvent avoir une valeur négative.

Chaînes : Une chaîne de caractères est une suite de caractères plus ou moins longue : un mot, une phrase, voire un texte ('bonjour', "Au revoir."). Les chaînes doivent être entourées de *'* ou *"*.

#### Tableaux

##### Tableaux simples

Ils permettent de lister des valeurs. Ils se notent de cette façon : `array(valeur1, valeur2);`

Exemple : `$fruits=array("pommes", "poires", "abricots");`

Pour accéder à une des valeurs, on utilise la notation suivante : `$fruits[1]` Attention, la liste commence à 0, donc `$fruits[1]` renvoie ici *poires*.

Les tableaux évitent d'avoir à créer beaucoup de variables (`$fruit1`, `$fruit2`).

##### Tableaux associatifs

Ils permettent d'associer chaque valeur à un mot-clef plutôt qu'à un numéro : `array(clef1=>valeur1, clef2=>valeur2);`

Exemple :

```php
//Tableau associatif
$utilisateur=array("prénom"=>"Jacques", "nom"=>"Dupont");
echo($utilisateur["nom"]);
```

### *\$\_GET*

La variable *\$\_GET* est définie par PHP, il n'y a pas besoin de la créer. C'est un tableau qui contient des paramètres récupérés dans l'URL de la page sous la forme `?var1=valeur1&var2=valeur2`.

Exemple : Si on a comme URL *get.php?variable=blabla*, alors `$_GET["variable"]` donnera *blabla*.

### *include* et *require*

Ces deux fonctions permettent d'inclure le contenu d'un fichier dans un autre de cette façon : `include "autre_fichier.php";`

(Les parenthèses ne sont pas nécessaires.)

La différence entre les deux est que *require* arrête le script si le fichier est introuvable alors qu'*include* continue.

Ces fonctions sont particulièrement utile si un contenu est le même sur toutes les pages d'un site (le menu, par exemple). Il suffit alors de mettre ce contenu dans un fichier séparé et de l'inclure dans chacune des pages. Cela permet de pouvoir modifier ce fichier une seule fois et pas dans chaque page.

## [Structures de contrôle](http://www.php.net/manual/fr/language.control-structures.php)

Les structures de contrôle sont des commandes qui contrôlent l'ordre dans lequel les différentes instructions d'un programme sont exécutées.

### Variables booléennes

Les variables booléennes ont deux valeurs possibles : *true* et *false* (sans guillemets). Elles permettent d'enregistrer un paramètres binaire (on/off, activé/désactivé, correct/faux). Elles sont particulièrement utiles pour les conditions.

### Conditions

Les conditions permettent de contrôler la façon dont les instructions du programme sont effectuées en fonction de critères prédéfinis.

#### *if*

La structure *if* permet de tester une condition. Cela permet d'adapter le programme en fonction de la valeur d'une variable.

Elle s'utilise de la façon suivante :

    if (condition) {
        instruction;
    }

Si la condition se vérifie (si elle renvoi *true*), les instructions contenues dans les accolades sont exécutées, sinon elles sont ignorées.

On peut utiliser *if* simplement pour vérifier qu'une variable à la valeur *true* :

    if ($bool) {
        //Vrai
    } //Equivalent à :
    if ($bool==true) {
        //Vrai
    }

Ou bien, on peut utiliser des comparaisons :

* *==* : égal à
* *!=* : inégal à
* *\>* : supérieur à
* *\<* : inférieur à
* *\>=* : supérieur ou égal à
* *\<=* : inférieur ou égal à
* *===* : strictement égal à
* *!==* : strictement inégal à

Exemple :

<!-- -->

    if ($num>2) {
        echo("Ce nombre est plus grand que 2.");
    }

L'opérateur *===* compare le type en plus de comparer la valeur :

    //Comparaison stricte
    if ("12"==12) {
        //Vrai
    }
    if ("12"===12) {
        //Faux
    }

#### *else* et *elseif*

Ces structures permettent d’enchaîner plusieurs conditions :

    if (condition1) {
        instruction1;
    } elseif (condition2) {
        instruction2;
    } else {
        instruction3;
    }

Si *condition1* est vrai, alors *instruction1* est exécuté, mais s'il est faux *condition2* est testé. Si toutes les conditions sont fausses, le bloc *else* est exécuté.

#### *switch*

*switch* permet d'éviter beaucoup de *elseif*.

    switch ($var) {
    case valeur1:
        instruction1;
    case valeur2:
        instruction2;
    }

La structure ci-dessus est équivalente à la structure suivante :

    if ($var==valeur1) {
        instruction1;
    } elseif ($var==valeur2) {
        instruction2;
    }

Ce genre de structure est donc utile quand une variable à un grand nombre de valeurs possibles et qu'on veut les tester une à une.

On peut utiliser *default* pour donner une instruction par défaut (équivalent à *else*) :

    if (isset($page)) {
        switch ($page) {
        case "accueil":
            //On affiche la page d'accueil
        case "contact":
            //On affiche le formulaire de contact
        default:
            //On affiche la page par défaut
        }
    }

#### Conditions multiples

On a parfois besoin de tester beaucoup de conditions similaires :

    if ($num==12) {
        echo("Ce nombre est un multiple de 12.");
    } else if ($num==24) {
        echo("Ce nombre est un multiple de 12.");
    } else if ($num==48) {
        echo("Ce nombre est un multiple de 12.");
    }

Il devient alors plus simple d'utiliser les opérateurs logiques *&&* et *||*.

*&&* permet de tester en une fois si deux conditions sont vraies :

    if ($participants>$min && $participants<$max) {
        echo("Il y a le bon nombre de participants.");
    }

La fonction *echo* ne sera exécutée que si *\$participants* est supérieur à *\$min* **et** inférieur à *\$max*.

*||* permet de vérifier si une de plusieurs conditions est vraie :

    if ($user==$admin1 || $user==$admin2 || $user==$admin3) {
        echo("Accès autorisé");
    }

La fonction *echo* sera exécutée si *\$user* est égal à *\$admin1*, *\$admin2* ou *\$admin3*.

On peut enchaîner autant de *&&* et *||* que nécessaire et on peut combiner les deux. Il est par contre conseillé d'utiliser des parenthèses pour clarifier l'ordre dans lequel sont effectués les tests :

    if (($user==$admin1 || $user==$admin2 || $user==$admin3) && ($connected)) {
        echo("Accès autorisé");
    }

### Boucles

Les boucles permettent d'exécuter une même instruction plusieurs fois.

#### *for*

Le moyen le plus courant de faire une boucle est d'utiliser la structure *for* :

    for (départ ; fin ; incrémentation) {
        instruction;
    }

Exemple :

<!-- -->

    for ($i=1; $i<=5; $i+=1) {
        echo('Passage n°'.$i.'<br/>');
    }

On utiliser une variable (généralement nommée *\$i*) qui servira à compter le nombre d'itérations de la boucle. Les trois paramètres à fournir à *for* sont :

* La valeur de départ de *\$i*
* La condition d'exécution de la boucle (`$i<=5` signifie que la boucle continuera tant que *\$i* sera inférieur ou égal à 5.)
* Une opération exécutée à la fin de chaque itération (`$i+=1` signifie qu'on rajoute 1 à *\$i* à chaque fois.)

La boucle ci-dessus produira donc le résultat suivant :

    Passage n°1<br/>Passage n°2<br/>Passage n°3<br/>Passage n°4<br/>Passage n°5<br/>

Il faut faire attention à ce qu'une boucle ait toujours une fin qui soit atteignable, sinon on crée une boucle infinie qui risque de bloquer le programme :

    for ($i=1; $i<=5; $i-=1) {
        //$i n'aura jamais la valeur 5 !
    }

#### *foreach*

La structure *foreach* permet de parcourir toutes les lignes d'un tableau :

    $notes=array(9, 13, 11, 18, 15, 18, 17, 6, 18, 10, 19, 1, 6, 18);
    foreach ($notes as $note) {
        //Instruction
    }

Le mot-clef *as* permet d'assigner à la variable qui le suit (ici *\$note*) le contenu de l'élément du tableau qu'on est en train de traiter. À chaque passage de la boucle, la variable *\$note* aura donc la valeur contenue dans la ligne en cours (*9*, *13*, *11*).

On peut également utiliser *foreach* sur un tableau associatif :

    //Tableau associatif
    $user=array(
        'Prénom'=>'Scott',
        'Nom'=>'McCloud',
        'Âge'=>52,
        'Nationalité'=>'américaine',
        'Ville'=>'Boston'
    );

    //Récupérer toutes les clefs et valeurs
    foreach ($user as $info=>$value) {
        echo($info.' : '.$value.'<br/>');
    }

Ici, la variable *\$info* contiendra le nom de la clef en cours (*Prénom*, *Nom*) et *\$value* contiendra la valeur correspondant à cette clef (*Scott*, *McCloud*).

## Liens utiles

* [Documentation officielle de PHP](http://www.php.net/docs.php)
