# Sélecteurs CSS et cascade



## Les sélecteurs en CSS

Pour que la propriété d'un élément puisse être modifiée par le CSS, il faut tout d'abord pouvoir sélectionner cet élément. Pour cela, nous disposons de trois méthodes :

### Les balises

On peut sélectionner l'élément grâce à sa balise. Ex : modification du titre de niveau 1 (`<h1/>`)

Code HTML :

```html
<html>
    <head></head>
    <body>
        <h1>Mon titre</h1>
        <p>Mon paragraphe1</p>
        <p>Mon paragraphe2</p>
    </body>
</html>
```    

Code CSS :
```css
h1 {color: red;}
```
    

Ici, on donne la couleur rouge au titre de niveau 1. Le problème avec le sélecteur balise, c'est qu'il s'applique à tous les éléments de la même balise. Ainsi, si on ajoute un autre titre de niveau 1, il sera de couleur rouge. Comment faire pour ne changer que la couleur du premier titre ?


### Les ids

On peut ajouter un attribut id dans la balise h1 pour ne sélectionner que le premier titre de niveau 1.

Code HTML :
```html
<html>
    <head></head>
    <body>
        <h1 id="titre1">Mon titre1</h1>
        <p>Mon paragraphe1</p>
        <p>Mon paragraphe2</p>
        <h1 id="titre2">Mon titre2</h1>
        <p>Mon paragraphe3</p>
        <p>Mon paragraphe4</p>
    </body>
</html>
```   

Code CSS :
```css
#titre1 {color: red;}
#titre2 {color: blue;}
```    

Le problème des ids, c'est l'inverse des balises: on ne peut sélectionner qu'un élément, celui qui possède l'attribut id. Or, un id doit être unique (il ne peut y avoir deux ids identiques dans la même page). Ainsi, pour modifier le deuxième titre (qui doit avoir la couleur bleu), on utilise un deuxième id. Personnellement, je n'utilise les ids que dans des cas particuliers en CSS, je leur préfère les classes (on verra pourquoi plus loin).


### Les classes

Les classes possèdent les avantages des balises et des ids. Elles peuvent être unique, si on ne la déclare qu'une seule fois dans la page HTML. Mais, elles peuvent aussi être utilisées autant de fois que nécessaire. De plus, l'attribut class peut avoir plusieurs valeurs (plusieurs classes différentes).


## La cascade ou la hiérarchie des sélecteurs

### Dans la balise

La hiérarchie est un système de poids qui permet de déterminer la propriété affectée à l'élément :

    - Les styles dans l'attribut style de la balise : 1,0,0,0
    - Les ids : 0,1,0,0
    - les classes et pseudo-classes : 0,0,1,0
    - les éléments et pseudo-éléments : 0,0,0,1

Ce que cette liste veut dire, c'est que :

    - Ce sont les propriétés de l'attribut style qui l'emportent sur toutes autres propriétés (celles de ids, des classes, des éléments)
    - Pour un élément qui a un attribut id et un attribut classe, ce sont les propriétés de l'id qui l'emportent sur celles de la classe.
    - Ce sont les propriétés de la classe qui l'emportent sur celles de l'élément.
    - Dans le cas de deux fois le même sélecteur et la même propriété, le poids dépend de sa position dans le fichier CSS; les dernières déclarations ont le poids le plus élevé.

    ```css
    .main p {color: blue;}
    .main p {color: red;}
    ```
    Les paragraphes contenus dans la classe main seront de couleur rouge.

Il est possible de contrecarrer cette hiérarchie par l'utilisation du mot clé `!important` à la fin de la valeur de la propriété.

### Les ids

Article content.... lorem ipsum si imet delor
Les classes

Article content.... lorem ipsum si imet delor


## L'héritage des propriétés chez les balises

Toute balise a un parent et zéro à plusieurs enfants. Une balise peut hériter les propriétés de sa balise parent qui la tient peut-être d'aileurs de sa balise parent à elle.

Exemple: si on déclare une police dans la balise body, tous les paragraphes, toutes les listes, tous les titres, etc. auront la police déclarée dans la balise body (à condition, bien sûr, qu'ils ne modifient pas, eux-mêmes, cette propriété).

Il y a cependant des exceptions, et nous allons voir ce qu'il en est.


## Bibliographie

    - [Specifics on CSS Specificity]()
    - [CSS specificity hierarchy: what you need to know]()
    - [Block and Inline Layout in Normal Flow]()

