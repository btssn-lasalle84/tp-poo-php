<img alt="points bar" align="right" height="36" src="../../blob/badges/.github/badges/points-bar.svg" />

![](https://img.shields.io/badge/Github-Classroom-green.svg) ![PHP Badge](https://img.shields.io/badge/PHP-777BB4?logo=php&logoColor=fff&style=plastic)

# TP POO : PHP

- [TP POO : PHP](#tp-poo--php)
  - [Le langage PHP](#le-langage-php)
    - [Présentation](#présentation)
    - [Le typage](#le-typage)
  - [La syntaxe](#la-syntaxe)
  - [Interprétation de code POO](#interprétation-de-code-poo)
  - [Travaux pratiques](#travaux-pratiques)
    - [Pré-requis](#pré-requis)
    - [Travail demandé](#travail-demandé)
  - [Tests unitaires](#tests-unitaires)
  - [Bac à sable et développement en ligne](#bac-à-sable-et-développement-en-ligne)

**Les objectifs de ce TP sont de s’initier à la programmation PHP en transférant ses connaissances de la programmation orientée objet.**

> Pour les enseignants, ceci est un "petit" devoir pour [Github Classroom](https://btssn-lasalle84.github.io/guides-developpement-logiciel/guide-classroom.html). Il montre l'utilisation des tests unitaires en PHP, la notation automatique et l'insertion d'un badge pour l'affichage de la note.

## Le langage PHP

Cette partie présente les éléments essentiels à connaître sur PHP. Evidemment, cela ne remplace pas un cours ou la documentation officielle du langage.

### Présentation

PHP est un langage de programmation interprété. Il permet la programmation orientée objet. Il est doté d’un typage dynamique faible.

> Le langage PHP a été créé en 1994 par Rasmus Lerdorf pour son site web. C’était à l’origine une bibliothèque logicielle en langage C dont il se servait pour conserver une trace des visiteurs qui venaient consulter son CV. PHP s’appelait alors PHP/FI (_Personal Home Page Tools/Form Interpreter_). En 1997, deux étudiants, Andi Gutmans et Zeev Suraski, ont redéveloppé le coeur de PHP/FI. Ce travail a abouti un an plus tard à la version 3 de PHP, devenu alors PHP (_Hypertext PreProcessor_). Peu de temps après, Andi Gutmans et Zeev Suraski ont commencé la réécriture du moteur interne de PHP. C'est ce nouveau moteur appelé Zend Engine qui a servi de base à la version 4 de PHP. Comme de nombreux projets Open Source, PHP possède une mascotte. Il s’agit de l’éléPHPant, dessiné en 1998 par El Roubio.
![](images/elephpant.png)

Le langage PHP est placé sous une licence libre et fonctionne sur la plupart des plates-formes informatiques (Windows, Unix, GNU/Linux, macOS, Android, iOS, ...).

PHP est un langage de programmation libre principalement utilisé pour produire des pages Web dynamiques via un serveur HTTP, mais il peut également fonctionner comme n’importe quel langage interprété de façon locale (notion de script).

> PHP a permis de créer un grand nombre de sites web célèbres, comme Facebook, Wikipédia, etc.

Ressources :

- Site officiel : https://secure.php.net/
- Documentation : https://www.php.net/docs.php
- Manuel : https://www.php.net/manual/fr/
- Cours PHP : http://tvaira.free.fr/web/cours-php.pdf et http://tvaira.free.fr/web/coursPHP5-OO.pdf
- Autres : http://tvaira.free.fr/web/

Le langage PHP est un langage populaire :

![](images/tiobe.png)

PHP est le langage de programmation web côté serveur le plus utilisé depuis plusieurs années (75 % de part de marché depuis 2010 puis 82 % en 2016). En 2013, PHP était utilisé par plus de 244 millions de sites Web à travers le monde.

### Le typage

Tous les langages de programmation permettent de manipuler des valeurs avec des variables.

Le typage d’une variable consiste à associer à son nom un « type » de donnée.

> Pour rappel, le « type » est la convention d’interprétation (codage) de la séquence de bits qui constitue la variable. Le type de la variable spécifie aussi la longueur de cette séquence (8 bits, 32 bits, 64 bits, ...).

Suivant les langages de programmation, il existe plusieurs manières de considérer le typage :

- Typage statique : il consiste à demander au programmeur de déclarer expressément chaque variable en indiquant son type. Exemples de langage à typage statique : C, C++, Java, C#
- Typage dynamique : il consiste à laisser l’interpréteur réaliser cette opération de typage « à la volée » lors de l’exécution du code. C’est la valeur affectée à la variable qui précisera son type.
Exemples de langage à typage dynamique : **PHP**, Perl, Python, Javascript, bash (shell Linux)
- Typage fort : Un langage de programmation est dit fortement typé lorsqu’il garantit que les types de données employés décrivent correctement les données manipulées. Exemples de langage fortement typé : C++, Java, C#, Python
- Typage faible : Un langage de programmation est dit faiblement typé lorsqu’il ne considère pas comme une erreur les changements de types. Exemples de langage faiblement typé : **PHP**, Javascript, C (car il accepte les transtypages implicites comme par exemple `int` vers `short`)

Le langage PHP est doté d’un **typage dynamique faible**.

Exemple d’utilisation des types en PHP (`type.php`) :

```php
#!/usr/bin/php
<?php
// En PHP : cf. http://php.net/manual/fr/language.types.type-juggling.php
$a = 1; // un entier
$b = 2.5; // un nombre à virgule flottante
$c = "hello"; // une chaîne de caractères
$d = false; // un booléen
$fruits = array('pomme', 'banane', 'fraise'); // un tableau

// afficher le type d'une variable :
var_dump($a); // int(1) cf. is_int() 
var_dump($b); // float(2.5) cf. is_float() 
var_dump($c); // string(5) "hello" cf. is_string()
var_dump($d); // bool(false) cf. is_bool()
var_dump($fruits); // array(3) ... cf. is_array()

// transtypage :
$a = (int)$b; // a vaut 2

// tester le type d'une variable :
echo is_int($a).PHP_EOL;
echo is_numeric($a).PHP_EOL;
// etc ...
?>
```

## La syntaxe

Le langage PHP utilise une syntaxe très proche de celle utilisée en C/C++.

Le code PHP doit être inséré entre les balises `<?php` et `?>` ou `<?` et `?>`.

Les variables sont préfixées par le symbole `$`.

La partie orientée objet du langage est très inspirée de celle de C++ et Java.

Pour accèder aux membres d’un objet, il faut obligatoirement utilisé l’autopointeur `$this`.

L’opérateur de concaténation de chaîne de caractères est le point (`.`).

## Interprétation de code POO

Soit le script PHP `poo.php` :

```php
#!/usr/bin/php
<?php

class Motocyclette
{
    private $cylindree;
    private $vitesseMaximale;
    private $couleur;

    public function __construct($couleur="", $cylindree="125", $vitesseMaximale="130")
    {
        $this->cylindree = $cylindree;
        $this->vitesseMaximale = $vitesseMaximale;
        $this->couleur = $couleur;
    }

    public function getCouleur()
    {
        return $this->couleur;
    }

    public function setCouleur($couleur)
    {
        $this->couleur = $couleur;
    }

    public function affiche()
    {
        echo "cylindree = $this->cylindree cm3".PHP_EOL;
        echo "vitesse maximale = $this->vitesseMaximale km/h".PHP_EOL;
        if(!empty($this->couleur))
            echo "couleur = $this->couleur".PHP_EOL;
    }
}

$MonTacot1 = new Motocyclette();
echo "MonTacot1".PHP_EOL;
$MonTacot1->affiche();
$MonTacot1->setCouleur("bleue");
echo "La couleur de MonTacot1 est ".$MonTacot1->getCouleur()."".PHP_EOL;

$MonTacot2 = new Motocyclette("rouge", "500 cm3"); // typage faible !
echo "MonTacot2".PHP_EOL;
$MonTacot2->affiche();
echo "La couleur de MonTacot2 est ".$MonTacot2->getCouleur()."".PHP_EOL;
?>
```

Question 1. Qu’est-ce que `Motocyclette` ?

Question 2. Qu’est-ce que `$MonTacot1` ?

Question 3. Qu’est-ce que `couleur` ?

Question 4. Qu’est-ce que `affiche()` ?

Question 5. Qu’est-ce que fait `affiche()` ?

Question 6. Qu’est-ce que `__construct()` ?

> A compléter dans le fichier `compte-rendu.md` (au format [Markdown](https://guides.github.com/features/mastering-markdown/)) fourni.

## Travaux pratiques

### Pré-requis

Programmer en PHP sous Ubuntu : https://doc.ubuntu-fr.org/php

La version actuelle est la version 7 sortie en 2016.

Version de PHP :

```sh
$ php --version
PHP 7.2.19-0ubuntu0.18.04.2 (cli) (built: Aug 12 2019 19:34:28) ( NTS )
Copyright (c) 1997-2018 The PHP Group
Zend Engine v3.2.0, Copyright (c) 1998-2018 Zend Technologies
    with Zend OPcache v7.2.19-0ubuntu0.18.04.2, Copyright (c) 1999-2018, by Zend Technologies

$ php -m
...
```

Le script PHP `helloworld.php` :

```php
#!/usr/bin/php
# Mode CLI
# Le code PHP doit être inséré entre les balises '<?php' et '?>' ou '<?' et '?>'

<?php

// un commentaire : mon premier programme PHP !

echo 'Version PHP courante : '.phpversion().''.PHP_EOL;
// PHP_EOL insère le saut de ligne adapté à la situation :
// - en mode CLI : ce sera un '\n'
// - en mode web : ce sera une balise <br>
echo 'Système : '.php_uname().PHP_EOL.PHP_EOL;// Voir aussi :
//phpinfo();

// Le programme

// saisie d'une chaîne de caractères
$langue = readline("Quelle est votre langue (fr, ...) ? ");

// une instruction conditionnelle
if ($langue == "fr") // test de la valeur
//if ($langue === "fr") // test de la valeur et du type
{
    $message = "Bonjour le monde";
}
else
{
    $message = "Hello world";
}

// saisie d'un entier
$nb = readline("Donnez un nombre : ");

$i = 0;
// une boucle
while ($i < $nb)
{
    //echo $message."".PHP_EOL;
    echo $message . " " . ($i + 1) . " fois".PHP_EOL;
    $i += 1;
}

?>
```

> La première ligne sert à préciser le chemin de l’interpréteur précédé des caractères `#!` (le _shebang_) qui exécutera le script. Cette ligne est inutile dans le cas d’une programmation web.

Il existe plusieurs manières d’exécuter un script PHP de façon locale (mode CLI) :

- le rendre exécutable :

```sh
$ chmod +x helloworld.php
$ ./helloworld.php
```

- utiliser l’interpréteur PHP :

```sh
$ php helloworld.php
```

### Travail demandé

Pour l’écriture d’un programme orientée objet en PHP, on désire disposer du concept de `CompteBancaire`.

Un `CompteBancaire` doit posséder un titulaire, un solde et une devise (EUR, USD, ...). Il est possible d’obtenir le nom du titulaire ainsi que le solde et la devise de ce solde. Lorsque l’on crée un compte bancaire, il est possible de préciser le nom du titulaire, le solde initial et la devise sinon il aura des valeurs nulles par défaut (EUR pour la devise).

![](images/classe-compte.png)

Fournir la classe `CompteBancaire` dans `'src/CompteBancaire.class.php'`.

Fournir un programme `compte-bancaire.php` qui permet de répondre aux questions ci-desous.

```php
#!/usr/bin/php
<?php

require_once('src/CompteBancaire.class.php');

// TODO

?>
```

Question 7. Implémenter la classe `CompteBancaire`.

Question 8. Instancier un objet `compte1` en utilisant le constructeur par défaut et un objet `compte2` dont le titulaire est "Bill Gates" dont la fortune est estimée à 105,3 milliards de dollars américains (USD).

Question 9. Donner l’instruction qui permet d’afficher simplement le solde et la devise du `compte2`.

Question 10. Afficher `compte1` et `compte2` avec la méthode `affiche()`.

Exemple :

```sh
Titulaire du compte : Moi
Vous disposez de 599400000 EUR
```

_Bonus :_ Bill Gates a décidé de vous faire un don de 666 millions de dollars américains. Combien reste-t-il sur son compte ?

## Tests unitaires

Il y a une série de tests unitaires pour ce TP qui utilise [PHPUnit](https://phpunit.de/).

Installation :

```sh
$ sudo apt install composer

$ composer require --dev phpunit/phpunit ^9

$ ./vendor/bin/phpunit -v
PHPUnit 9.5.28 by Sebastian Bergmann and contributors.

Usage:
  phpunit [options] UnitTest.php
  phpunit [options] <directory>
...

$ ./vendor/bin/phpunit tests/TestCompteBancaire.php

$ ./vendor/bin/phpunit --testsuite TestCompteBancaire
```

## Bac à sable et développement en ligne

Il est souvent nécessaire de passer par un "bac à sable".

> En informatique, le bac à sable (_sandbox_) est une zone d'essai permettant d'exécuter des programmes en phase de test ou dans lesquels la confiance est incertaine. C'est notamment très utilisé en sécurité informatique pour sa notion d'isolation.

Il existe de nombreux sites web qui fournissent des EDI (Environnement de Développement Intégré) en ligne pour tester du code ou des services : un espace d'apprentissage séparé. Ils permettent aussi d'échanger des exemples.

Quelques sites :

- JSFiddle : https://jsfiddle.net/ pour HTML, CSS et JavaScript
- Codeply : https://www.codeply.com/ pour les frameworks JavaScript
- Coding Ground For Developers : https://www.tutorialspoint.com/codingground.htm pour tout !
    - **PHP : https://www.tutorialspoint.com/execute_php_online.php**
    - Python : https://www.tutorialspoint.com/execute_python3_online.php
    - Markdown : https://www.tutorialspoint.com/online_markdown_editor.php
- Visual Studio Code Online : https://vscode.dev/
- Gitpod : https://www.gitpod.io/
- Codeanywhere (Cloud IDE) : https://codeanywhere.com/

Exercices d’entraînement : http://tvaira.free.fr/web/

---
Thierry Vaira : **[thierry(dot)vaira(at)gmail(dot)com](mailto:thierry.vaira@gmail.com)**
