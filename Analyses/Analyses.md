    Analyses (Damien Vandenheede)

   ## Structure du corpus (détailler le nombre de livres par siècle, le nombre de livres par région)
   
Afin de constituer notre corpus nous avons pris les informations sur le site de la Bibliothèque Nationale de France (BNF). Dans le but de mieux analyser les données nous avons répertorié les ouvrages en fonction du nombre de livres qui ont été publié par siècle. Nous pouvons voir qu'il y a plus de livres au cours du XIXe siècle. Nous ne devons néanmoins pas négliger la période précédente qui est très importante pour la naissance des États-Unis.
    
  ## Importance du XIXe
  
L'augmentation du nombre de livre portant sur les États-Unis en France au XIXe siècle s'explique par le fait qu'il y a une amélioration de l'alphabétisation qui est principalement due aux lois Ferry entre 1880 et 1881 pour rendre l'école gratuite et obligatoire jusqu'à l'âge de treize ans. Nous pouvons voir une multiplication des livres petits formats qui font parfois quelques dizaines de pages qui sont destinés aux plus pauvres. Un livre avec 
plusieurs centaines de pages restent assez coûteux au XIXe siècle. 
  

## Importance des Etats-Unis
Nous avons décidé d'étudier la vision que les Français ont des États-Unis. Le lien entre ces deux pays est important. En effet, la France sous Louis XVI a aidé les insurgés dans leur lutte contre la Grande-Bretagne pour leur indépendance. La France est l'une des première à avoir reconnu l'indépendance des États-Unis. Quand Benjamin Franklin, l'un des Pères fondateurs est venu en France pour voir Louis XVI et s'allier avec le roi. Ce dernier a permis que l'on traduise en français, que l'on fasse imprimer et que l'on diffuse la déclaration d'indépendance de juillet 1776. Il est important de souligner que normalement la censure aurait interdit ce texte qui critique le régime monarchique. La déclaration a une grande influence en France. Elle inspire les révolutionnaires français comme par exemple Brissot qui est un fervent défenseur de la Révolution américaine. Les États-unis et la France gardent de bonnes relations, au fil des décennies et des siècles les États-Unis se développe et devienne une puissance importante qui rivalise avec les pays européens et qui fascine ces derniers. C'est pour cela que nous nous sommes intéressés à la vision que les Français avaient des États-Unis.


Nous avons créé une base de données afin de pouvoir analyser, grâce à des requêtes SQL, la matérialité des livres. 

Nous avons calculé le nombre de pages moyen des livres écrits entre le XVIIe et le XXe siècle grâce à la requête suivante :
`SELECT AVG(Nb_pages) AS "Nb de pages moyen" FROM EDITIONS WHERE Nb_pages IS NOT NULL`

Nous pouvons voir que le nombre moyen de pages est de 251 pages en moyenne. Un livre de 251 pages est relativement important pour cette période. Cela nous montre l'importance des États-Unis pour les Français.

Nous avons calculé le nombre de pages moyen par ouvrages et par siècle grâce à la requête suivante : 

`SELECT Siecle_edition, AVG(Nb_pages) AS "Nb de pages moyen" FROM EDITIONS WHERE Nb_pages IS NOT NULL GROUP BY Siecle_edition`

| Siècle | Nombres moyen de pages |
| ---------- | -------------|
| XVIIe |320|
|XVIIIe|224|
|XIXe|247|
|XXe|293|


Nous pouvons voir qu'il y a une diminution du nombre moyen de pages puis une augmentation. Nous pouvons interprêter cela de plusieurs manières : premièrement nous l'avons vu il y a une amélioration de l'alphabétisation de la population, les plus pauvres ne pouvaient se procurer que des livres avec peu de pages. Deuxièmement, l'augmentation du nombre de pages au XXe siècle s'explique par le fait que les États-Unis est une puissance importante qui continue de fasciner les Européens et surtout les Français. Ce ne sont que des suppositions, nous ne pouvons pas connaître les causes de ces évolutions.



    Présence d'illustrations

    Nous avons fait une analyse des fonctions des auteurs grâce à la requête suivante :
    
`SELECT Categorie_fonction, COUNT(*) FROM FONCTIONS  
WHERE Categorie_principale = 1
GROUP BY Categorie_fonction`

| Fonction | Nombre d'auteurs qui l'exerce|
| ---------- | -------------|
| Artistes |10|
|Homme d'affaires|7|
|Hommes de lettres|57|
|Juriste|11|
|Militaire|22|
|Politique ou administrateur|15|
|Religieux|31|
|Scientifique|32|
|Voyageur|11|

Nous pouvons souligner le fait que les auteurs sont exclusivement masculins. Il est compliqué d'expliquer cela en quelques mots, évoquons simplement qu'il était plus difficile pour les femmes de pouvoir publier leurs travaux.Ce sont essentiellement des hommes qui se sont rendus aux États-Unis. Dans le tableau si dessus nous pouvons voir que les fonctions exerçaient sont masculinisées. Il faut néanmoins évoquer le fait qu'il y a des femmes qui exercent ces métiers.  

    Evolution des fonctions
Avec la requête suivante : `SELECT Intitule_fonction FROM Fonctions WHERE Intitule_fonction LIKE '%Jésuite%' 
OR Intitule_fonction LIKE '%jésuite%'` 
nous pouvons compter le nombre de jésuites. Il y a 12 jésuites parmi les 31 religieux que nous avons répertiorié. La présence de religieux puis leur disparition progressive au fil des siècles peut s'expliquer par le fait que suite à la "découverte" de l'Amérique des religieux fuyant l'intolérance en Europe partent se réfugier en Amérique. Il y a également des missionnaires comme les jésuites, qui s'y rendent afin d'évangéliser les populations autochtones. 
    



| Région | Nombre d'ouvrages publiés par région|
| ---------- | -------------|
|Canada |44|
|Est des Etats-Unis |38|
|Ouest Etats-Unis|37|
|Louisiane |21|
|Amérique latine |14|

Nous nous sommes concentrés sur les ouvrages rédigés au XIXe siècle élaborer ce tableau. Les ouvrages répertioriés évoquent le lien entre la France et les Etats-Unis mais aussi la vision que les Français ont de ces derniers. 





    
