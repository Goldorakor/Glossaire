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

___
___

## Général
  
  
1.	Quel est l’environnement à installer pour exécuter un script PHP ? Citer 2 logiciels permettant ce contexte.

Il faut installer un **serveur local** sur son ordinateur, qui pourra **interpréter le code PHP** car le navigateur n'en est pas capable.
Précisément, il faut un serveur web (Apache est un choix fréquent), un interpréteur PHP (on choisit la dernière version stable de PHP) et une base de données si notre script interagit avec une base de données (un choix fréquent est MySQL).

Laragon inclut le serveur web Apache et la base de données MySQL (visibles sur la fenêtre menu) et propose plusieurs versions de PHP. C'est un environnement préconfiguré qui inclut ce dont on a besoin.

XAMPP permet également de créer un environnement de développement local pour PHP. C'est une alernative à Laragon.

___

2.	Qu’est-ce qu’un algorithme ?

Un algorithme est une **succession finie d'instructions claires et de règles bien définies**, à réaliser pour **résoudre un problème ou effectuer une tâche complexe**. On doit garder en mémoire qu'il doit **être efficace** (temps d'exécution le plus court possible et utilisation des ressources le moins possible).

___

3.	Qu’est-ce qu’une variable ? Par quel symbole est préfixée une variable en PHP ?

Une variable est un **emplacement mémoire qui associe un nom à une valeur**. Elle peut être de différents types : nombre entier, nombre à virgule, booléen, chaine de caractères, tableau, etc.  

En PHP, une variable est **préfixée par le symbole $**.

___

4.	Qu’est-ce que la portée d’une variable ?

La portée d'une variable détermine **où elle est accessible dans le code**. Une variable définie à l'intérieur d'une fonction n'est en général pas accessible en dehors de cette fonction. 

___

5.	Qu’est-ce qu’une constante ? Quelle est la différence avec une variable ?

Une constante est une valeur qui, une fois définie, ne sera plus jamais modifiée au cours de l'exécution d'un programme.

Les différences sont :
- la constante n'est **pas déclarée avec le symbole $**.
- la constante est souvent **écrite en majuscule**.
- la constante **ne sert pas à stocker une valeur (une information) qui peut varier** pendant l'exécution du programme.

___

6.	Qu’est-ce qu’une superglobale, combien en existe-t-il ? Donner un exemple d’utilisation.

Une superglobale est **une variable (variable prédéfinie) qui est toujours accessible, peu importe le contexte dans lequel elle est utilisée**. Contrairement aux variables normales, qui ont une portée limitée, les superglobales sont **accessibles de n'importe où dans le script**.

Il existe plusieurs superglobales en PHP :
1. $GLOBALS : Contient toutes les variables globales.
2. $_SERVER : Contient des informations sur les en-têtes, chemins, et emplacements des scripts.
3. $_REQUEST : Contient les données envoyées via les méthodes GET et POST.
4. $_POST : Contient les données envoyées via la méthode POST.
5. $_GET : Contient les données envoyées via la méthode GET.
6. $_FILES : Contient des informations sur les fichiers téléchargés via le script.
7. $_COOKIE : Contient les cookies envoyés par le client.
8. $_SESSION : Contient les variables de session.

Une superglobale en PHP peut être vue comme un tableau associatif.

Exemple d'utilisation de la superglobale $_POST, à étudier pour une meilleure compréhension :

#### Un formulaire HTML :
```
<!DOCTYPE html>
<html lang="fr">
<head>
    <meta charset="UTF-8">
    <title>Formulaire de contact</title>
</head>
<body>
    <form action="traitement.php" method="post">
        <label for="nom">Nom :</label>
        <input type="text" id="nom" name="nom" required>
        
        <label for="email">Email :</label>
        <input type="email" id="email" name="email" required>
        
        <input type="submit" value="Envoyer">
    </form>
</body>
</html>
```

#### Le fichier de traitement 'traitement.php'
```
<?php
if ($_SERVER["REQUEST_METHOD"] == "POST") {
    // Récupérer les données du formulaire
    $nom = htmlspecialchars($_POST['nom']);
    $email = htmlspecialchars($_POST['email']);
    
    // Afficher les données
    echo "Nom : " . $nom . "<br>";
    echo "Email : " . $email;
}
?>
```

#### Explications :

**Formulaire HTML :**

- Le formulaire envoie les données à traitement.php en utilisant la méthode POST.

**Traitement en PHP :**

- Dans traitement.php, nous vérifions si la requête est de type POST.
- Nous utilisons $_POST pour accéder aux valeurs des champs nom et email.
- htmlspecialchars() est utilisé pour échapper les caractères spéciaux afin d'éviter les attaques XSS.

**Affichage :**

- Les données du formulaire sont ensuite affichées à l'écran.

**En images pour bien comprendre :**

![Exemple de formulaire et de fichier de traitement](images/05_code_pour_exemple.jpg)

![Les explications de l'exemple précédent](images/06_explication_code_pour_exemple.jpg)

**Dans les détails :**

![Les détails du formulaire HTML](images/01_details_du_formulaire.jpg)

![Le traitement dans traitement.php](images/02_traitement_dans_traitement_php.jpg)

![La récupération des données](images/03_recuperation_des_donnees.jpg)

![Conclusion](images/04_conclusion.jpg)

___

7.	Quels sont les différents types (primitifs) que l’on peut associer à une variable en PHP ? Les citer et en donner des exemples (ne pas oublier le type d’une variable sans valeur).

Les différents types que l'on peut associer à une variable en PHP sont :
- une **chaine de caracères (string)**. Exemple : $chaine = "Bonjour"
- un **nombre entier (integer)**. Exemple : $nombre = 4
- un **nombre à virgule (float)**. Exemple : $float = 3.20
- un **booléen (boolean)**. Exemple : Exemple : $bool = true ou $bool = false
- un **tableau (array)**. Exemple : $tableau = [ "élément1" , 4 , 4.20 , "élément5", $variable ] -> un tableau peut contenir toute sorte de choses
- un **objet (object)**. Exemple : $maVoiture = new Voiture [avant de pouvoir créer une instance de la classe voiture, on a dû définir la classe voiture au préalable] :  
```
class Voiture {  
    // voici les propriétés de la classe que nous créeons :  
    public $marque;  
    public $modèle;  
    pblic $couleur;  
}  
```

-  une **variable sans valeur**. Exemple : 
    - $maVariable [la variable est déclarée mais n'a pas de valeur initiale, donc elle est non définie : sa valeur est considérée comme NULL]
    - $mavariable2 = NULL [on définit explicitement la variable comme NULL]

> commentaire : un objet peut contenir des propriétés et des méthodes.

___

8.	Existe-t-il plusieurs types de tableaux en PHP, si oui lesquels ?

Il existe trois types de tableaux, à savoir les tableaux indexés, les tableaux associatifs et les tableaux multidimensionnels.

- Les **tableaux indexés** sont des tableaux dont les éléments sont indexés par des nombres. Par défaut, les indices commencent à 0.
- Les **tableaux associatifs**  sont des tableaux dont les éléments sont indexés par des clés nommées. On peut donc accéder aux valeurs par ces clés. Attention, on ne peut pas avoir dans un même tableau deux clés identiques. Par contre, deux clés différentes peuvent avoir la même valeur.
- Les **tableaux multidimensionnels** sont des tableaux contenant d'autres tableaux, pour créer des structures de données plus complexes.

___

9.	Quelles sont les différentes structures de contrôle qu’il existe en algorithmie ? Donner un exemple pour chacune d’entre elles.

#### Il y a les structures conditionnelles qui permettent de prendre des décisions basées sur des conditions.

1. if :  
```
si (condition) alors  
    faire quelque chose  
fin si 
``` 

2. if ... else :  
```
si (condition) alors  
    faire quelque chose  
sinon  
    faire autre chose  
fin si  
```

3. switch :  
```
choix variable  
    cas valeur1 :  
        faire quelque chose  
    cas valeur2 :  
        faire autre chose   
    par défaut :  
        faire une autre chose   
fin choix  
```


#### Il y a les structures de répétition (les boucles) qui permettent de répéter un bloc de code plusieurs fois.

1. while :  
```
tant que (condition) faire  
    faire quelque chose  
fin tant que  
```

La condition est vérifiée avant chaque itération.  
Elle est généralement utilisée lorsque le nombre d'itérations n'est pas connu à l'avance et dépend d'une condition dynamique.  

2. for : 
```
pour i de 1 à 10 faire  
    faire quelque chose  
fin pour  
```

L'initialisation, la condition et l'incrément sont généralement définis dans la même ligne.  
Elle est souvent utilisée lorsque le nombre d'itérations est connu à l'avance.  

3. do ... while :  
```
faire  
    faire quelque chose  
tant que (condition) 
``` 

Le **bloc de code est exécuté au moins une fois**, car la condition est vérifiée après l'exécution du code.  
Elle est utile lorsque vous souhaitez garantir qu'une action est effectuée au moins une fois, indépendamment de la condition.  


#### Il y a les structures de saut qui permettent de modifier le flux d'exécution en sautant à d'autres parties du code.

1. break (utilisé **pour sortir d'une boucle** ou d'une structure de contrôle) : 
```
pour i de 1 à 10 faire  
    si (i = 5) alors  
        sortir  
    fin si  
fin pour  
```

2. continue (utilisé **pour sauter à l'itération suivante** d'une boucle) : 
```
pour i de 1 à 10 faire  
    si (i est pair) alors  
        continuer  
    fin si  
    faire quelque chose  
fin pour 
``` 

3. return (utilisé **pour sortir d'une fonction** et éventuellement renvoyer une valeur) :
``` 
fonction somme(a, b)  
    retourner a + b  
fin fonction   
```

___

10.	Quelle est la fonction PHP permettant de demander la longueur d’une chaîne de caractères ?

La fonction PHP permettant de demander la longueur d’une chaîne de caractères est : **strlen ()**. Cette fonction compte tous les caractères, y compris les espaces et la ponctuation.  
*ATTENTION* : si la chaine contient des caractères spéciaux, on préfèrera utiliser la fonction **mb_strlen()**.

___

11.	Qu’est-ce qu’une session ? Quelle fonction permet de démarrer une session en PHP ? Donner un exemple d’utilisation en PHP.

Une session en PHP est un mécanisme qui permet de stocker des données "utilisateur" sur le serveur afin de les conserver entre différentes requêtes HTTP. 
La **fonction session_start()** permet de démarrer une session en PHP.

Sur un site marchand, la session permet de conserver le contenu du panier d'achat jusqu'à la finalisation de la commande.

___

12.	Qu’est-ce qu’un cookie ? Donner un exemple d’utilisation en PHP.

___

13.	Quelle est la différence entre les instructions «require» et «include» en PHP ?

Ces instructions sont utilisées **pour inclure le contenu d'un fichier dans un autre fichier**. Mais elles présentent des différences en terme de comportement et d'utilisation.

Si le fichier spécifié ne peut pas être inclus, **require** génère une erreur fatale et arrête l'exécution du script : si le fichier est essentiel pour le fonctionnement du programme, l'utilisation de **require** est donc appropriée.

Si le fichier ne peut pas être inclus, **include** génère un avertissement et le script continue à s'exécuter. Cela peut être utile si le fichier est optionnel ou si vous voulez que le programme continue même en cas d'erreur.

En résumé, choisissez **require** lorsque le fichier est indispensable au fonctionnement du script et **include** lorsque le fichier est optionnel. Les variantes **require_once** et **include_once** permettent d'**éviter les inclusions multiples**, garantissant que le contenu du fichier est exécuté une seule fois.

___

14.	Comment effectuer une redirection en PHP ?

___

15.	Définir la partie « front-end » et « back-end » d’une application.

La partie **front-end** d'une application contient toute la partie visible par l'utilisateur. Elle contient donc **la partie "contenu informatif du site" et la partie "mise en forme du site"**. Les langages associés à cette partie sont le **HTML** et le **CSS**.

- **HTML pour fournir du contenu et le structurer**. (je maitrise les fondamentaux)
- **CSS pour la mise en forme et la gestion graphique du site**. (je dois améliorer ma pratique des outils flexbox)

Mon navigateur gère parfaitement l'affichage du front-end et je peux développer sans outil particulier. Le logiciel VSCode fait très bien le travail demandé.

La partie **back-end** d'une application contient toute la machinerie cachée qui permet un bon fonctionnement de mon application. Le langage associé à cette partie est le PHP (en ce qui me concerne).

- **PHP pour aller envoyer des requêtes au serveur**. (je découvre ce langage en ce moment même)

**Mon navigateur ne gère pas correctement le langage PHP**. En plus du logiciel VSCode, je vais installer Laragon, qui va me fournir les outils adaptés au besoin du développement en PHP.

___

16.	Définir le contrôle de version ? Qu’est-ce que Git ?

Le **contrôle de version** est un système qui **enregistre les modifications apportés à des fichiers au fil de l'avancement d'un projet**. 
- On sait quelle modification a été faite, qui a fait la modification et quand elle a été faite.
- On garde un historique complet des versions des fichiers, pour revenir facilement à une version ancienne si besoin.
- On peut travailler à plusieurs sur un même projet, en travaillant chacun sur sa propre copie des fichiers.
- On peut créer des branches pour travailler sur des fonctionnalités séparement puis fusionner ces branches à la branche principale.
- En cas de conflits, on a à disposition des outils pour les résoudre.

Git est un logiciel de contrôle de version très populaire, utilisé pour la gestion de code source. Utilisé avec la plateforme en ligne GitHub, il permet en plus une gesion décentralisée.

___

17.	Qu’est-ce qu’un CMS ? Citer au moins 2 exemples.

Un CMS (**Content Management System**), aussi appelé **système de gestion de contenu**, est un logiciel qui permet de créer, gérer et modifier du contenu numérique sur un site web sans compétences techniques avancées en programmation.

Deux exemples de CMS : 
- **WordPress**
- **Shopify**

___
___

## Front-end

    
18.	Définir HTML.

HTML (**HyperText Markup Language**) est un langage de balisage qui permet d'**ajouter du contenu et** de **le structurer**, pour la création d'une page web. Il permet entre autres de **créer des liens hypertextes** qui relient différentes pages web entre elles. Il s'utilise avec d'autres langages informatiques.

___

19.	Définir CSS.

CSS (**Cascading Style Sheets**) est un langage informatique utilisé **pour contrôler l'apparence visuelle d'une page web**. Il permet de bien contrôler la disposition des éléments sur une page et le design de chaque élément. C'est vraiment le langage **pour styliser et mettre en forme sa page web**. Il s'utilise avec d'autres langages informatiques.

*ATTENTION* : un fichier CSS peut être couplé à un fichier HTML via une balise `<link>` dans la section `<head>` du fichier HTML.  
- `<link rel="stylesheet" href="styles.css">` 

C'est la méthode la plus propre pour faire interagir du code CSS et du code HTML et nous l'utiliserons par la suite. Le code CSS est stocké proprement dans un fichier CSS distinct.

___

20.	Définir Javascript.

Je n'utilise pas encore ce langage informatique. C'est l'un des 3 piliers du développement web, avec HMTL et CSS. 

___

21.	Définir JSON. Dans quel contexte ce format est-il utilisé ? 

___

22.	Peut-on interpréter du Javascript côté serveur ? Si oui, comment ?

___

23.	Qu’est-ce qu’un sélecteur CSS ?

Un **sélecteur CSS** est un élément qui permet de cibler des éléments HTML spécifiques pour leur appliquer des styles. Les sélecteurs CSS sont des outils puissants qui permettent de cibler des éléments HTML pour appliquer des styles de manière précise et flexible.  
  
On notera comme différents sélecteurs :

- le **sélecteur de type** qui cible tous les éléments d'un type particulier (balise).    
```
p {  
    color: blue; /* Tous les paragraphes seront bleus */  
}  
```

- le **sélecteur de classe** qui cible tous les éléments ayant une classe spécifique, préfixée par un point `.`.  
```
.mon-style {  
    font-weight: bold; /* Tous les éléments avec la classe "mon-style" seront en gras */  
}  
```

- le **sélecteur d'identifiant** qui cible un élément unique ayant un identifiant spécifique, préfixé par un dièse `#`.   
```
#mon-id {  
    background-color: yellow; /* L'élément avec l'id "mon-id" aura un fond jaune */  
}  
```

- le **sélecteur d'attribut** qui cible les éléments en fonction de leurs attributs ou de leurs valeurs d'attribut.    
```
a[href] {  
    text-decoration: none; /* Tous les liens avec un attribut href n'auront pas de soulignement */  
}  
```

**Une illustration syntaxique avec les deux premiers cas :**

![Des exemples de sélecteurs d'attribut](images/07_selecteur_attribut.jpg)

- le **sélecteur combiné** qui combine plusieurs sélecteurs pour cibler des éléments en fonction de leur relation. Trop compliqué pour moi, je ne pense pas l'utiliser pour le moment.    

- le **sélecteur pseudo-classe** qui cible des éléments dans un état particulier. Peut être super utile pour des effets au survol de la souris par exemple.    
```
a:hover {  
    color: green; /* Le lien deviendra vert au survol */  
}  
```

- le **sélecteur pseudo-élément** qui cible des parties spécifiques d'un élément. Peut être sympa à utiliser.  
```
p::first-line {  
    font-weight: bold; /* La première ligne de tous les paragraphes sera en gras */  
}  
```

___

24.	Quelle balise HTML permet de créer un lien hypertexte ?

La balise qui permet de créer un lien hypertexte est la balise `<a></a>`.
Exemple : `<a href="https://www.example.com">Visitez notre site</a>`

#### attributs de la balise `<a>` :
- href : obligatoire, il spécifie l'URL de la page vers laquelle renvoie le lien.
- target : facultatif, il spécifie comment ouvrir le lien. `target="_blank"` ouvre le lien dans un nouvel onglet ou une nouvelle fenêtre alors que `target="_self"` ouvre le lien dans le même onglet.
- title : fournit des informations supplémentaires sur le lien. Ce texte s'affiche généralement en tant qu'info-bulle lorsque l'utilisateur survole le lien.
- download : indique que le lien doit être traité comme un téléchargement. Si cet attribut est présent, le lien déclenche le téléchargement du fichier lié au lieu de naviguer vers celui-ci.

Exemple de code pour une balise `<a>` avec un attribut download :
```
<a href="https://www.example.com" 
   target="_blank" 
   title="Visitez notre site" 
   rel="noopener" (notion liée à la sécurité)
   download>
   Télécharger notre brochure
</a>
```

___

25.	Qu’est-ce qu’une requête AJAX ? (je ne maitrise pas cet outil)

Une requête AJAX (**Asynchronous JavaScript and XML**) est une technique qui permet de communiquer avec un serveur sans recharger la page web. Cela permet d'**échanger des données en arrière-plan** et de mettre à jour des parties de la page sans interrompre l'expérience utilisateur.

#### Caractéristiques principales
1. **Asynchrone** : les requêtes AJAX se font de manière asynchrone, ce qui signifie que l'utilisateur peut continuer à interagir avec la page pendant que la requête est en cours.

2. **Formats de données** : bien que le nom fasse référence à XML, AJAX peut également utiliser d'autres formats de données comme JSON, HTML ou texte brut.

3. **Utilisation de JavaScript** : AJAX s'appuie sur JavaScript, souvent en utilisant l'objet ``XMLHttpRequest` ou la méthode `fetch()` pour effectuer des requêtes.

#### Exemples simples

![Un exemple de code de requête AJAX](images/08_ajax.jpg)

#### Avantages
- **Expérience utilisateur améliorée** : les pages se chargent plus rapidement et de manière plus fluide.

- **Réduction de la bande passante** : seules les données nécessaires sont échangées, pas la page entière.

#### Utilisations courantes
- Chargement de contenu dynamique (comme les commentaires ou les articles).

- Envoi de formulaires sans recharger la page.

- Mise à jour de sections spécifiques d'une page (comme les notifications).

___

26.	Quel sélecteur CSS permet de sélectionner tous les éléments d’une classe spécifique ? D’un identifiant spécifique ? (déjà répondu à la question 23)

Le premier s'appelle le **sélecteur de classe** qui cible tous les éléments ayant une classe spécifique, **préfixée par un point (.)**.
```
.mon-style {
    font-weight: bold; /* Tous les éléments avec la classe "mon-style" seront en gras */
}
```

Le deuxième s'appelle le **sélecteur d'identifiant** qui cible un élément unique ayant un identifiant spécifique, **préfixé par un dièse (#)**.
```
#mon-id {
    background-color: yellow; /* L'élément avec l'id "mon-id" aura un fond jaune */
}
```

___

27.	Définir le responsive design

Le **responsive design** est une approche de conception web qui vise à créer des sites et des applications capables de s'adapter à une variété de tailles d'écran.

___

28.	Qu’est-ce que le templating ?

**Le templating est une technique** utilisée dans le développement web pour générer du contenu HTML dynamique à partir de **modèles** (ou **templates** en anglais). Ces modèles contiennent généralement des espaces réservés (**placeholders** en anglais) qui sont remplacés par des données réelles au moment de l'exécution. Cela permet de séparer la logique de l'application de la présentation, rendant le code plus organisé et maintenable. Le templating est essentiel pour créer des applications web dynamiques et modernes.

#### Caractéristiques principales :

1. **Séparation des préoccupations** : le templating aide à séparer **le code logique** (JavaScript, PHP, etc.) de **la présentation** (HTML, CSS). Cela rend le code plus lisible et plus facile à maintenir.

2. **Réutilisabilité** : les templates peuvent être réutilisés pour générer plusieurs pages ou sections de pages, ce qui évite la duplication de code.

3. **Données dynamiques** : les modèles peuvent être remplis avec des données provenant de bases de données, d'API, ou d'autres sources, permettant ainsi de créer du contenu personnalisé.

#### Comment ça fonctionne :

1. **Création d'un modèle** : un fichier template est créé avec des balises spécifiques pour les variables. Par exemple, en utilisant une syntaxe comme {{ variable }} pour indiquer où une donnée doit être insérée. Commentaire : la plateforme de Nalan utilisait cette technique.

2. **Rendu** : lorsqu'une page est demandée, le serveur (ou le client, selon l'architecture) remplace les espaces réservés par les valeurs réelles et génère le HTML final.

#### Exemple simple :

![Un exemple de syntaxe de templating](images/09_template_exemple.jpg)

#### Outils et frameworks :

Il existe de nombreux outils et frameworks qui facilitent le templating, tels que :

- JavaScript : Handlebars, EJS, Mustache
- Python : Jinja2, Django Templates
- PHP : Twig, Blade
- Ruby : ERB, Haml

On notera **un lien entre les notions de templating et de frameworks**. Voici les remarques de chatGPT sur la question : 

Un framework est un ensemble d'outils, de bibliothèques et de conventions qui facilitent le développement d'applications en fournissant une structure de base. Il permet aux développeurs de gagner du temps et de respecter des bonnes pratiques en intégrant des fonctionnalités réutilisables et des abstractions.

En résumé, un framework est un outil puissant qui aide à structurer et à accélérer le développement d'applications en fournissant des ressources et des conventions bien définies.

**Le templating est souvent une composante essentielle des frameworks**, permettant de générer des interfaces utilisateur dynamiques et de maintenir une bonne organisation du code. **Les deux concepts se renforcent mutuellement**, rendant le développement d'applications plus fluide et structuré.
___

29.	Qu’est-ce qu’une fonction anonyme en Javascript ?

___

30.	Quelle méthode JavaScript est utilisée pour ajouter un élément à la fin d'un tableau ?

La méthode JavaScript utilisée pour ajouter un élément à la fin d'un tableau est **push()**.

Exemple 1 :
```
let fruits = ['pomme', 'banane'];
fruits.push('orange'); // Ajoute 'orange' à la fin du tableau

console.log(fruits); // Affiche : ['pomme', 'banane', 'orange']
```
Exemple 2 :
```
fruits.push('kiwi', 'fraise'); // Ajoute 'kiwi' et 'fraise' à la fin du tableau

console.log(fruits); // Affiche : ['pomme', 'banane', 'orange', 'kiwi', 'fraise']
```

#### Détails :

- La méthode **push()** modifie le tableau original et retourne la nouvelle longueur du tableau après l'ajout.

- Elle peut également accepter plusieurs arguments pour ajouter plusieurs éléments en une seule fois (voir l'exemple 2).

___

31.	Qu’est-ce qu’un « media query » ?

Une instruction pour appliquer des styles différents en fonction des caractéristiques du dispositif, telles que la largeur de l'écran, la résolution, ou l'orientation (portrait ou paysage).
```
@media (max-width: 600px) {
    body {
        background-color: lightblue; /* Applique un fond bleu clair sur les petits écrans */
    }
}
```

___

32.	Qu’est-ce qu’un pseudo-élément en CSS ?

En langage CSS, **un pseudo-élément est un mot-clé** (before, after, first-line, first-letter, etc) qui permet de sélectionner et de styliser une partie spécifique d'un élément HTML. Il ne cible pas des éléments entiers comme les sélecteurs classiques le font mais il applique des styles à des sous-éléments virtuels sans avoir à ajouter des éléments HTML supplémentaires. Les **pseudo-éléments sont préfixés par deux deux-points (::)**, ce qui les distingue des pseudo-classes (comme :hover ou :focus, qui utilisent un seul deux-points). En conclusion, les pseudo-éléments sont un outil puissant en CSS pour styliser des parties spécifiques d'un élément sans modifier le HTML.

Exemple 01 : ::before, qui insère du contenu avant le contenu d'un élément sélectionné.
```
p::before {
    content: "Note : "; /* Ajoute "Note : " avant chaque paragraphe */
    font-weight: bold;
}
```

Exemple 02 : ::after, qui insère du contenu après le contenu d'un élément sélectionné.
```
p::after {
    content: " (fin)"; /* Ajoute " (fin)" après chaque paragraphe */
    font-style: italic;
}
```

Exemple 03 : ::first-line, qui cible la première ligne de texte d'un élément.
```
p::first-line {
    font-weight: bold; /* La première ligne de tous les paragraphes sera en gras */
}
```

Exemple 04 : ::first-letter, qui cible la première lettre d'un élément.
```
p::first-letter {
    font-size: 2em; /* Agrandit la première lettre de chaque paragraphe */
    float: left; /* Permet de créer un effet de lettrine */
}
```

___

33.	Qu’est-ce que Bootstrap ? Donner d’autres exemples équivalents.

Bootstrap est **un framework front-end open-source** conçu pour faciliter le développement d'interfaces web réactives et attrayantes. Il fournit une collection de composants CSS et JavaScript préconstruits, permettant aux développeurs de créer rapidement des sites web modernes et adaptatifs.


#### Utilisation :

Pour commencer à utiliser Bootstrap, il suffit d'inclure les fichiers CSS et JavaScript dans ton projet. Tu peux soit télécharger les fichiers depuis le site officiel, soit utiliser un CDN (**Content Delivery Network** = un réseau de serveurs répartis géographiquement qui stockent et distribuent du contenu web.).

#### Exemple d'inclusion via un CDN : (dans notre fichier .html)

```
<link rel="stylesheet" href="https://stackpath.bootstrapcdn.com/bootstrap/4.5.2/css/bootstrap.min.css">
<script src="https://code.jquery.com/jquery-3.5.1.slim.min.js"></script>
<script src="https://cdn.jsdelivr.net/npm/@popperjs/core@2.0.7/dist/umd/popper.min.js"></script>
<script src="https://stackpath.bootstrapcdn.com/bootstrap/4.5.2/js/bootstrap.min.js"></script>
```

___

34.	Quand un formulaire HTML est créé, quelles sont les 2 méthodes qui peuvent lui être associées ? Donner la différence entre ces 2 méthodes.

Lorsqu'un formulaire HTML est créé, les deux méthodes qui peuvent lui être associées sont GET et POST. Voici une explication des deux méthodes et leurs différences.

#### Méthode GET

- Description : **la méthode GET envoie les données du formulaire en les ajoutant à l'URL sous forme de paramètres de requête. Les données sont visibles dans la barre d'adresse du navigateur.**

- Caractéristiques :
    - Limité en taille (environ 2000 caractères selon le navigateur).
    - Les données sont exposées dans l'URL, ce qui peut poser des problèmes de sécurité pour des informations sensibles.
    - Idéal pour des requêtes non sensibles, comme des recherches ou des filtrages, où les données peuvent être mises en cache et partagées.

- Exemple :
```
<form action="/search" method="GET">
    <input type="text" name="query">
    <button type="submit">Rechercher</button>
</form>
```

#### Méthode POST

- Description : **La méthode POST envoie les données du formulaire dans le corps de la requête HTTP, ce qui les rend invisibles dans l'URL.**

- Caractéristiques :
    - Pas de limite de taille stricte, permettant d'envoyer des volumes de données plus importants.
    - Les données ne sont pas visibles dans l'URL, offrant une meilleure sécurité pour les informations sensibles (comme les mots de passe).
    - Idéal pour soumettre des données sensibles, télécharger des fichiers ou effectuer des opérations qui modifient les données sur le serveur.

- Exemple :

```
<form action="/submit" method="POST">
    <input type="text" name="username">
    <input type="password" name="password">
    <button type="submit">Se connecter</button>
</form>
```

#### Différences clés :

| Caractéristique          | GET                        | POST                        |
|-------------------------|---------------------------|-----------------------------|
| Visibilité des données   | Dans l'URL                | Dans le corps de la requête |
| Limite de taille         | Environ 2000 caractères    | Pas de limite stricte        |
| Sécurité des données     | Moins sécurisée           | Plus sécurisée              |
| Utilisation typique      | Requêtes non sensibles     | Soumissions de données sensibles |

___
___

## UX UI


35.	Quelle est la différence entre UX Design et UI Design ?

UX Design (User Experience Design) et UI Design (User Interface Design) sont deux concepts distincts mais complémentaires dans le processus de création d'interfaces numériques.

 L'UX Design se concentre sur l'expérience globale de l'utilisateur lors de l'interaction avec un produit ou un service. Cela inclut la recherche, la définition des besoins des utilisateurs, et la création de parcours utilisateur efficaces. L'objectif principal est de rendre l'interaction aussi fluide, intuitive et agréable que possible. L'UX Designer s'efforce de résoudre des problèmes pour les utilisateurs et d'optimiser la satisfaction. **Se concentre sur l'expérience utilisateur globale et l'interaction, en s'assurant que le produit répond aux besoins des utilisateurs.**

 L'UI Design se concentre sur l'aspect visuel et l'interaction d'une interface utilisateur. Cela inclut la conception de tous les éléments visuels, tels que les boutons, les icônes, les typographies, les couleurs, et la mise en page. L'objectif principal est de créer une interface esthétique et cohérente qui facilite l'interaction et améliore l'attrait visuel du produit. **Se concentre sur l'aspect visuel et l'esthétique de l'interface, en créant une présentation attrayante et cohérente.**

___

36.	Qu’est-ce qu’un wireframe ?

Un **wireframe** est une **représentation visuelle simplifiée** d'une interface utilisateur, généralement utilisée dans les phases de conception d'un produit numérique (site web, application, etc.). Il sert de plan ou de maquette qui montre la structure, la disposition et les fonctionnalités de l'interface **sans se soucier des détails esthétiques**.

#### Caractéristiques principales d'un wireframe :

1. **Simplicité** : les wireframes sont **souvent en noir et blanc** et se concentrent sur la disposition des éléments, tels que les boutons, les images, les menus et le contenu, sans inclure de couleurs ou de graphiques complexes.

2. **Fonctionnalités** : ils mettent en avant la **hiérarchie de l'information** et les **interactions possibles**, aidant à clarifier comment les utilisateurs interagiront avec le produit.

3. **Communication** : les wireframes facilitent la **communication entre les membres de l'équipe de projet** (designers, développeurs, clients) en fournissant un aperçu clair de l'interface sans distractions visuelles.

4. **Itératif** : les wireframes peuvent être **facilement modifiés et améliorés** en fonction des **retours d'expérience**, ce qui permet de tester et d'affiner les idées avant de passer à des étapes de conception plus détaillées. (itératif -> processus qui se déroule en plusieurs étapes ou cycles, où chaque itération permet d'apporter des améliorations et des ajustements.)

___

37.	Qu’est-ce qu’un prototype ? 


Un **prototype** est une **version préliminaire** d'un produit ou d'un système, utilisée pour tester et valider des concepts, des fonctionnalités et des designs avant la production finale. Dans le domaine du design, notamment en UX/UI, **un prototype permet de simuler l'interaction avec une interface** sans avoir à construire le produit complet.

#### Caractéristiques principales d'un prototype :

1. **Interactivité** : les prototypes interactifs permettent aux utilisateurs de tester les fonctionnalités et d'interagir avec l'interface, ce qui aide à évaluer l'expérience utilisateur.

2. **Validation** : ils sont utilisés pour recueillir des retours d'expérience de la part des utilisateurs, des parties prenantes et des équipes, afin d'identifier les problèmes et d'apporter des améliorations.

3. **Itératif** : le processus de prototypage est généralement itératif, ce qui signifie que les prototypes sont affinés et modifiés en fonction des retours jusqu'à ce que le produit réponde aux attentes.

#### Types de prototypes :

1. Prototypes papier : utilisent des dessins sur papier pour représenter des interfaces et des flux utilisateur.

2. Prototypes numériques : créés à l'aide d'outils comme **Figma**, Adobe XD, ou InVision, permettant une simulation plus réaliste des interactions.

3. Prototypes fonctionnels : impliquent une certaine forme de code et de développement, permettant de tester des fonctionnalités spécifiques dans un **environnement plus proche du produit final**.

___

38.	Qu’est-ce que la hiérarchie visuelle en UI Design ?

La hiérarchie visuelle en UI Design est un principe qui organise les éléments d'une interface de manière à guider l'utilisateur à travers le contenu et à mettre en avant les informations les plus importantes. Elle utilise des techniques visuelles pour créer un ordre de priorité et aider à la compréhension et à la navigation.

#### Éléments de la hiérarchie visuelle :

- **Taille et échelle** : les éléments plus grands attirent plus l'attention. Par exemple, un titre principal sera généralement plus grand qu'un sous-titre.

- **Couleur** : l'utilisation de couleurs contrastées peut faire ressortir certains éléments. Les couleurs vives attirent l'œil, tandis que des couleurs plus neutres peuvent être utilisées pour des éléments moins importants.

- **Poids typographique** : les polices de caractères en gras ou différentes tailles peuvent indiquer l'importance. Un texte en gras ou en italique peut attirer l'attention.

- **Espacement et alignement** : un bon espacement entre les éléments crée une structure claire. Les éléments alignés de manière cohérente facilitent la lecture et la compréhension.

- **Position** : les éléments placés en haut ou au centre d'une page sont souvent perçus comme plus importants. La position sur la page peut influencer la manière dont l'information est interprétée.

- **Contraste** : le contraste entre les éléments (couleur, forme, texture) aide à faire ressortir des informations clés.


#### Importance de la hiérarchie visuelle

- **Guidage de l'utilisateur** : elle aide les utilisateurs à naviguer dans l'interface et à comprendre quelles actions sont prioritaires.

- **Amélioration de l'expérience utilisateur** : une hiérarchie claire rend l'interface plus intuitive et agréable à utiliser.

- **Facilitation de la compréhension** : elle permet aux utilisateurs de traiter rapidement l'information, en leur montrant ce qui est le plus pertinent.


En résumé, la hiérarchie visuelle est un outil essentiel en UI Design pour orienter l'attention des utilisateurs, simplifier la navigation et améliorer l'expérience globale.

___

39.	Qu’est-ce que l’accessibilité en UX Design ? 

L'accessibilité en UX Design fait référence à la conception d'interfaces et d'expériences utilisateur qui peuvent être utilisées par tous, y compris les personnes ayant des handicaps ou des limitations. Cela inclut des considérations pour les personnes ayant des problèmes de vision, d'audition, de motricité ou de cognition.


#### Principes de l'accessibilité :

- **Perceptibilité** : l'information et les éléments de l'interface doivent être présentés de manière à ce qu'ils puissent être perçus par tous les utilisateurs. Cela inclut des textes lisibles, des contrastes suffisants, et des alternatives textuelles pour les images.

- **Utilisabilité** : l'interface doit être utilisable, c'est-à-dire que tous les utilisateurs doivent pouvoir interagir avec elle facilement. Cela peut impliquer des tailles de boutons appropriées, des zones cliquables assez grandes, et des éléments facilement navigables.

- **Compréhensibilité** : le contenu doit être facile à comprendre. Cela inclut une terminologie simple, des instructions claires et une structure logique de l'information.

- **Robustesse** : l'interface doit être compatible avec divers appareils et technologies d'assistance, tels que les lecteurs d'écran. Cela signifie que le code HTML doit être sémantique et bien structuré.

#### Importance de l'accessibilité :

- **Inclusion** : l'accessibilité garantit que tout le monde, quel que soit son handicap, peut accéder à l'information et aux services en ligne.
    
- **Conformité** : de nombreuses législations, comme la loi ADA (Americans with Disabilities Act) aux États-Unis ou les normes WCAG (Web Content Accessibility Guidelines), exigent que les sites web soient accessibles.
    
- **Amélioration de l'expérience utilisateur** : une conception accessible bénéficie à tous les utilisateurs, car elle améliore la clarté et la facilité d'utilisation de l'interface.
    
- **Élargissement de l'audience** : en rendant un produit accessible, tu peux toucher un public plus large, y compris des personnes ayant des besoins spécifiques.


#### Exemples de bonnes pratiques en accessibilité :

- Utiliser un contraste élevé entre le texte et l'arrière-plan.
    
- Fournir des descriptions alternatives pour les images.
    
- Assurer que tous les éléments interactifs sont accessibles au clavier.
    
- Utiliser des titres et des balises pour structurer le contenu de manière logique.

En résumé, l'accessibilité en UX Design est **essentielle pour créer des expériences inclusives et conviviales** qui répondent aux besoins de tous les utilisateurs.

___

40.	Qu’est-ce qu’une grille de mise en page ?

Une grille de mise en page (ou **grid layout** en anglais) est un système de lignes et de colonnes utilisé en design graphique et en design d'interface pour organiser et structurer le contenu de manière cohérente et esthétique. Elle aide à aligner les éléments visuels et à créer une hiérarchie visuelle, facilitant ainsi la lecture et la navigation.

#### Caractéristiques d'une grille de mise en page :

- **Colonnes et rangées** : Une grille est généralement composée de colonnes (verticales) et de rangées (horizontales) qui forment des cellules où les éléments peuvent être placés.

- **Espacement** : les grilles définissent souvent des marges et des gouttières (l'espace entre les colonnes) pour assurer un espacement cohérent entre les éléments.

- **Flexibilité** : les grilles peuvent être rigides (avec des dimensions fixes) ou fluides (s'adaptant à différentes tailles d'écran), ce qui les rend utiles pour le **responsive design**.

- **Alignement** : elles aident à aligner les éléments de manière cohérente, ce qui contribue à une **apparence soignée et ordonnée**.

#### Avantages d'une grille de mise en page :

- **Cohérence** : en utilisant une grille, tu peux **maintenir une structure cohérente** à travers différentes pages ou sections d'un site.

- **Hiérarchie visuelle** : les grilles aident à établir une hiérarchie, rendant le contenu plus facile à lire et à comprendre.

- **Facilité de mise en œuvre** : elles simplifient le processus de conception, car les designers peuvent se concentrer sur le contenu sans se soucier constamment de l'alignement.

#### Types de grilles :

- **Grille à colonnes fixes** : les colonnes ont des largeurs définies, souvent utilisées pour des designs plus traditionnels.

- **Grille fluide** : les colonnes s'ajustent en fonction de la taille de l'écran, couramment utilisée dans le **design web moderne**.

- **Grille asymétrique** : les éléments peuvent avoir des largeurs variées, offrant plus de flexibilité pour des compositions créatives.

- **Grille modulaire** : elle utilise à la fois des colonnes et des rangées, permettant de créer des modules ou des sections répétitives.

#### Conclusion

En résumé, une grille de mise en page est un outil essentiel en design qui **aide à organiser le contenu de manière claire et esthétique**, facilitant ainsi la navigation et l'expérience utilisateur. Elle est particulièrement **importante dans le design d'interface, où la lisibilité et l'accessibilité sont primordiales**.

___

41.	Qu’est-ce que la notion d’affordance en UX Design ?

#### définitions 

Faculté d'un objet ou d'un environnement à suggérer spontanément sa propre utilisation.

L’affordance est la capacité d’un objet ou d’un système à évoquer son utilisation, sa fonction.
Par définition, l’affordance provoque une interaction spontanée entre un environnement et son utilisateur. En ergonomie, elle permet de rendre l’utilisation d’un objet ou d’un service « intuitive ». Pour améliorer l’interface utilisateur (UI) et l’expérience utilisateur (UX), les affordances sont donc essentielles dans le design des interfaces et des services

### définition du chat 

L'affordance en UX Design désigne la qualité d'un objet ou d'un élément d'interface qui suggère son utilisation ou son interaction. En d'autres termes, c'est la manière dont un design communique à l'utilisateur comment il doit interagir avec un élément donné.

#### Types d'affordance :

- **Affordance réelle** : cela fait référence aux propriétés physiques d'un objet qui permettent une interaction. Par exemple, une poignée de porte offre une prise pour être tirée ou poussée.

- **Affordance perçue** : c'est la manière dont un utilisateur perçoit comment interagir avec un objet ou un élément d'interface, même si cela n'est pas évident. Par exemple, un bouton avec une ombre ou un effet de survol indique à l'utilisateur qu'il peut cliquer dessus.

#### Importance de l'affordance en UX Design :

- **Facilite l'utilisation** : une bonne affordance **rend l'interface intuitive**, permettant aux utilisateurs de comprendre rapidement comment interagir avec les éléments sans avoir besoin d'instructions.

- **Réduit la courbe d'apprentissage** : les utilisateurs peuvent naviguer et utiliser une interface de manière plus fluide, car ils savent instinctivement comment interagir avec les éléments.

- **Améliore l'expérience utilisateur** : en créant des éléments qui sont faciles à comprendre et à utiliser, l'affordance **contribue à une expérience utilisateur positive et satisfaisante**.

#### Exemples d'affordance :

- **Boutons** : un bouton qui semble en relief (avec des ombres et des bordures) indique qu'il peut être cliqué.
- **Liens** : le texte souligné et en couleur est souvent perçu comme un lien cliquable.
- **Glissières** : les barres de défilement ou les curseurs qui semblent pouvoir être tirés indiquent une interactivité.

#### Conclusion

En résumé, l'affordance en UX Design est essentielle pour créer des interfaces intuitives et faciles à utiliser. Elle permet aux utilisateurs de comprendre rapidement comment interagir avec les éléments d'une interface, améliorant ainsi l'efficacité et la satisfaction générale.

___

42.	Qu’est-ce qu’un « mobile first design » ?

Le **mobile first design** est une approche de conception web qui consiste à créer des sites et des applications **en partant d'abord de la version mobile**, avant de s'adapter aux écrans plus grands, comme ceux des tablettes et des ordinateurs de bureau. Cette méthode est devenue populaire avec l'augmentation de l'utilisation des appareils mobiles pour naviguer sur Internet.

#### Principes du mobile first design :

1. **Priorité au contenu essentiel** : En concevant d'abord pour les petits écrans, les designers sont forcés de se concentrer sur les fonctionnalités et le contenu les plus importants, éliminant le superflu.

2. **Responsive design** : Après avoir conçu la version mobile, on adapte progressivement le design pour les écrans plus grands, en ajoutant des éléments et des fonctionnalités supplémentaires au fur et à mesure.

3. **Performance optimisée** : Les sites conçus en mobile first sont généralement plus légers et plus rapides, car ils doivent fonctionner efficacement sur des appareils avec des ressources limitées.

4. **Expérience utilisateur améliorée** : En se concentrant d'abord sur les besoins des utilisateurs mobiles, cette approche garantit une expérience fluide et intuitive, quel que soit l'appareil utilisé.

#### Avantages du mobile first design :

- **Adaptation à la réalité actuelle** : Avec une part croissante du trafic web provenant des appareils mobiles, cette approche répond aux besoins des utilisateurs modernes.

- **Meilleure accessibilité** : Les utilisateurs mobiles peuvent accéder au contenu plus facilement et rapidement, ce qui peut améliorer l'engagement.

- **Optimisation pour le SEO** : Les moteurs de recherche favorisent souvent les sites conçus en mobile first, ce qui peut améliorer leur classement dans les résultats de recherche.

#### Conclusion

En résumé, le mobile first design est une approche stratégique qui met l'accent sur la création d'expériences utilisateur optimales pour les appareils mobiles avant de s'étendre à des écrans plus grands. Cela permet de répondre aux besoins des utilisateurs modernes et d'assurer une interface efficace et conviviale.

___
___

## Programmation orientée objet (POO)

43.	Donner une définition de la programmation orientée objet.   

La programmation orientée objet (POO) est un paradigme de programmation qui organise le code autour d'objets, qui sont des instances de classes. Ces objets regroupent des données (attributs) et des comportements (méthodes) associés. La POO repose sur quatre concepts principaux :

1. **Encapsulation** : regrouper les données et les méthodes qui manipulent ces données, tout en cachant les détails internes de l'objet.

2. **Héritage** : permettre à une classe de dériver d'une autre classe, réutilisant ainsi le code existant et ajoutant ou modifiant des fonctionnalités.

3. **Polymorphisme** : permettre à des objets de différentes classes d'être traités comme des objets de la même classe, facilitant ainsi la flexibilité et l'extensibilité du code.

4. **Abstraction** : fournir une interface simplifiée tout en cachant la complexité sous-jacente, permettant aux utilisateurs de se concentrer sur les interactions essentielles.

La POO favorise la modularité, la réutilisation du code et facilite la maintenance des applications.

#### UTILE : une présentation des paradigmes les plus courants !

Un **paradigme de programmation** est un style ou une approche fondamentale pour structurer et écrire du code. Il définit **la manière dont les problèmes sont résolus et comment les concepts de programmation sont organisés**.

Les paradigmes de programmation influencent la façon dont les développeurs pensent et conçoivent leurs programmes. Voici quelques exemples courants :

1. **Programmation impérative** : se concentre sur des instructions séquentielles qui modifient l'état du programme. C'est la façon traditionnelle de programmer, en utilisant des structures comme les boucles et les conditions.

2. **Programmation orientée objet (POO)** : comme expliqué précédemment, elle organise le code autour d'objets, ce qui permet de modéliser des concepts du monde réel et de favoriser la réutilisation du code.

3. **Programmation fonctionnelle** : met l'accent sur l'utilisation de fonctions comme des "citoyens de première classe" et évite les effets de bord. Elle favorise des approches déclaratives où le "quoi" est plus important que le "comment".

4. **Programmation déclarative** : se concentre sur la description de ce que le programme doit accomplir, plutôt que sur les étapes spécifiques pour y parvenir. Les langages de requête comme SQL en sont un exemple.

Chaque paradigme a ses avantages et ses inconvénients, et le choix d'un paradigme dépend souvent du problème à résoudre et des préférences du développeur.

#### En ce qui nous concerne ...

En PHP, tu as la liberté d'utiliser plusieurs paradigmes de programmation, ce qui en fait un langage polyvalent. Voici comment les principaux paradigmes peuvent être appliqués :

1. Programmation impérative : Tu peux écrire du code de manière impérative en utilisant des instructions séquentielles, des boucles et des conditions. C’est le style le plus courant et accessible.

2. Programmation orientée objet (POO) : PHP prend en charge la POO depuis sa version 5, te permettant de créer des classes, des objets, d'utiliser l'héritage, l'encapsulation et le polymorphisme. Cela te permet d'organiser ton code de manière modulaire et réutilisable.

3. Programmation fonctionnelle : Bien que PHP ne soit pas un langage fonctionnel pur, il supporte certaines fonctionnalités de la programmation fonctionnelle, comme les fonctions anonymes (closures) et des fonctions de manipulation de tableaux comme array_map, array_filter, etc.

4. Programmation déclarative : PHP ne se concentre pas spécifiquement sur la programmation déclarative, mais tu peux utiliser des bibliothèques ou des frameworks qui adoptent ce style, notamment pour des requêtes SQL ou des configurations.

En résumé, **PHP permet de mélanger ces paradigmes selon les besoins du projet**, ce qui donne beaucoup de flexibilité dans la façon de coder.

___

44.	Qu’est-ce qu’une classe ? Comment la déclare-t-on ?

En programmation orientée objet (POO), une classe est un modèle ou un plan qui définit les propriétés (attributs) et les comportements (méthodes) que les objets créés à partir de cette classe auront. En d'autres termes, **une classe sert de structure pour créer des objets**.

#### Principales caractéristiques d'une classe :

1. **Attributs** : ce sont les variables qui stockent les données ou les états d'un objet. Par exemple, si tu as une classe `Voiture`, les attributs pourraient inclure `couleur`, `marque`, et `vitesse`.

2. **Méthodes** : ce sont les fonctions définies au sein de la classe qui décrivent les comportements ou les actions que les objets peuvent effectuer. Dans notre exemple de `Voiture`, une méthode pourrait être `accélérer()` ou `freiner()`.

3. **Constructeur** : c'est une **méthode spéciale** qui est appelée lors de la création d'un objet. Elle permet d'**initialiser les attributs de l'objet**.

4. **Encapsulation** : les attributs et les méthodes d'une classe peuvent être rendus privés ou protégés pour contrôler l'accès, ce qui aide à **protéger les données**.

#### Exemple en PHP :

![Exemple d'une classe en POO en PHP](images/11_poo_definition_classe.jpg)

Dans cet exemple, `Voiture` est une classe qui définit les attributs et les méthodes associés aux objets de type `Voiture`. Tu peux créer plusieurs objets à partir de cette classe, chacun ayant ses propres valeurs pour les attributs définis.

> commentaire : En PHP, `$this` est une référence à l'objet courant dans lequel le code est exécuté. Il est utilisé au sein d'une classe pour accéder aux attributs et aux méthodes de l'objet en cours. Voici quelques points clés concernant $this :

> 1. *Accès aux attributs* : lorsque tu veux accéder à un attribut d'un objet à l'intérieur d'une méthode de la même classe, tu utilises `$this->nomAttribut`. Par exemple, dans l'exemple de la classe `Voiture`, `$this->vitesse` accède à l'attribut `vitesse` de l'objet.

> 2. *Accès aux méthodes* : de même, pour appeler une méthode de l'objet courant, tu utilises `$this->nomMethode()`. Cela permet d'exécuter d'autres méthodes de l'objet à l'intérieur de la méthode actuelle.

> 3. *Identité de l'objet* : `$this` permet de distinguer entre les propriétés et méthodes de l'objet courant et les variables locales ou les paramètres de méthode. C'est particulièrement utile lorsqu'un paramètre a le même nom qu'un attribut.

![Exemple d'utilisation de $this en PHP](images/12_poo_this.jpg)

___

45.	Qu’est-ce qu’un objet ?

En programmation orientée objet (POO), un objet est une instance d'une classe. Il représente une entité concrète qui combine des données (attributs) et des comportements (méthodes) définis par la classe dont il est issu.

#### Caractéristiques d'un objet :

1. **État** : les attributs d'un objet définissent son état. Par exemple, pour un objet `Voiture`, des attributs comme `couleur`, `marque`, et `vitesse` décrivent ses caractéristiques à un moment donné.

2. **Comportement** : les méthodes de l'objet définissent ce qu'il peut faire. Par exemple, une méthode `accelerer()` permet à la voiture d'augmenter sa vitesse.

3. **Identité** : **chaque objet a une identité unique**, même s'il est créé à partir de la même classe. Cela signifie que deux objets peuvent avoir les mêmes attributs mais sont des instances distinctes.

#### Exemple en PHP : on reprend l'exemple de la classe `Voiture`.

![Exemple d'un objet en POO en PHP](images/13_poo_objet.jpg)

Dans cet exemple :

- `maVoiture` et `autreVoiture` sont des objets distincts de la classe `Voiture`.
- Chacun a ses propres valeurs pour `couleur`, `marque`, et `vitesse`, ce qui illustre l'état unique de chaque objet.
- Ils peuvent interagir avec leurs propres méthodes sans interférer l'un avec l'autre.

En résumé, **un objet est une instance concrète d'une classe**, combinant état et comportement, ce qui permet de modéliser des entités du monde réel dans le code.


> commentaire : En PHP, on utilise le double underscore __ devant construct pour indiquer qu'il s'agit d'une méthode spéciale, appelée **méthode magique**.

> - Constructeur : la méthode __construct est le constructeur de la classe. Elle est automatiquement appelée lors de la création d'une nouvelle instance de la classe (lorsque tu utilises le mot-clé new).

> - Initialisation : son rôle principal est d'initialiser les attributs de l'objet. Dans l'exemple précédent, __construct est utilisé pour définir la couleur, la marque et la vitesse de la voiture au moment de sa création.

![Exemple d'une variante](images/14_poo_objet_02.jpg)

___

46.	Définir la notion de propriété / attribut / méthode

En programmation orientée objet (POO), les notions de propriété, d'attribut et de méthode sont essentielles pour comprendre comment fonctionnent les classes et les objets. Voici une définition pour chacune de ces notions :

#### Propriété

La propriété fait généralement référence à une caractéristique d'une classe. En POO, on utilise souvent ce terme de manière interchangeable avec "attribut", mais il peut aussi désigner les propriétés d'une classe en tant que telles, souvent en relation avec les concepts de visibilité et d'encapsulation.

#### Attribut

Un attribut est une variable qui fait partie d'une classe. Il représente l'état ou les données d'un objet. Par exemple, dans une classe `Voiture`, les attributs pourraient être `couleur`, `marque`, et `vitesse`. Les attributs peuvent avoir différents niveaux de visibilité (public, privé, protégé) qui déterminent leur accessibilité.

#### Méthode

Une méthode est une fonction définie à l'intérieur d'une classe. Elle définit un comportement que l'objet peut réaliser. Les méthodes peuvent manipuler les attributs de l'objet et effectuer des actions. Par exemple, dans la classe `Voiture`, une méthode comme `accelerer()` permettrait d'augmenter la vitesse de la voiture.

#### Exemple en PHP

Voici comment ces notions se combinent dans un exemple :

```
php

class Voiture {
    // Attributs (ou propriétés)
    private $couleur; // Attribut privé
    private $marque;  // Attribut privé
    private $vitesse; // Attribut privé

    // Constructeur pour initialiser les attributs
    public function __construct($couleur, $marque) {
        $this->couleur = $couleur;
        $this->marque = $marque;
        $this->vitesse = 0; // Initialisation à 0
    }

    // Méthode pour accélérer
    public function accelerer($augmentation) {
        $this->vitesse += $augmentation; // Manipule l'attribut vitesse
    }

    // Méthode pour obtenir la vitesse actuelle
    public function getVitesse() {
        return $this->vitesse; // Retourne l'attribut vitesse
    }
}
```

#### Résumé

- **Attribut** : variable qui stocke des données ou l'état d'un objet.
- **Propriété** : terme souvent interchangeable avec "attribut", désignant une caractéristique d'une classe.
- **Méthode** : fonction définie dans une classe, qui décrit les actions ou comportements que l'objet peut réaliser.

___

47.	Qu’est-ce que la visibilité d’une propriété ou d’une méthode ? Citer les différents types de visibilité.

La visibilité d’une propriété ou d’une méthode en programmation orientée objet (POO) détermine l'accessibilité de ces éléments depuis d'autres parties du code, notamment d'autres classes ou objets. En PHP, il existe trois types de visibilité :

#### 1. Public

- **Accessibilité** : les propriétés et méthodes déclarées comme `public` peuvent être **accessibles depuis n'importe où**, que ce soit à l'intérieur de la classe, à l'extérieur, ou dans des classes dérivées.
- **Usage** : utilisé pour les éléments que l'on souhaite exposer et rendre accessibles à tous.

#### 2. Privé (private)

- **Accessibilité** : les éléments déclarés comme `private` ne sont **accessibles que depuis l'intérieur de la classe où ils sont définis**. Ils ne peuvent pas être accédés depuis d'autres classes, même celles qui héritent de cette classe.
- **Usage** : utilisé pour protéger les données sensibles ou internes de l'objet, en empêchant les modifications non contrôlées.

#### 3. Protégé (protected)

- **Accessibilité** : les éléments `protected` sont **accessibles à l'intérieur de la classe où ils sont définis et dans toutes les classes qui en héritent (les sous-classes)**. Cependant, ils ne sont pas accessibles depuis l'extérieur de ces classes.
- **Usage** : utilisé pour permettre un accès aux propriétés ou méthodes par des classes dérivées, tout en les protégeant de l'accès direct depuis l'extérieur.

#### Exemple en PHP 

Voici un exemple illustrant ces différents niveaux de visibilité :

![Les niveaux de visibilité d'un élément d'une classe](images/15_visibilite.jpg)

#### Résumé

- **Public** : accessible de partout.
- **Privé** : accessible uniquement à l'intérieur de la classe.
- **Protégé** : accessible dans la classe et ses sous-classes.

> Commentaire :
> - Si aucune visibilité n'est spécifiée, les propriétés et méthodes sont considérées comme **publiques**.
> - Il est généralement recommandé de toujours définir explicitement la visibilité pour plus de clarté et pour éviter toute confusion dans le code.

___

48.	Quelle est la méthode spécifique utilisée pour créer un nouvel objet à partir d’une classe ?



___

49.	Qu’est-ce que l’encapsulation ?

 

___

50.	Que signifie « étendre une classe » ? Quelle est le concept clé mis en œuvre ? Donner un exemple.



___

51.	Définir l’opérateur de résolution de portée.



___

52.	Définir une méthode / propriété statique.



___

53.	Définir le polymorphisme en POO.



___

54.	Définir une méthode / classe abstraite ?



___

55.	Définir le chaînage de méthodes.



___

56.	Qu’est-ce que la méthode __toString() ? Existe-t-il d’autres méthodes « magiques » ?



___

57.	Qu’est-ce qu’un « autoload » ?



___

58.	Comment appelle-t-on en français les « getters » et les « setters » ?



___

59.	Qu’est-ce que la sérialisation en PHP ? 



___
___

## Architecture 

60.	Qu’est-ce que l’architecture client / serveur ? Grâce à quel type de requête peut-on interroger le serveur. Définir l’acronyme de ce type de requête. Si on ajoute un « S » à cet acronyme, expliquer la différence.

___

61.	Donner la définition d’un design pattern. Citer au moins 3 exemples de design pattern.

___

62.	Qu’est-ce que l’architecture MVC ?

___

63.	Quel est le rôle de chaque couche du design pattern MVC : Model, View, Controller ?

___

64.	Quels sont les avantages de l’architecture MVC ?

___

65.	Existe-t-il des variantes à l’architecture MVC ?

___

66.	Qu’est-ce qu’une API ? Définir l’architecture REST.

___

## Modélisation - Base de données

67.	Qu’est-ce que la modélisation de données ? Définir la méthode Merise.

___

68.	Quelles sont les 3 étapes principales de la méthode Merise ?  
a.	Analyse, conception et réalisation  
b.	Planification, exécution et contrôle  
c.	Création, modification et suppression  

___

69.	Qu’est-ce qu’un modèle conceptuel de données (MCD) en Merise ?

___

70.	Qu’est-ce qu’un modèle logique de données (MLD) en Merise ?

___

71.	Donner la définition des mots suivants :  
a.	Entité  
b.	Relation  
c.	Cardinalité  
d.	Clé primaire / clé étrangère  

___

72.	Que devient une relation de type « Many To Many » dans le modèle logique de données ?

___

73.	Qu’est-ce qu’une base de données ?

___

74.	Définir les notions suivantes :  
a.	SQL  
b.	MySQL  
c.	SGBD (donner 2 exemples de SGBD)  

___

75.	Dans une base de données, les données sont stockées dans des ___. Celles-ci sont constituées de lignes appelées ___ et de colonnes appelées ___.

___

76.	Quelle est la différence entre une base de données relationnelle et non relationnelle ?

___

77.	Qu’est-ce qu’une jointure dans une base de données ? En existe-t-il plusieurs ? Si oui lesquelles ?

___

78.	A quoi sert une vue dans une base de données ?

___

79.	Qu’est-ce que l’intégrité référentielle dans une base de données ?

___

80.	Quelles sont les fonctions d’agrégation en SQL ?

___

81.	Qu’est-ce qu’un CRUD dans le contexte d’une base de données ?

___

82.	Quelles sont les clauses qui permettent de :  
a.	Insérer un nouvel enregistrement dans une table  
b.	Modifier un enregistrement dans une table  
c.	Supprimer un enregistrement dans une table  
d.	Supprimer la base de données  
e.	Filtrer les résultats d’une requête SQL  
f.	Trier les résultats d’une requête SELECT  
g.	Regrouper les résultats d'une requête SELECT en fonction d'une colonne spécifique  
h.	Concaténer 2 chaînes de caractères  

___

83.	Comment se connecter à une base de données en PHP ? Quelle est la classe native utilisée ?

___

## Symfony

84.	Qu’est-ce que Symfony ?

___

85.	Sur quel langage de programmation et design pattern repose Symfony ?

___

86.	Quelle est la dernière version en date de Symfony ?

___

87.	Qu’est-ce qu’un bundle ?

___

88.	Quel est le moteur de template utilisé par défaut dans Symfony ?

___

89.	Qu’est-ce qu’un ORM ? Quel est son utilité et comment s’appelle-t-il au sein de Symfony ?

___

90.	Qu’est-ce que l’injection de dépendances ? Quel est l’outil utilisé dans ce contexte et quel fichier contient l’intégralité des dépendances du projet ?

___

91.	Que permet le bundle Maker au sein de Symfony ? 

___

92.	Quel est le langage de requêtage exploité au sein d’un projet Symfony ?

___

93.	Quel est le composant qui garantit l’authentification et l’autorisation des utilisateurs ?

___

## Sécurité

94.	Qu’est-ce que l’injection SQL ? Comment s’en prémunir ?

___

95.	Qu’est-ce que la faille XSS ? Comment s’en prémunir ?

___

96.	Qu’est-ce que la faille CSRF ? Comment s’en prémunir ?

___

97.	Définir l’attaque par force brute et l’attaque par dictionnaire.

___

98. Existe-t-il d’autres failles de sécurité ? Citer celles-ci et expliquer simplement leur comportement.

___

99. A quoi servent l’authentification et l’autorisation dans un contexte d’application web ?

___

100.    Définir la notion de hachage d’un mot de passe et citer des algorithmes de hachage.

___

101.	Qu’est-ce qu’une politique de mots de passe forts ?

___

102.	Qu’est-ce que l’hameçonnage ?

___

103.	Définir la « validation des entrées ».

___

## RGPD

104.	Qu’est-ce que le RGPD ?

___

105.	Quel est son objectif principal ?

___

106.	Quelle est la date d’entrée en vigueur du RGPD ?

___

107.	Quelles sont les sanctions possibles en cas de non-respect du RGPD ?

___

108.	En France, quel est l’autorité administrative qui s’occupe de faire appliquer le RGPD ?

___

109.	Quel est le consentement valide selon le RPGD ?

___

110.	Qu’est-ce qu’une politique de confidentialité ?

___

111.	Quelle est la durée de conservation maximale des données personnelles selon le RGPD ?

___

112.	Quels sont les droits des utilisateurs selon le RGPD ?

___

113.	Qu’est-ce que le principe de minimisation des données selon le RGPD ?

___

## SEO

114.	Qu’est-ce que le SEO ? 

___

115.	Quel est l’objectif principal du SEO ?

___

116.	Existe-t-il plusieurs types de référencement ? Lesquels ?

___

117.	Qu’est-ce que la densité de mots-clés en SEO ?

___

118.	Qu’est-ce qu’une balise « alt » ?

___

119.	Qu’est-ce que la balise « meta description » ?

___

120.	Qu’est-ce que le « nofollow » en SEO ?

___

121.	Quelle est l'importance du contenu de qualité pour le référencement d'un site web ?

___

122.	Pourquoi est-il important d'utiliser des balises de titre (h1, h2, h3, etc.) de manière structurée ?

___

123.	Quelle est la recommandation pour les URL d'un site web bien référencé ?

___

124.	Qu'est-ce que le maillage interne et pourquoi est-il important pour le référencement ?

___

125.	Qu'est-ce que l'optimisation des images pour le référencement ?

___

126.	Qu'est-ce qu'un plan de site (sitemap) et pourquoi est-il important pour le référencement ?

___
___

## Gestion de projets - DevOps

___

127.	Qu’est-ce que la gestion de projet ?

La **gestion de projet** est l’ensemble des pratiques et des techniques utilisées pour planifier, exécuter et finaliser un projet dans les délais et les budgets impartis. Elle implique plusieurs étapes clés :  

1. **Initiation** : définir l’objectif du projet et ses parties prenantes.
    
2. **Planification** : élaborer un plan qui inclut les ressources, le budget, les délais et les tâches nécessaires.
    
3. **Exécution** : mettre en œuvre le plan, coordonner les équipes et gérer les ressources.
    
4. **Suivi et contrôle** : surveiller l’avancement du projet, ajuster les plans si nécessaire et gérer les risques.
    
5. **Clôture** : finaliser le projet, évaluer les résultats et documenter les leçons apprises.

La gestion de projet vise à atteindre des résultats spécifiques tout en respectant les contraintes de temps, de coût et de qualité.
___

128.	Qu’est-ce qu’une méthode Agile de gestion de projet ? 

La méthode Agile est une approche de gestion de projet qui privilégie la flexibilité, la collaboration et l'adaptabilité face aux changements. Elle est particulièrement populaire dans le développement logiciel, mais peut être appliquée à divers types de projets. Voici quelques caractéristiques clés :

1. **Itérations courtes** : les projets sont divisés en cycles appelés "sprints", généralement de deux à quatre semaines, permettant d'obtenir rapidement des résultats.

2. **Collaboration** : les équipes travaillent en étroite collaboration avec les parties prenantes, favorisant une communication ouverte et continue.

3. **Adaptabilité** : les équipes peuvent ajuster leurs priorités et leurs plans en fonction des retours d'expérience et des changements de besoins.

4. **Feedback régulier** : les retours des utilisateurs sont intégrés à chaque étape, permettant d'améliorer constamment le produit.

5. **Livraison continue** : l'objectif est de livrer des fonctionnalités opérationnelles à la fin de chaque sprint, assurant ainsi une progression constante.

Les méthodes Agile, comme Scrum et Kanban, sont conçues pour répondre rapidement aux besoins changeants des clients et pour améliorer la qualité du produit final.
___

129.	Expliquer la méthode MoSCoW en quelques lignes et citer ses avantages.

La méthode MoSCoW est une **technique de priorisation utilisée dans la gestion de projet** pour aider à classer les exigences en fonction de leur importance. MoSCoW est un acronyme qui signifie :

- **Must have** (doit avoir) : les éléments essentiels au succès du projet.
    
- **Should have** (devrait avoir) : les éléments importants mais non critiques.
    
- **Could have** (pourrait avoir) : les éléments souhaitables qui peuvent être ajoutés si le temps et les ressources le permettent.
    
- **Won't have this time** (n’aura pas cette fois) : les éléments qui ne seront pas inclus dans cette phase.

### Avantages de la méthode MoSCoW :

1. **Clarté** : aide à clarifier les priorités et à aligner les attentes des parties prenantes.
    
2. **Gestion des ressources** : permet de concentrer les efforts sur les éléments les plus critiques, optimisant ainsi l'utilisation des ressources.
    
3. **Flexibilité** : facilite les ajustements en cours de projet en permettant d’identifier rapidement ce qui peut être abandonné ou ajusté.
    
4. **Communication** : favorise une meilleure communication entre les équipes et les parties prenantes en rendant les priorités explicites.

Cette méthode est particulièrement **utile dans un contexte Agile**, où les besoins peuvent évoluer rapidement.
___

130.	A quoi sert la méthodologie MVP ? Citer les caractéristiques clés.

La méthodologie MVP, ou **Minimum Viable Product**, est une approche utilisée dans le développement de produits, notamment dans le domaine des startups et des technologies. Son objectif est de **créer un produit avec les fonctionnalités essentielles** qui répondent **aux besoins de base des utilisateurs**, afin de **tester une idée** sur le marché **le plus rapidement possible**.

### Objectifs de la méthodologie MVP :

1. **Valider une idée** : tester une hypothèse de produit avec un **minimum de ressources** avant de développer davantage.
    
2. **Réduire les risques** : **minimiser les investissements initiaux et les risques** associés à un produit qui pourrait ne pas rencontrer le succès.
    
3. **Recueillir des retours** : obtenir **rapidement des feedbacks** des utilisateurs pour améliorer le produit.

### Caractéristiques clés de la méthodologie MVP :

1. **Fonctionnalités minimales** : se concentrer sur les **fonctionnalités essentielles** qui répondent aux besoins des utilisateurs cibles.
    
2. **Lancement rapide** : développer et lancer le produit **sur le marché rapidement** pour valider les hypothèses.
    
3. **Apprentissage continu** : recueillir **des données et des retours d'expérience** pour guider les futures améliorations et évolutions du produit.
    
4. **Adaptabilité** : être prêt à itérer sur le produit en fonction des feedbacks reçus et des changements dans le marché.

L'approche MVP permet donc de **tester des idées rapidement et efficacement**, tout en restant orienté vers les besoins des utilisateurs.
___

131.	Qu’est-ce que la planification itérative ?

La planification itérative est une approche de gestion de projet qui consiste à **diviser le travail en petites étapes ou itérations**, permettant ainsi une planification, une exécution et une révision continues. Contrairement à une planification linéaire, où toutes les phases du projet sont définies dès le départ, la planification itérative permet de **s'adapter aux changements et d'ajuster les priorités** au fur et à mesure de l’avancement du projet.

### Caractéristiques de la planification itérative :

1.**Cycles courts** : les projets sont divisés en itérations (ou **sprints**) qui durent généralement de quelques jours à quelques semaines.

2.**Feedback régulier** : à la fin de chaque itération, des retours sont recueillis, permettant d'ajuster les fonctionnalités ou les priorités en fonction des besoins réels des utilisateurs.

3.**Amélioration continue** : chaque itération permet d’apprendre et d’améliorer le produit, ce qui peut conduire à des ajustements significatifs en cours de route.

4. **Flexibilité** : la planification itérative permet de **s’adapter facilement aux changements**, qu’ils proviennent des besoins des utilisateurs ou de nouvelles contraintes de marché.

### Avantages de la planification itérative :

- **Réduction des risques** : en validant régulièrement le travail effectué, on peut identifier rapidement les problèmes potentiels.

- **Meilleure qualité** : les itérations permettent d’intégrer des améliorations basées sur les retours d’expérience, ce qui augmente la qualité finale du produit.

- **Satisfaction accrue des utilisateurs** : en impliquant les utilisateurs dans le processus et en tenant compte de leurs retours, le produit final est plus susceptible de répondre à leurs attentes.

Cette méthode est particulièrement **efficace dans des environnements complexes et changeants**, comme le développement logiciel.
___

132.	Citer 3 méthodes Agiles dans le cadre d’un projet informatique.

Voici **trois méthodes Agiles** couramment utilisées dans le cadre de projets informatiques :

1. **Scrum** :
- Scrum est un cadre qui organise le travail en sprints (itérations de 1 à 4 semaines). Il implique des rôles définis (Scrum Master, Product Owner, équipe de développement) et des événements réguliers (réunions de planification, revues et rétrospectives) pour favoriser la collaboration et l'adaptabilité.

2. **Kanban** :
- Kanban est une méthode visuelle qui utilise un tableau (physique ou numérique) pour représenter le flux de travail. Les tâches sont organisées en colonnes (par exemple, "À faire", "En cours", "Terminé") et la méthode met l'accent sur la limitation du travail en cours (**WIP** - Work In Progress) pour améliorer l'efficacité et la fluidité.

3. **Extreme Programming (XP)** :
- XP est une méthode qui se concentre sur l'amélioration de la qualité du logiciel et la réactivité au changement. Elle inclut des pratiques telles que le développement piloté par les tests (**TDD** Test-Driven Development - développement piloté par les tests), la programmation en binôme, et des cycles de développement courts pour favoriser une collaboration étroite avec le client.

Chacune de ces méthodes offre des approches différentes pour gérer le développement de projets informatiques tout en restant **flexible et réactive aux besoins changeants des utilisateurs**.
___

133.	Qu’est-ce qu’une réunion de revue de projet ?

Une **réunion de revue de projet** est un rassemblement organisé à des moments clés du cycle de vie d'un projet pour évaluer son avancement, ses résultats et prendre des décisions sur les prochaines étapes. Ces réunions sont essentielles pour assurer la transparence et la communication entre les membres de l'équipe et les parties prenantes.

### Objectifs de la réunion de revue de projet :

1. **Évaluation de l'avancement** : examiner les progrès réalisés par rapport aux objectifs fixés, aux délais et aux budgets.

2. **Identification des problèmes** : discuter des obstacles rencontrés et des risques potentiels, et proposer des solutions.

3. **Recueil de retours** : obtenir des retours d'expérience des membres de l'équipe et des parties prenantes sur ce qui fonctionne bien et ce qui pourrait être amélioré.

4. **Ajustement des plans** : adapter le plan de projet si nécessaire, en tenant compte des retours et des résultats de l'évaluation.

5. **Renforcement de la collaboration** : favoriser la communication entre les équipes et les parties prenantes, en s'assurant que tout le monde est aligné sur les objectifs et les attentes.

### Fréquence et participants :

- Ces réunions peuvent avoir lieu à intervalles réguliers (par exemple, toutes les deux semaines) ou à des moments spécifiques, comme à la fin d'une phase ou d'une itération.

- Les participants incluent généralement les membres de l'équipe de projet, les chefs de projet, les parties prenantes et parfois des clients ou des utilisateurs.

En résumé, la réunion de revue de projet est un outil important pour garantir que le projet reste sur la bonne voie, pour résoudre les problèmes et pour s'assurer que toutes les parties sont alignées sur les objectifs.
___

134.	Qu’est-ce qu’un livrable dans un projet ? 

Un **livrable** dans un projet est tout produit, service ou résultat concret qui est remis à une partie prenante à la fin d'une phase ou d'une tâche du projet. Les livrables peuvent prendre différentes formes selon la nature du projet et ses objectifs.

### Caractéristiques des livrables :

1. **Mesurables et spécifiques** : les livrables doivent être clairement définis et quantifiables, permettant ainsi d'évaluer s'ils ont été atteints.

2. **Temporellement définis** : chaque livrable a une date de livraison associée, déterminant quand il doit être complété.

3. **Associés à des objectifs** : les livrables sont souvent liés à des objectifs de projet spécifiques, contribuant à l'atteinte des résultats globaux.

### Exemples de livrables :

- **Documents** : rapports, analyses, spécifications fonctionnelles, plans de projet.

- **Produits** : logiciels, applications, prototypes, sites web.

- **Services** : formations, support technique, consultations.

- **Résultats** : études de marché, études de faisabilité, résultats de tests.

En résumé, les livrables sont des éléments essentiels qui permettent de **suivre l'avancement du projet** et de **s'assurer que les attentes des parties prenantes sont satisfaites**. Ils sont souvent utilisés comme **critères d'achèvement** pour valider que le projet progresse conformément aux plans.
___

135.	Quels sont les 3 piliers SCRUM ? Définir chacun d’entre eux.

Les trois piliers de Scrum sont **la transparence, l'inspection et l'adaptation**. Chacun de ces piliers joue un rôle crucial dans le succès de la méthode Scrum et dans la gestion efficace des projets Agile.

### 1. Transparence :

- **Définition** : la transparence signifie que tous les aspects du processus de développement doivent être visibles et accessibles à toutes les parties prenantes. Cela inclut la clarté sur le travail en cours, les priorités et les problèmes rencontrés.

- **Importance** : en assurant une transparence totale, toutes les personnes impliquées peuvent comprendre le projet, ce qui favorise la collaboration et la confiance. Les éléments comme le backlog produit et le tableau Scrum (ou tableau Kanban) doivent être clairement visibles.

### 2. Inspection :

- **Définition** : l'inspection consiste à examiner régulièrement le produit et le processus de développement pour identifier les écarts par rapport aux attentes ou aux objectifs. Cela se fait lors des événements Scrum, comme les revues de sprint.

- **Importance** : des inspections fréquentes permettent de détecter rapidement les problèmes ou les dysfonctionnements, ce qui aide à maintenir la qualité du produit et à s'assurer que l'équipe reste sur la bonne voie.

### 3. Adaptation :

- **Définition** : l'adaptation fait référence à la nécessité d'ajuster le processus et le produit en réponse aux résultats des inspections. Cela peut inclure la modification des priorités, la révision des méthodes de travail ou l'ajustement des objectifs.

- **Importance** : la capacité d'adaptation est essentielle pour répondre aux changements des besoins des utilisateurs ou aux défis imprévus, garantissant que l'équipe peut évoluer et s'améliorer continuellement.

Ces trois piliers sont interconnectés et renforcent la dynamique Agile de Scrum, permettant aux équipes de rester flexibles, réactives et concentrées sur la livraison de valeur.
___

136.	Qu’est-ce que le DevOps et quel est son objectif principal ?

DevOps est une approche qui **combine le développement (*Dev*) et les opérations (*Ops*)** pour améliorer la collaboration et l'efficacité entre les équipes de développement logiciel et les équipes d'exploitation informatique. Il s'agit d'une culture, d'une philosophie et d'un ensemble de pratiques qui visent à réduire le temps entre le développement d'une fonctionnalité et sa mise en production.
Objectif principal du DevOps :

Le principal objectif de DevOps est d'accélérer le cycle de vie du développement logiciel tout en améliorant la qualité et la fiabilité des applications. Cela inclut :

1. **Collaboration améliorée** : favoriser une culture de collaboration entre les équipes de développement et d'exploitation, brisant ainsi les silos traditionnels.

2. **Automatisation** : automatiser les processus de déploiement, de tests et de gestion des infrastructures pour réduire les erreurs humaines et accélérer le temps de mise sur le marché.

3. **Feedback continu** : intégrer des mécanismes de retour d'information tout au long du cycle de vie du développement, permettant des améliorations rapides basées sur les retours des utilisateurs et des performances des systèmes.

4. **Mises à jour fréquentes** : permettre des mises à jour fréquentes et fiables des applications, ce qui permet d'intégrer rapidement de nouvelles fonctionnalités et de corriger les bogues.

En résumé, DevOps vise à améliorer la productivité des équipes, à réduire le temps de mise sur le marché et à augmenter la satisfaction des clients grâce à des livraisons de logiciels plus rapides et de meilleure qualité.
___

137.	Qu’est-ce que l’intégration continue ? 

L'intégration continue (**CI**, pour **Continuous Integration**) est une pratique de développement logiciel qui consiste à intégrer régulièrement les modifications de code dans un référentiel partagé. L'objectif est d'assurer que le code est toujours dans un état déployable, en automatisant le processus de test et d'intégration.

### Principes de l'intégration continue :

1. **Intégration fréquente** : les développeurs intègrent leurs modifications plusieurs fois par jour, plutôt qu'à la fin d'un cycle de développement. Cela réduit le risque de conflits de code.

2. **Automatisation des tests** : chaque intégration déclenche automatiquement une série de tests pour vérifier que les modifications n'ont pas introduit de bogues. Cela inclut des tests unitaires, d'intégration et parfois des tests fonctionnels.

3. **Feedback rapide** : les résultats des tests sont fournis rapidement aux développeurs, ce qui permet d'identifier et de résoudre les problèmes dès qu'ils surviennent.

4. **Déploiement simplifié** : l'intégration continue prépare le terrain pour des déploiements fréquents, en s'assurant que le code est stable et prêt à être mis en production.

### Avantages de l'intégration continue :

- **Détection précoce des erreurs** : les problèmes peuvent être identifiés rapidement, ce qui réduit le coût et le temps nécessaires pour les corriger.

- **Amélioration de la qualité du code** : en intégrant et en testant régulièrement, le code est souvent plus propre et mieux structuré.

- **Collaboration renforcée** : facilite la collaboration entre les membres de l'équipe, car chacun est informé des modifications apportées au code.

- **Réduction du temps de mise sur le marché** : permet des cycles de développement plus courts, ce qui aide à livrer des fonctionnalités plus rapidement aux utilisateurs.

En résumé, l'intégration continue est une **pratique essentielle dans le développement Agile et DevOps**, favorisant une approche proactive pour gérer le code et assurer la qualité des livrables.
___

138.	Qu’est-ce que Docker ? Et en quoi est-il utile dans le cadre du DevOps ?

**Docker** est une plateforme de virtualisation légère qui permet de créer, déployer et exécuter des applications dans des conteneurs. Un conteneur est une unité standardisée qui regroupe tout ce dont une application a besoin pour fonctionner, y compris le code, les bibliothèques, les dépendances et les configurations.

### Caractéristiques de Docker :

1. **Isolation** : les conteneurs isolent les applications les unes des autres, ce qui permet d'exécuter plusieurs applications sur la même machine sans conflit.

2. **Portabilité** : les conteneurs peuvent être exécutés sur n'importe quel environnement qui prend en charge Docker, qu'il s'agisse d'un ordinateur local, d'un serveur ou du cloud.

3. **Légèreté** : contrairement aux machines virtuelles, qui nécessitent un système d'exploitation complet, les conteneurs partagent le noyau du système d'exploitation sous-jacent, ce qui les rend plus légers et plus rapides à démarrer.

### Utilité de Docker dans le cadre du DevOps :

1. **Cohérence des environnements** : Docker garantit que les applications fonctionnent de la même manière dans tous les environnements (développement, test, production), réduisant ainsi les problèmes de "ça marche sur ma machine".

2. **Déploiement rapide** : les conteneurs peuvent être créés et déployés rapidement, facilitant les mises à jour fréquentes et les déploiements continus.

3. **Scalabilité** : Docker permet de scaler facilement les applications en déployant plusieurs instances de conteneurs, ce qui est essentiel pour répondre à la demande.

4. **Automatisation** : l'utilisation de Docker avec des outils d'orchestration comme Kubernetes permet d'automatiser le déploiement, la gestion et la mise à l'échelle des conteneurs, ce qui s'aligne avec les pratiques DevOps.

5. **Gestion des dépendances** : en encapsulant les dépendances de l'application dans le conteneur, Docker simplifie la gestion des versions et des mises à jour.

En résumé, Docker est un outil puissant qui facilite le développement, le déploiement et la gestion des applications dans un environnement DevOps, en promouvant l'agilité, la collaboration et l'efficacité.
___

139.	Qu’est-ce qu’un test unitaire ? 

Un **test unitaire** est une méthode de test logiciel qui consiste à vérifier le fonctionnement d'une petite unité de code, généralement une fonction ou une méthode, de manière isolée. L'objectif principal est de s'assurer que chaque unité fonctionne comme prévu.

### Caractéristiques des tests unitaires :

1. **Isolation** : les tests unitaires sont conçus pour tester une seule unité de code à la fois, sans dépendance externe (comme les bases de données ou les services externes). Cela permet de se concentrer sur le comportement de l'unité testée.

2. **Automatisation** : les tests unitaires sont souvent automatisés, ce qui signifie qu'ils peuvent être exécutés rapidement et de manière répétée. Cela facilite leur intégration dans le processus de développement.

3. **Rapidité** : étant donné qu'ils testent des portions de code relativement petites, les tests unitaires s'exécutent généralement très rapidement, ce qui permet aux développeurs de les exécuter fréquemment.

### Avantages des tests unitaires :

- **Détection précoce des bogues** : en vérifiant chaque unité de code individuellement, les tests unitaires aident à identifier les erreurs dès les premières étapes du développement, ce qui réduit le coût de correction.

- **Facilite la maintenance** : avec une bonne couverture de tests unitaires, les développeurs peuvent modifier le code en ayant l'assurance que les tests vérifieront que le comportement reste correct.

- **Documentation** : les tests unitaires servent de documentation vivante du code, montrant comment chaque unité est censée fonctionner.

- **Encourage le bon design** : lors de l'écriture de tests unitaires, les développeurs sont souvent amenés à réfléchir à la conception de leur code, ce qui peut conduire à une meilleure architecture.

En résumé, les tests unitaires sont une pratique essentielle dans le développement logiciel, particulièrement dans les méthodologies Agile et DevOps, car ils garantissent la qualité et la fiabilité du code tout au long du cycle de développement.
___

140.	Quelle est l'unité de code testée lors d'un test unitaire ?

Lors d'un test unitaire, l'unité de code testée est généralement une **fonction**, une **méthode** ou un **module** spécifique. Cela peut également inclure des classes ou des composants isolés dans le cadre d'un logiciel. L'idée est de **vérifier le comportement d'une petite partie du code de manière isolée, sans dépendances extérieures**.

### Objectifs des tests unitaires sur cette unité de code :

1. **Vérifier la logique** : s'assurer que la logique de l'unité fonctionne comme prévu et produit les résultats attendus pour différents cas d'entrée.

2. **Tester les erreurs** : évaluer comment l'unité gère les entrées invalides ou les situations exceptionnelles.

3. **Confirmer les effets de bord** : vérifier que les modifications apportées à l'unité n'affectent pas d'autres parties du code.

En se concentrant sur des unités de code spécifiques, les tests unitaires permettent d'identifier rapidement les problèmes et de garantir que chaque composant fonctionne correctement dans le cadre global de l'application.
___

141.	Quelles sont les caractéristiques d'un bon test unitaire ?

Un bon test unitaire doit posséder plusieurs caractéristiques clés pour être efficace et utile. Voici les principales :

### 1. Indépendant :

- Chaque test doit être isolé des autres. Les résultats d’un test ne doivent pas dépendre de l'exécution d'autres tests, ce qui facilite le débogage.

### 2. Rapide :

- Les tests unitaires doivent s'exécuter rapidement. Cela permet de les exécuter fréquemment pendant le développement sans ralentir le processus.

### 3. Précis :

- Chaque test doit vérifier un seul aspect ou une seule fonctionnalité de l'unité testée. Cela aide à identifier facilement la source d'un échec.

### 4. Clair et lisible :

- Le code du test doit être compréhensible. Un bon nom de test et des commentaires appropriés aident à comprendre l'objectif du test.

### 5. Automatisable :

- Les tests unitaires doivent être facilement automatisables pour s'intégrer dans le processus de CI/CD (intégration continue/déploiement continu).

### 6. Réplicable :

- Les tests doivent produire les mêmes résultats à chaque exécution, sous les mêmes conditions. Cela garantit la fiabilité des résultats.

### 7. Axé sur les cas limites :

- Les tests doivent inclure des scénarios normaux ainsi que des cas limites et des cas d'erreur pour garantir une couverture complète.

### 8. Facile à maintenir :

- Les tests doivent pouvoir être facilement modifiés pour suivre l'évolution du code. Une bonne structure de test facilite la mise à jour lorsque des changements surviennent.

### 9. Documenté :

- Chaque test devrait servir de documentation pour le comportement attendu de l'unité de code. Cela aide les développeurs à comprendre rapidement la fonctionnalité.

En intégrant ces caractéristiques, un bon test unitaire contribue à améliorer la qualité du code, facilite la maintenance et réduit le risque d'introduire des bogues lors des modifications.
___

142.	Qu'est-ce qu'une assertion dans un test unitaire ?

 Une **assertion** dans un test unitaire est une instruction qui vérifie si une condition spécifiée est vraie. Elle est utilisée pour valider que le comportement d'une unité de code (comme une fonction ou une méthode) est conforme aux attentes. Si l'assertion échoue, cela signifie qu'il y a un problème avec le code testé.

### Caractéristiques des assertions :

1. **Validation des résultats** : les assertions comparent la sortie réelle d'une fonction avec la sortie attendue. Par exemple, si une fonction est censée renvoyer un nombre, l'assertion vérifiera que le nombre renvoyé correspond à ce qui est prévu.

2. **Échec des tests** : si l'assertion échoue (c'est-à-dire que la condition vérifiée est fausse), le test unitaire est considéré comme échoué, signalant un problème potentiel dans le code.

3. **Simplicité** : les assertions sont généralement simples et concises, facilitant la lecture et la compréhension des tests.


### Exemple d'utilisation :

Supposons que nous ayons une fonction qui additionne deux nombres :

```
def add(a, b):
    return a + b
```

Un test unitaire avec une assertion pourrait ressembler à ceci :

```
def test_add():
    result = add(2, 3)
    assert result == 5  # Assertion vérifiant que le résultat attendu est correct
```

Dans cet exemple, l'assertion `assert result == 5` valide que la fonction `add` renvoie bien 5 lorsque les arguments 2 et 3 lui sont passés. Si la fonction ne renvoie pas 5, le test échouera, indiquant qu'il y a un problème dans l'implémentation de la fonction.

En résumé, les assertions sont des éléments fondamentaux des tests unitaires, car elles permettent de vérifier le comportement attendu du code et d'assurer sa qualité.

___

## English

1)	What does JavaScript enable you to do on a website ?  
a.	Add interactive behavior and dynamic content. <--  
b.	Define the layout and design of web pages.  
c.	Handle server-side operations.  

___

2)	Which programming language is primarily used for server-side web development ?  
a.	PHP. <--  
b.	JavaScript.  
c.	HTML.  

___

3)	What is the purpose of a web browser ?  
a.	To render and display web pages. <--  
b.	To execute serve-side code.  
c.	To manage databases.  

___

4)	What is the difference between GET and POST methods in HTTP ?  
a.	GET retrieves data from a server, while POST submits data to a server.  
b.	GET submits data to a server, while POST retrieves data from a server.  
c.	GET and POST methods are interchangeable.  

___

5)	What is the purpose of version control systems (e.g., Git) in web development ?  
a.	To track changes and manage collaborative development.  
b.	To optimize website loading speed.  
c.	To handle server-side scripting.  

___

6)	What is the purpose of a framework in web development ?  
a.	To provide a structured environment for building web applications.  
b.	To handle network protocols and data transfer.  
c.	To create visual designs and layouts for websites.  

___

7)	What does NoSQL stand for ?  
a.	Not Only SQL.  
b.	Non-Structured Query Language.  
c.	New Object-Oriented Language.  

___

8)	Which of the following is a characteristic of NoSQL databases ?  
a.	Strict schema enforcement.  
b.	Support for complex transactions.  
c.	Scalability and flexible data models.  

___
