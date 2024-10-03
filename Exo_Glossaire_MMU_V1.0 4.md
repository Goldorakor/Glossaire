# GLOSSAIRE

- [Général](#général)
- [Front-end](#front-end)
- [UX / UI](#ux-ui)
- [Architecture](#architecture)
- [Modélisation / Base de données](#modélisation---base-de-données)
- [Symfony](#symfony)
- [Sécurité](#sécurité)
- [RGPD](#rgpd)
- [SEO](#seo)
- [Gestion de projets / DevOps](#gestion-de-projets---devops)
- [English](#english)


## Général

1.	Quel est l’environnement à installer pour exécuter un script PHP ? Citer 2 exemples de logiciels permettant ce contexte.

Il faut installer un serveur local sur son ordinateur, qui pourra interpréter le code PHP car le navigateur n'en est pas capable.
Précisément, il faut un serveur web (Apache est un choix fréquent), un interpréteur PHP (on choisit la dernière version stable de PHP) et une base de données si notre script interagit avec une base de données (un choix fréquent est MySQL).

Laragon inclut le serveur web Apache et la base de données MySQL (visibles sur la fenêtre menu) et propose plusieurs versions de PHP. C'est un environnement préconfiguré qui inclut ce dont on a besoin.

XAMPP permet également de créer un environnement de développement local pour PHP. C'est une alernative à Laragon.

2.	Qu’est-ce qu’un algorithme ?

Un algorithme est une succession finie d'instructions claires et de règles bien définies, à réaliser pour résoudre un problème ou effectuer une tâche complexe. On doit garder en mémoire qu'il doit être efficace (temps d'exécution le plus court possible et utilisation des ressources le moins possible).

3.	Qu’est-ce qu’une variable ? Par quel symbole est préfixée une variable en PHP ?

Une variable est un emplacement mémoire qui associe un nom à une valeur. Elle peut être de différents types : nombre entier, nombre à virgule, booléen, chaine de caractères, tableau, etc.

En PHP, une variable est préfixée par le symbole $.

4.	Qu’est-ce que la portée d’une variable ?

La portée d'une variable détermine où elle est accessible dans le code. Une variable définie à l'intérieur d'une fonction n'est en général pas accessible en dehors de cette fonction. 

5.	Qu’est-ce qu’une constante ? Quelle est la différence avec une variable ?

Une constante est une valeur qui, une fois définie, ne sera plus jamais modifiée au cours de l'exécution d'un programme.

Les différences sont :
- la constante n'est pas déclarée avec le symbole $.
- la constante est souvent écrite en majuscule.
- la constante ne sert pas à stocker une valeur (une information) qui peut varier pendant l'exécution du programme.

6.	Qu’est-ce qu’une superglobale, combien en existent-ils et donner un exemple d’utilisation 



7.	Quels sont les différents types (primitifs) que l’on peut associer à une variable en PHP ? Les citer et en donner des exemples (ne pas oublier le type d’une variable sans valeur)

Les différents types que l'on peut associer à une variable en PHP sont :
- une chaine de caracères (string). Exemple : $chaine = "Bonjour"
- un nombre entier (integer). Exemple : $nombre = 4
- un nombre à virgule (float). Exemple : $float = 3.20
- un booléen (boolean). Exemple : Exemple : $bool = true ou $bool = false
- un tableau (array). Exemple : $tableau = [ "élément1" , 4 , 4.20 , "élément5", $variable ] -> un tableau peut contenir toute sorte de choses
- un objet (object). Exemple : $maVoiture = new Voiture [avant de pouvoir créer une instance de la classe Voiture, on a dû définir la classe Voiture au préalable] : 
class Voiture {
    // voici les propriétés de la classe que nous créeons.
    public $marque;
    public $modèle;
    pblic $couleur;
}
-  une variable sans valeur. Exemple : 
-- $maVariable [la variable est déclarée mais n'a pas de valeur initiale, donc elle est non définie : sa valeur est considérée comme NULL]
-- $mavariable2 = NULL [on définit explicitement la variable comme NULL]

* un objet peut contenir des propriétés et des méthodes.

8.	Existe-t-il plusieurs types de tableaux en PHP, si oui lesquels ?

Il existe trois types de tableaux, à savoir les tableaux indexés, les tableaux associatifs et les tableaux multidimensionnels.
Les "tableaux indexés" sont des tableaux dont les éléments sont indexés par des nombres. Par défaut, les indices commencent à 0.
Les "tableaux associatifs"  sont des tableaux dont les éléments sont indexés par des clés nommées. On peut donc accéder aux valeurs par ces clés. Attention, on ne peut npas avoir dans un même tableau deux clés identiques. Par contre, deux clés différentes peuvent avoir la même valeur.
Les "tableaux multidimensionnels" sont des tableaux contenant d'autres tableaux, pour créer des structures de données plus complexes.

9.	Quelles sont les différentes structures de contrôle qu’il existe en algorithmie ? Donner un exemple pour chacune d’entre elles.

Il y a les structures conditionnelles qui permettent de prendre des décisions basées sur des conditions.

a. if :
si (condition) alors
    faire quelque chose
fin si

b : if ... else :
si (condition) alors
    faire quelque chose
sinon
    faire autre chose
fin si

c : switch :
choix variable
    cas valeur1 :
        faire quelque chose
    cas valeur2 :
        faire autre chose
    par défaut :
        faire une autre chose
fin choix


Il y a les structures de répétition (les boucles) qui permettent de répéter un bloc de code plusieurs fois.

a. while :
tant que (condition) faire
    faire quelque chose
fin tant que

La condition est vérifiée avant chaque itération.
Elle est généralement utilisée lorsque le nombre d'itérations n'est pas connu à l'avance et dépend d'une condition dynamique.

b. for : 
pour i de 1 à 10 faire
    faire quelque chose
fin pour

L'initialisation, la condition et l'incrément sont généralement définis dans la même ligne.
Elle est souvent utilisée lorsque le nombre d'itérations est connu à l'avance.

c : do ... while :
faire
    faire quelque chose
tant que (condition)

Le bloc de code est exécuté au moins une fois, car la condition est vérifiée après l'exécution du code.
Elle est utile lorsque vous souhaitez garantir qu'une action est effectuée au moins une fois, indépendamment de la condition.


Il y a les structures de saut qui permettent de modifier le flux d'exécution en sautant à d'autres parties du code.

a. break (utilisé pour sortir d'une boucle ou d'une structure de contrôle) : 
pour i de 1 à 10 faire
    si (i = 5) alors
        sortir
    fin si
fin pour

b. continue (utilisé pour sauter à l'itération suivante d'une boucle) : 
pour i de 1 à 10 faire
    si (i est pair) alors
        continuer
    fin si
    faire quelque chose
fin pour

c. return (utilisé pour sortir d'une fonction et éventuellement renvoyer une valeur) : 
fonction somme(a, b)
    retourner a + b
fin fonction


10.	Quelle est la fonction PHP permettant de demander la longueur d’une chaîne de caractères ?

La fonction PHP permettant de demander la longueur d’une chaîne de caractères est : strlen (). Cette fonction compte tous les caractères, y compris les espaces et la ponctuation.
ATTENTION : si la chaine contient des caractères spéciaux, on préfèrera utiliser la fonction mb_strlen().

11.	Qu’est-ce qu’une session ? Quelle fonction permet de démarrer une session en PHP ? Donner un exemple d’utilisation en PHP.

Une session en PHP est un mécanisme qui permet de stocker des données "utilisateur" sur le serveur afin de les conserver entre différentes requêtes HTTP. 
La fonction session_start() permet de démarrer une session en PHP.
Sur un site marchand, la session permet de conserver le contenu du panier d'achat jusqu'à la finalisation de la commande.

12.	Qu’est-ce qu’un cookie ? Donner un exemple d’utilisation en PHP.



13.	Quelle est la différence entre les instructions «require» et «include» en PHP ?

Ces instructions sont utilisées pour inclure le contenu d'un fichier dans un autre fichier. Mais elles présentent des différences en terme de comportement et d'utilisation.

Si le fichier spécifié ne peut pas être inclus, "require" génère une erreur fatale et arrête l'exécution du script : si le fichier est essentiel pour le fonctionnement du programme, l'utilisation de "require" est donc appropriée.

Si le fichier ne peut pas être inclus, "include" génère un avertissement et le script continue à s'exécuter. Cela peut être utile si le fichier est optionnel ou si vous voulez que le programme continue même en cas d'erreur.

En résumé, choisissez "require" lorsque le fichier est indispensable au fonctionnement du script et "include" lorsque le fichier est optionnel. Les variantes "require_once" et "include_once" permettent d'éviter les inclusions multiples, garantissant que le contenu du fichier est exécuté une seule fois.

14.	Comment effectuer une redirection en PHP ?

15.	Définir la partie « front-end » et « back-end » d’une application.

La partie front-end d'une application contient toute la partie visible par l'utilisateur. Elle contient donc la partie "contenu informatif du site" et la partie "mise en forme du site". Les langages associés à cette partie sont le HTML et le CSS.
- HTML pour fournir du contenu et le structurer.
- CSS pour la mise en forme et la gestion graphique du site. 
Mon navigateur gère parfaitement l'affichage du front-end et je peux développer sans outil particulier. Le logiciel VSCode fait très bien le travail demandé.

La partie back-end d'une application contient toute la machinerie cachée qui permet un bon fonctionnement de mon application. Le langage associé à cette partie est le PHP (en ce qui me concerne).
- PHP pour aller envoyer des requêtes au serveur.
Mon navigateur ne gère pas correctement le langage PHP. En plus du logiciel VSCode, je vais installer Laragon, qui va me fournir les outils adaptés au besoin du développement en PHP.

16.	Définir le contrôle de version ? Qu’est-ce que Git ?

Le contrôle de version est un système qui enregistre les modifications apportés à des fichiers au fil de l'avancement d'un projet. 
- On sait quelle modification a été faite, qui a fait la modification et quand elle a été faite.
- On garde un historique complet des versions des fichiers, pour revenir facilement à une version ancienne si besoin.
- On peut travailler à plusieurs sur un même projet, en travaillant chacun sur sa propre copie des fichiers.
- On peut créer des branches pour travailler sur des fonctionnalités séparement puis fusionner ces branches à la branche principale.
- En cas de conflits, on a à disposition des outils pour les résoudre.

Git est un logiciel de contrôle de version très populaire, utilisé pour la gestion de code source. Utilisé avec la plateforme en ligne GitHub, il permet en plus une gesion décentralisée.

17.	Qu’est-ce qu’un CMS ? Citer au moins 2 exemples.

Un CMS (Content Management System), aussi appelé système de gestion de contenu, est un logiciel qui permet de créer, gérer et modifier du contenu numérique sur un site web sans compétences techniques avancées en programmation.

Deux exemples de CMS : WordPress et Shopify.

## Front-end
18.	Définir HTML

HTML (HyperText Markup Language) est un langage de balisage qui permet d'ajouter du contenu et de le structurer, pour la création d'une page web. Il permet entre autres de créer des liens hypertextes qui relient différentes pages web entre elles. Il s'utilise avec d'autres langages informatiques.

19.	Définir CSS

CSS (Cascading Style Sheets) est un langage informatique utilisé pour contrôler l'apparence visuelle d'une page web. Il permet de bien contrôler la disposition des éléments sur une page et le design de chaque élément. C'est vraiment le langage pour styliser et mettre en forme sa page web. Il s'utilise avec d'autres langages informatiques.

ATTENTION : CSS peut être intégré dans un document HTML comme suit : En liant une feuille de style externe via une balise <link> dans la section <head>.
- <link rel="stylesheet" href="styles.css">
C'est la méthode la plus propre pour intégrer du CSS dans un document HTML et c'est la méthode à utiliser par la suite. Le CSS est rangé proprement dans un fichier CSS à part.

20.	Définir Javascript

Je n'utilise pas encore ce langage informatique. C'est l'un des 3 piliers du développement web, avec HMTL et CSS. 


21.	Définir JSON. Dans quel contexte ce format est-il utilisé ? 



22.	Peut-on interpréter du Javascript côté serveur ? Si oui, comment ?



23.	Qu’est-ce qu’un sélecteur CSS ?

Un sélecteur CSS est un élément qui permet de cibler des éléments HTML spécifiques pour leur appliquer des styles. Les sélecteurs CSS sont des outils puissants qui permettent de cibler des éléments HTML pour appliquer des styles de manière précise et flexible.
On notera comme différents sélecteurs :

- le sélecteur de type qui cible tous les éléments d'un type particulier (balise). (je connais)
p {
    color: blue; /* Tous les paragraphes seront bleus */
}

- le sélecteur de classe qui cible tous les éléments ayant une classe spécifique, préfixée par un point (.). (je connais)
.mon-style {
    font-weight: bold; /* Tous les éléments avec la classe "mon-style" seront en gras */
}

- le sélecteur d'identifiant qui cible un élément unique ayant un identifiant spécifique, préfixé par un dièse (#). (je connais)
#mon-id {
    background-color: yellow; /* L'élément avec l'id "mon-id" aura un fond jaune */
}

- le sélecteur d'attribut qui cible les éléments en fonction de leurs attributs ou de leurs valeurs d'attribut. (jamais utilisé)
a[href] {
    text-decoration: none; /* Tous les liens avec un attribut href n'auront pas de soulignement */
}

- le sélecteur combiné qui combine plusieurs sélecteurs pour cibler des éléments en fonction de leur relation. Trop compliqué pour moi, je ne pense pas l'utiliser pour le moment. (jamais utilisé)

- le sélecteur pseudo-classe qui cible des éléments dans un état particulier. Peut être super utile pour des effets au survol de la souris par exemple. (jamais utilisé)
a:hover {
    color: green; /* Le lien deviendra vert au survol */
}

- le sélecteur pseudo-élément qui cible des parties spécifiques d'un élément. Peut être sympa à utiliser. (jamais utilisé)
p::first-line {
    font-weight: bold; /* La première ligne de tous les paragraphes sera en gras */
}


24.	Quelle balise HTML permet de créer un lien hypertexte ?

La balise qui permet de créer un lien hypertexte est la balise <a></a>.
Exemple : <a href="https://www.example.com">Visitez notre site</a>
attributs :
- href : obligatoire, il spécifie l'URL de la page vers laquelle renvoie le lien.
- target : facultatif, il spécifie comment ouvrir le lien. target="_blank" ouvre le lein dans un nouvel onglet ou une nouvelle fenêtre alors que target="_self" ouvre le lien dans le même onglet.
- title : fournit des informations supplémentaires sur le lien. Ce texte s'affiche généralement en tant qu'info-bulle lorsque l'utilisateur survole le lien.
- download : indique que le lien doit être traité comme un téléchargement. Si cet attribut est présent, le lien déclenche le téléchargement du fichier lié au lieu de naviguer vers celui-ci.

Exemple de code pour une balise <a> avec un attribut download :
<a href="https://www.example.com" 
   target="_blank" 
   title="Visitez notre site" 
   rel="noopener" (notion liée à la sécurité)
   download>
   Télécharger notre brochure
</a>

25.	Qu’est-ce qu’une requête AJAX ?



26.	Quel sélecteur CSS permet de sélectionner tous les éléments d’une classe spécifique ? D’un identifiant spécifique ?

Le premier s'appelle le sélecteur de classe qui cible tous les éléments ayant une classe spécifique, préfixée par un point (.). (je connais)
.mon-style {
    font-weight: bold; /* Tous les éléments avec la classe "mon-style" seront en gras */
}

Le deuxième s'appelle le sélecteur d'identifiant qui cible un élément unique ayant un identifiant spécifique, préfixé par un dièse (#). (je connais)
#mon-id {
    background-color: yellow; /* L'élément avec l'id "mon-id" aura un fond jaune */
}

27.	Définir le responsive design

Le responsive design est une approche de conception web qui vise à créer des sites et des applications capables de s'adapter à une variété de tailles d'écran.

28.	Qu’est-ce que le templating ?



29.	Qu’est-ce qu’une fonction anonyme en Javascript ?



30.	Quelle méthode JavaScript est utilisée pour ajouter un élément à la fin d'un tableau ?



31.	Qu’est-ce qu’un « media query » ?

Une instruction pour appliquer des styles différents en fonction des caractéristiques du dispositif, telles que la largeur de l'écran, la résolution, ou l'orientation (portrait ou paysage).
@media (max-width: 600px) {
    body {
        background-color: lightblue; /* Applique un fond bleu clair sur les petits écrans */
    }
}

32.	Qu’est-ce qu’un pseudo-élément en CSS ?

En langage CSS, un pseudo-élément est un mot-clé (before, after, first-line, first-letter, etc) qui permet de sélectionner et de styliser une partie spécifique d'un élément HTML. Il ne cible pas des éléments entiers comme les sélecteurs classiques le font mais il applique des styles à des sous-éléments virtuels sans avoir à ajouter des éléments HTML supplémentaires. Les pseudo-éléments sont préfixés par deux deux-points (::), ce qui les distingue des pseudo-classes (comme :hover ou :focus, qui utilisent un seul deux-points). En conclusion, les pseudo-éléments sont un outil puissant en CSS pour styliser des parties spécifiques d'un élément sans modifier le HTML.

Exemple 01 : ::before, qui insère du contenu avant le contenu d'un élément sélectionné.
p::before {
    content: "Note : "; /* Ajoute "Note : " avant chaque paragraphe */
    font-weight: bold;
}

Exemple 02 : ::after, qui insère du contenu après le contenu d'un élément sélectionné.
p::after {
    content: " (fin)"; /* Ajoute " (fin)" après chaque paragraphe */
    font-style: italic;
}

Exemple 03 : ::first-line, qui cible la première ligne de texte d'un élément.
p::first-line {
    font-weight: bold; /* La première ligne de tous les paragraphes sera en gras */
}

Exemple 04 : ::first-letter, qui cible la première lettre d'un élément.
p::first-letter {
    font-size: 2em; /* Agrandit la première lettre de chaque paragraphe */
    float: left; /* Permet de créer un effet de lettrine */
}

33.	Qu’est-ce que Bootstrap ? Donner d’autres exemples équivalent.



34.	Quand un formulaire HTML est créé, quelles sont les 2 méthodes qui peuvent lui être associées ? Donner la différence entre ces 2 méthodes.



## UX UI

35.	Quelle est la différence entre UX Design et UI Design ?

L'UI Design se concentre sur l'apparence et la présentation de l'interface alors que l'UX Design se concentre sur l'expérience globale de l'utilisateur.
Pour moi, une UX Design réussie nécessite forcément une UI Design réussie, l'inverse n'est pas vraie : une UI Design réussie n'engendre pas forcément une UX Design réussie, si par ailleurs les fonctionnalités sont mauvaises.

36.	Qu’est-ce qu’un wireframe ?



37.	Qu’est-ce qu’un prototype ? 



38.	Qu’est-ce que la hiérarchie visuelle en UI Design ?



39.	Qu’est-ce que l’accessibilité en UX Design ? 



40.	Qu’est-ce qu’une grille de mise en page ?



41.	Qu’est-ce que la notion d’affordance en UX Design ?



42.	Qu’est-ce qu’un « mobile first design » ?




## Programmation orientée objet (POO)

43.	Donner une définition de la programmation orientée objet 



44.	Qu’est-ce qu’une classe ? Comment la déclare-t-on ?


45.	Qu’est-ce qu’un objet ?


46.	Définir la notion de propriété / attribut / méthode



47.	Qu’est-ce que la visibilité d’une propriété ou d’une méthode ? Citer les différents types de visibilité.




48.	Quelle est la méthode spécifique utilisée pour créer un nouvel objet à partir d’une classe ?




49.	Qu’est-ce que l’encapsulation ?




50.	Que signifie « étendre une classe » ? Quelle est le concept clé mis en œuvre ? Donner un exemple.




51.	Définir l’opérateur de résolution de portée.




52.	Définir une méthode / propriété statique.




53.	Définir le polymorphisme en POO.




54.	Définir une méthode / classe abstraite ?




55.	Définir le chaînage de méthodes.




56.	Qu’est-ce que la méthode __toString() ? Existe-t-il d’autres méthodes « magiques » ?




57.	Qu’est-ce qu’un « autoload » ?




58.	Comment appelle-t-on en français les « getters » et les « setters » ?




59.	Qu’est-ce que la sérialisation en PHP ? 





## Architecture 
60.	Qu’est-ce que l’architecture client / serveur ? Grâce à quel type de requête peut-on interroger le serveur. Définir l’acronyme de ce type de requête. Si on ajoute un « S » à cet acronyme, expliquer la différence
61.	Donner la définition d’un design pattern. Citer au moins 3 exemples de design pattern
62.	Qu’est-ce que l’architecture MVC ?
63.	Quel est le rôle de chaque couche du design pattern MVC : Model, View, Controller ?
64.	Quels sont les avantages de l’architecture MVC ?
65.	Existe-t-il des variantes à l’architecture MVC ?
66.	Qu’est-ce qu’une API ? Définir l’architecture REST

## Modélisation - Base de données
67.	Qu’est-ce que la modélisation de données ? Définir la méthode Merise
68.	Quelles sont les 3 étapes principales de la méthode Merise ? 
a.	Analyse, conception et réalisation
b.	Planification, exécution et contrôle
c.	Création, modification et suppression
69.	Qu’est-ce qu’un modèle conceptuel de données (MCD) en Merise ?
70.	Qu’est-ce qu’un modèle logique de données (MLD) en Merise ?
71.	Donner la définition des mots suivants :
a.	Entité
b.	Relation
c.	Cardinalité
d.	Clé primaire / clé étrangère
72.	Que devient une relation de type « Many To Many » dans le modèle logique de données ?
73.	Qu’est-ce qu’une base de données ?
74.	Définir les notions suivantes : 
a.	SQL
b.	MySQL
c.	SGBD (donner 2 exemples de SGBD)
75.	Dans une base de données, les données sont stockées dans des ___. Celles-ci sont constituées de lignes appelées ___ et de colonnes appelées ___
76.	Quelle est la différence entre une base de données relationnelle et non relationnelle ?
77.	Qu’est-ce qu’une jointure dans une base de données ? En existe-t-il plusieurs ? Si oui lesquelles ?
78.	A quoi sert une vue dans une base de données ?
79.	Qu’est-ce que l’intégrité référentielle dans une base de données ?
80.	Quelles sont les fonctions d’agrégation en SQL ?
81.	Qu’est-ce qu’un CRUD dans le contexte d’une base de données ?
82.	Quelles sont les clauses qui permettent de :
a.	Insérer un nouvel enregistrement dans une table
b.	Modifier un enregistrement dans une table
c.	Supprimer un enregistrement dans une table
d.	Supprimer la base de données
e.	Filtrer les résultats d’une requête SQL
f.	Trier les résultats d’une requête SELECT
g.	Regrouper les résultats d'une requête SELECT en fonction d'une colonne spécifique
h.	Concaténer 2 chaînes de caractères 
83.	Comment se connecter à une base de données en PHP ? Quelle est la classe native utilisée ?

## Symfony
84.	Qu’est-ce que Symfony ?
85.	Sur quel langage de programmation et design pattern repose Symfony ? 
86.	Quelle est la dernière version en date de Symfony ?
87.	Qu’est-ce qu’un bundle ? 
88.	Quel est le moteur de template utilisé par défaut dans Symfony ?
89.	Qu’est-ce qu’un ORM ? Quel est son utilité et comment s’appelle-t-il au sein de Symfony ?
90.	Qu’est-ce que l’injection de dépendances ? Quel est l’outil utilisé dans ce contexte et quel fichier contient l’intégralité des dépendances du projet ?
91.	Que permet le bundle Maker au sein de Symfony ? 
92.	Quel est le langage de requêtage exploité au sein d’un projet Symfony ?
93.	Quel est le composant qui garantit l’authentification et l’autorisation des utilisateurs ?

## Sécurité
94.	Qu’est-ce que l’injection SQL ? Comment s’en prémunir ?
95.	Qu’est-ce que la faille XSS ? Comment s’en prémunir ?
96.	Qu’est-ce que la faille CSRF ? Comment s’en prémunir ?
97.	Définir l’attaque par force brute et l’attaque par dictionnaire
98.	Existe-t-il d’autres failles de sécurité ? Citer celles-ci et expliquer simplement leur comportement
99.	A quoi servent l’authentification et l’autorisation dans un contexte d’application web ?
100.	Définir la notion de hachage d’un mot de passe et citer des algorithmes de hachage
101.	Qu’est-ce qu’une politique de mots de passe forts ?
102.	Qu’est-ce que l’hameçonnage ?
103.	Définir la « validation des entrées »

## RGPD
104.	Qu’est-ce que le RGPD ?



105.	Quel est son objectif principal ?



106.	Quelle est la date d’entrée en vigueur du RGPD ?



107.	Quelles sont les sanctions possibles en cas de non-respect du RGPD ?



108.	En France, quel est l’autorité administrative qui s’occupe de faire appliquer le RGPD ?



109.	Quel est le consentement valide selon le RPGD ?



110.	Qu’est-ce qu’une politique de confidentialité ?



111.	Quelle est la durée de conservation maximale des données personnelles selon le RGPD ?



112.	Quels sont les droits des utilisateurs selon le RGPD ?



113.	Qu’est-ce que le principe de minimisation des données selon le RGPD ?




## SEO

114.	Qu’est-ce que le SEO ? 



115.	Quel est l’objectif principal du SEO ?



116.	Existe-t-il plusieurs types de référencement ? Lesquels ?



117.	Qu’est-ce que la densité de mots-clés en SEO ?



118.	Qu’est-ce qu’une balise « alt » ?



119.	Qu’est-ce que la balise « meta description » ?



120.	Qu’est-ce que le « nofollow » en SEO ?



121.	Quelle est l'importance du contenu de qualité pour le référencement d'un site web ?



122.	Pourquoi est-il important d'utiliser des balises de titre (h1, h2, h3, etc.) de manière structurée ?



123.	Quelle est la recommandation pour les URL d'un site web bien référencé ?



124.	Qu'est-ce que le maillage interne et pourquoi est-il important pour le référencement ?



125.	Qu'est-ce que l'optimisation des images pour le référencement ?



126.	Qu'est-ce qu'un plan de site (sitemap) et pourquoi est-il important pour le référencement ?




## Gestion de projets - DevOps


127.	Qu’est-ce que la gestion de projet ?	



128.	Qu’est-ce qu’une méthode Agile de gestion de projet ? 



129.	Expliquer la méthode MoSCoW en quelques lignes et citer ses avantages.



130.	A quoi sert la méthodologie MVP ? Citer les caractéristiques clés.



131.	Qu’est-ce que la planification itérative ?



132.	Citer 3 méthodes Agiles dans le cadre d’un projet informatique.



133.	Qu’est-ce qu’une réunion de revue de projet ?



134.	Qu’est-ce qu’un livrable dans un projet ? 



135.	Quels sont les 3 piliers SCRUM ? Définir chacun d’entre eux.



136.	Qu’est-ce que le DevOps et quel est son objectif principal ?



137.	Qu’est-ce que l’intégration continue ? 



138.	Qu’est-ce que Docker ? Et en quoi est-il utile dans le cadre du DevOps ?



139.	Qu’est-ce qu’un test unitaire ? 



140.	Quelle est l'unité de code testée lors d'un test unitaire ?



141.	Quelles sont les caractéristiques d'un bon test unitaire ?



142.	Qu'est-ce qu'une assertion dans un test unitaire ?
 



## English


1)	What does JavaScript enable you to do on a website ?
a.	Add interactive behavior and dynamic content. <--
b.	Define the layout and design of web pages.
c.	Handle server-side operations.


2)	Which programming language is primarily used for server-side web development ?
a.	PHP. <--
b.	JavaScript.
c.	HTML.


3)	What is the purpose of a web browser ?
a.	To render and display web pages. <--
b.	To execute serve-side code.
c.	To manage databases.


4)	What is the difference between GET and POST methods in HTTP ?
a.	GET retrieves data from a server, while POST submits data to a server.
b.	GET submits data to a server, while POST retrieves data from a server.
c.	GET and POST methods are interchangeable.


5)	What is the purpose of version control systems (e.g., Git) in web development ?
a.	To track changes and manage collaborative development.
b.	To optimize website loading speed.
c.	To handle server-side scripting.


6)	What is the purpose of a framework in web development ?
a.	To provide a structured environment for building web applications.
b.	To handle network protocols and data transfer.
c.	To create visual designs and layouts for websites.


7)	What does NoSQL stand for ?
a.	Not Only SQL.
b.	Non-Structured Query Language.
c.	New Object-Oriented Language.


8)	Which of the following is a characteristic of NoSQL databases ?
a.	Strict schema enforcement.
b.	Support for complex transactions.
c.	Scalability and flexible data models.
