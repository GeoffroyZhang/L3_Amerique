# Structure de la base de données (Geoffroy Zhang)

Inventée par le mathématicien Edgar F. Codd, la base de données relationnelle se définit comme : "un ensemble structuré de données reliées entre elles et stockées de manière cohérente, sans redondance inutile" (Marc Humbert, *Les bases de données*, Paris, Hermes, 1991).
Notre base de données relationnelle se structure, comme toutes les bases, d'un ensemble de tables et de divers autres éléments que nous expliquerons ci-dessous. Cette base de données a été créée sur la base du corpus d'ouvrages sur l'Amérique issu du catalogue général de la BnF.

## Le modèle conceptuel des données (MCD) de notre corpus

La méthode de modélisation d'une base de données passe par plusieurs étapes préalables. Premièrement l'identification des entités, attributs et relations du MCD ; puis de l'identification de la cardinalité des relations ; enfin de la définition et de la liaison des tables. 

Le MCD est l'étape préalable à la conception d'une base de données. En effet, celui-ci nous a permis, dans le cadre de ce projet, de modéliser les données du corpus au sein d'une structure organisée qui indique différents éléments :
- Les **entités** : la chose que l'on décrit ;
- Les **attributs** : ce qui décrit ou caractérise une chose ;
- Les **relations** : les relations entre les entités.

Le MCD est composé de : 

- Les **tables** ;
- Leurs **champs** ;
- Leur **type de donnée** (entier, texte, booléen); 
- Les **clés primaires** et **étrangères** ;
- Les **relations entre les tables** et leur **signification** ;
- Les **cardinalités**.

**<ins>Schéma du MCD d'apès le corpus Amérique du catalogue de la BnF : </ins>**
![MCD_Corpus_Amérique](https://github.com/user-attachments/assets/15ffb8cd-2d3a-4058-96bf-1fa9dfaf1b9e)

Le MCD a été crée sur la base du corpus d'ouvrages sur l'Amérique du catalogue général de la BnF. 

**<ins>Explication du choix des entités, de leurs attributs et de leurs relations :</ins>**

Tout d'abord, nous avons identifié les entités, les attributs et leur relation, après l'analyse du corpus. Cette ébauche nous a permis de dresser notre MCD. Les entités sont représentées par des tables en forme de boîte aux angles à 90 degrés ; alors que les relations sont caractérisées par des boîtes aux angles plus arrondis et contiennent souvent des verbes (Ex. *Parle de* pour la relation de l'entité *TEXTE* et *SUJETS*). Ainsi, la base de données est composée de diverses tables ou entités que sont : les tables *EDITIONS*, *FONCTIONS*, *TEXTES*, *AUTEURS* et *SUJETS*. 

Le choix des entités a été le produit d'une réflexion en classe après avoir analysé la structure du corpus. En effet, chaque nom d'entité (Ex. *TEXTES*) caractérise l'élément que nous décrivons. L'entité *TEXTES* correspond à un texte de la base de données ; il est donc important de connaître son contexte d'édition d'où la relation *Publié dans* avec l'entité *EDITIONS*, en effet, on part du principe que chaque texte a été édité au moins une fois. De même, il est intéressant de connaître le ou les sujets du texte en question, d'où la relation "Parle de" entre l'entité *TEXTES* et l'entité *SUJETS* ; en effet, un texte parle forcément d'un ou plusieurs sujets. Ainsi, les attributs - ce qui décrit ou caractérise une chose - de l'entité *TEXTES* décrivent des informations relatives à l'ouvrage tel que son titre, sa langue ou encore son contenu. Ces attributs ont été choisis car nous les avons récupérés sur les notices bibliographiques qui donnent des informations sur les ouvrages. De même pour les attributs de l'entité *EDITION* qui permettent donc de connaître diverses informations sur la forme de l'ouvrage et son contenu. En effet, l'attribut  "Nb de pages" permet de savoir précisément le nombre de pages de l'ouvrage ce qui est intéressant si on essaie de situer le texte dans une certaine époque. L'entité *SUJETS* permet de décrire le sujet du texte, autrement dit, de savoir de quoi parle le texte (Ex. L'attribut "désignation" dans la table *SUJETS* permet de connaître l'intitulé précis du texte). Il se peut qu'il y ait une dépendance fonctionnelle, c'est-à-dire un lien qui existe entre 2 attributs lorsqu'un attribut détermine un second attribut (problème de redondance). Dans ces cas-là, pour optimiser le MCD, nous créons une autre entité, c'est le cas de l'entité *SUJETS*. Ainsi, ces attributs ont été choisis car on peut les retrouver sur les notices bibliographiques.  

L'entité *AUTEURS* est tout aussi centrale dans le MCD. En effet, le corpus ducumentaire sur l'Amérique nous donne des informations sur les auteurs et, de plus, chaque texte est forcément écrit par (la relation) un auteur, d'où sa relation avec l'entité *TEXTES*, modélisée par la table de jonction *ECRIT_PAR*. L'entité *AUTEURS* nous permet de connaître diverses informations sur ce qui caractérise l'auteur (attributs), c'est-à-dire son nom, son prénom, son sexe, sa date de naissance, son lieu de naissance, sa date de décès, son lieu de décès ou encore sa nationalité. Il peut être intéressant de connaître la nationalité des auteurs qui écrivent sur l'Amérique et l'époque à laquelle ils ont écrit. Ces informations peuvent être trouvées sur les notices de personne du catalogue général de la BnF. L'entité *FONCTIONS* décrit la fonction d'un auteur, d'où la relation "Exerce" avec l'entité *AUTEURS*. En effet, via ses attributs, on peut obtenir des informations précises sur la fonction de l'auteur, telles que son intitulé, la catégorie de celle-ci ou encore son lieu d'exercice. La clé étrangère "Ref_auteur" fait référence à la clé primaire de la table *AUTEURS*. En effet, on place la clé étrangère dans la table de l'entité multiple. 

**<ins>Explication des cardinalités :</ins>**

Les cardinalités indiquent le nombre d'entités pouvant entrer en relation. Pour caractériser ces relations, nous prenons en compte le maximum, c'est-à-dire le deuxième élément de la cardinalité. 

<ins>On a 3 types de cardinalité :</ins>   
- 1:1 = fusion des tables : on a une correspondance ;  
- 1:n = deux tables séparées avec une clé étrangère nécessaire dans celle de l'entité ou de l'attribut multiple : on a une ou plusieurs correspondances ; 
- n:n = table de jonction. 
Le caractère se situant à gauche désigne le minimum et celui de droite, le maximum. 
La clé étrangère, c'est-à-dire le champ qui fait référence à la clé primaire d'une autre table, est nécessaire dans le champ de l'entité ou de l'attribut multiple.

*Pour plus d'informations sur les cardinalités : [IBM](https://www.ibm.com/docs/fr/cognos-analytics/11.1.0?topic=r-cardinality)*

Pour ce qui est de notre MCD, nous avons une relation de n:1 entre la table *TEXTES* et la table *EDITIONS*, illustrée par la relation *Publié dans*, autrement dit, un texte est publié au minimum une fois et au maximum n fois, c'est-à-dire plusieurs fois. Au contraire, l'édition ne fait référence qu'à un et un seul texte. 
Nous avons également une relation de n:1 entre les tables *TEXTES* et *SUJETS*, illustrée par la relation *Parle de*. En effet, un texte peut parler d'un ou plusieurs sujets et un sujet ne peut que concerner un seul texte. 
Il se peut qu'un auteur ait écrit plusieurs textes, autrement dit, que plusieurs textes ont été écrits par un auteur ou plusieurs auteurs. En effet, pour éviter de la redondance dans les tables, nous créons une table de jonction (relation n:n) illustrée par la table *ECRIT_PAR*, qui contient deux clés étrangères qui font référence aux clés primaires des tables *TEXTES* et *AUTEURS*. Ainsi, on crée une table intermédiaire symbolisée par la relation entre les deux tables de relation n:n puisqu'il n'est pas possible de mettre de clé étrangère dans l'une ou l'autre table. 
Enfin, la table *AUTEURS* est liée à la table *FONCTIONS* par une relation de 1:n. Autrement dit, un auteur a pu exercer 0, 1 ou plusieurs fonctions et une fonction a été exercée par au moins un auteur et un seul. 

**<ins>Utilisation des identifiants ARK comme clés primaires :</ins>**

Un identifiant ARK (Archival Resource Key) est un format d'identifiant créé en 2001 par la California Digital Library permettant d'identifier des ressources de tous types : physiques, numériques et immatérielles. Pour plus d'informations sur l'identifiant ARK veuillez suivre ce lien : [L'identifiant ARK](https://www.bnf.fr/fr/lidentifiant-ark-archival-resource-key.  

Les identifiants ARK permettent de retrouver les éléments plus facilement. Ils renvoient à des notices  bibliographiques et à des notices de personne. Par exemple, l'identifiant ARK/clé primaire de la table *AUTEURS* renvoie à une notice de personne : [Exemple de notice de personne](https://catalogue.bnf.fr/ark:/12148/cb13185865d). L'identifiant ARK de la table *EDITIONS* renvoie à une notice bibliographique : [Exemple de notice bibliographique](https://catalogue.bnf.fr/ark:/12148/cb300062607). La clé primaire est un champ qui doit être présent dans chaque table avec une numérotation unique. Le type de données de la clé primaire est souvent un entier, mais dans le cas des identifiants ARK, il s'agit d'un texte court.

Dans le cadre de notre base de données, l'utilisation des identifiants ARK permet directement de renvoyer à l'auteur ou à l'édition précise du texte. Il permet l'identification directe de la ressource, ce n'est pas un permalien, c'est-à-dire une URL. Ainsi, l'identifiant ARK est unique, ce qui convient parfaitement à la définition d'une clé primaire. 

## Le dictionnaire des données 

Le dictionnaire des données est un référentiel d'informations relatif aux bases de données. Autrement dit, c'est une liste des informations que l'on veut enregistrer dans la base de données. C'est la description complète des champs de chaque table (nom, type, description). Par exemple, dans notre MCD, le champ "Prénom" de la table "AUTEURS" a pour type un entier avec une description sur le nom de famille. Ainsi, le dictionnaire de données décrit les différentes informations d'une base de données.

Exemple de dictionnaire des données du projet sur le corpus d'ouvrages sur l'Amérique pour la table *FONCTIONS* : 

| Nom | Type |Remarques|
| ----------- | ----------- | ----------- |
| ID_fonction | Entier | Clé primaire |
| Intitule_fonction | Texte court | Intitulé de la fonction de l'auteur |
| Catégorie_fonction | Texte court | Catégorie de la fonction de l'auteur |
| Catégorie_principale | Booléen | Désigne la caractère principal du métier ou non |
| Lieu_fonction | Texte long | Lieu d'exerice de la fonction |
| Ref_auteur | Entier | Clé étrangère faisant référence à la clé primaire ID_Ark_auteur de la table *AUTEURS* |

Exemple de dictionnaire des données du projet sur le corpus d'ouvrages sur l'Amérique pour la table *AUTEURS* : 

| Nom | Type |Remarques|
| ----------- | ----------- | ----------- |
| ID_ARK_auteur | Texte court | Clé primaire |
| Nom | Texte court | Nom complet de l'auteur |
| Prenom | Texte court | Prénom complet de l'auteur |
| Sexe | Texte court | Sexe de l'auteur |
| Nationalite | Texte court | Nationalité de l'auteur |
| Date_naissance | Entier | Date de naissance de l'auteur |
| Lieu_naissance | Texte court | Lieu de naissance de l'auteur |
| Date_deces | Entier | Date de décès de l'auteur |
| Lieu_deces | Texte court | Lieu de décès de l'auteur |

Exemple de dictionnaire des données du projet sur le corpus d'ouvrages sur l'Amérique pour la table *ECRIT_PAR* : 

| Nom | Type |Remarques|
| ----------- | ----------- | ----------- |
| ID_ecrit_par| Entier | Clé primaire |
| Ref_Ark_auteur | Texte court | Clé étrangère faisant référence à la clé primaire ID_auteur de la table *AUTEURS* |
| Ref_texte | Entier | Clé étrangère faisant référence à la clé primaire ID_texte de la table *TEXTES* |
| Role | Texte court | Rôle de l'auteur |

Exemple de dictionnaire des données du projet sur le corpus d'ouvrages sur l'Amérique pour la table *TEXTES* : 

| Nom | Type |Remarques|
| ----------- | ----------- | ----------- |
| ID_texte | Entier | Clé primaire |
| Titre | Texte court | Titre complet de l'ouvrage |
| Langue | Texte court | Langue de l'ouvrage |
| Region | Texte court | Région de l'ouvrage |
| Contenu texte | Texte long | Contenu de l'ouvrage |

Exemple de dictionnaire des données du projet sur le corpus d'ouvrages sur l'Amérique pour la table *EDITIONS* : 

| Nom | Type |Remarques|
| ----------- | ----------- | ----------- |
| ID_edition | Entier | Clé primaire |
| Date_edition_inf | Entier | Date d'édition inférieure de l'ouvrage |
| Date_edition_sup | Entier | Date d'édition supérieure de l'ouvrage |
| Siecle_edition | Entier | Le siècle d'édition de l'ouvrage |
| Lieu_edition | Texte court | Le lieu d'édition de l'ouvrage |
| Nom_edition | Texte court | Le nom de l'éditeur de l'ouvrage |
| Format | Texte court | Le format du texte |
| Illustrations | Booléen | La présence d'illustrations ou non |
| Nb_pages | Entier | Le nombre de pages |
| Nb_volumes | Entier | Le nombre de volumes |
| Taille | Entier | La taille de l'ouvrage |
| Ref_texte | Entier | Clé étrangère faisant référence à la clé primaire ID_texte de la table *TEXTES* |

Exemple de dictionnaire des données du projet sur le corpus d'ouvrages sur l'Amérique pour la table *SUJETS* : 

| Nom | Type |Remarques|
| ----------- | ----------- | ----------- |
| ID_sujet | Entier | Clé primaire |
| Désignation | Texte court | Sujet de l'ouvrage |
| Ref_ARK_edition | Entier | Clé étrangère faisant référence à la clé primaire ID_edition de la table *EDITIONS* |

## Recodage des données 

Le recodage des données se fait par un système de gestion de base de données, c'est-à-dire un logiciel permettant aux utilisateurs de créer et de gérer des bases de données. Notre base de données est hébergée sur le logiciel *phpMyAdmin* et sur LibreOffice Base. 

**<ins>Les siècles des éditions :</ins>**

Nous avons ajouté, à l'aide de requêtes SQL (Structured Query Language), une colonne "Siècle_edition" dans la table *EDITIONS* de notre base de données afin de préciser le siècle - la date n'étant pas souvent claire - d'édition de l'ouvrage. Ces requêtes ont été appliquées dans le menu SQL, dans la fenêtre principale de la base de données, sur le logiciel Base d'OpenOffice.

| Siècle | Requête SQL | Nombre d'ouvrages |
| ----------- | ----------- | ----------- |
| XVIe siècle  |  `UPDATE "Editions" SET "Siecle_edition"=16 WHERE("Date_edition_inf"+"Date_edition_sup")/2 BETWEEN 1500 and 1599` |1 ouvrage|
| XVIIe siècle  | `UPDATE "Editions" SET "Siecle_edition"=17 WHERE("Date_edition_inf"+"Date_edition_sup")/2 BETWEEN 1600 and 1699` |25 ouvrages|
| XVIIIe siècle  | `UPDATE "Editions" SET "Siecle_edition"=18 WHERE("Date_edition_inf"+"Date_edition_sup")/2 BETWEEN 1700 and 1799` |42 ouvrages|
| XIXe siècle  | `UPDATE "Editions" SET "Siecle_edition"=19 WHERE("Date_edition_inf"+"Date_edition_sup")/2 BETWEEN 1800 and 1899`|210 ouvrages|
| XXe siècle  | `UPDATE "Editions" SET "Siecle_edition"=20 WHERE("Date_edition_inf"+"Date_edition_sup")/2 BETWEEN 1900 and 1999`|23 ouvrages|

Ainsi, ces requêtes nous aide clairement à identifier quel siècle à été le plus prolifique, en effet, le XIXe siècle ressort le plus souvent. 

**<ins>Les auteurs manquants :</ins>**

Nous avons également, dans la table *AUTEURS* ajouté manuellement les auteurs là où il en manque via le système de gestion de base de données. Cela a été possible grâce à l'identifiant ARK qui nous renvoie, comme dit précédemment, sur les notices bibliographiques puis sur les notices de personne, nous donnant ainsi des informations sur le nom, le prénom et le genre de l'auteur en question. 

**<ins>Les régions couvertes par les ouvrages :</ins>**

Avec l'utilisation du logiciel de textométrie TXM, nous avons pu situer les principales zones géographiques couvertes par les ouvrages du corpus. Nous avons sélectionné les lieux qui revenaient le plus souvent afin de définir des catégories géographiques. Nous avons ainsi identifié plusieurs catégories géographiques que sont : les régions de l'ouest des Etats-Unis, les Antilles/îles, les régions de l'est des Etats-Unis, l'Amérique latine, la Louisiane et le Canada. On associe une région principale à chaque texte de la table *TEXTES*. Enfin, avec l'aide de requêtes SQL, nous avons mis à jour la base de données et notamment la colonne "Region" de la table *TEXTES* avec la requête suivante : 

``` 
SELECT * FROM TEXTES 
UPDATE TEXTES SET Region = 'Nom de la catégorie' 
WHERE Titre LIKE '%Mot recherché%'
```

Par exemple, pour les ouvrages parlant des Antilles/îles nous utilisons la requête suivante : 

``` 
SELECT * FROM TEXTES
UPDATE TEXTES SET Region ='Antilles/îles'
WHERE Titre LIKE '%Antilles%'
OR Titre LIKE '%Martinique%'
OR Titre LIKE '%Domingue%'
OR Titre LIKE '%Guadeloupe%'
``` 

Ainsi, pour tous les ouvrages qui contiennent, dans leur titre, le mot "Antilles", "Martinique", "Domingue" et "Guadeloupe", la catégorie "Antilles/îles" sera placée dans le champ "Region". 

**<ins>Les fonctions/métiers des auteurs :</ins>**

Le logiciel TXM nous a également permis de catégoriser les fonctions des auteurs et de créer des catégories socio-professionnelles. Nous avons ainsi identifié plusieurs catégories socio-professionnelles que sont : les hommes de lettres, les artistes, l'armée, les scientifiques, les politiques, les religieux, les professions juridiques, les explorateurs/voyageurs et les indéfinis. En effet, il existe une multitude de fonctions que nous avons trouvé plus judicieux de ranger dans des catégories socio-professionnelles pour mieux organiser la base et pour sa clarté . Ainsi, un missionnaire ou un jésuite sera classé dans la catégorie "religieux".  

Dans la table *FONCTIONS*, chaque fonction est identifié par un "ID_fonction" unique (clé primaire). On connaît également, à travers ses attributs, l'intitulé de la fonction, la catégorie de cette fonction ou encore le lieu de son exercice. Cette table est rattachée à la table *AUTEURS* par la clé étrangère "Ref_auteur" ce qui nous permet d'avoir des informations sur l'auteur, autrement dit, celui qui exerce la fonction. 

Il est intéressant de connaître la fonction de l'auteur, mais bien souvent, certains auteurs exercent plusieurs fonctions. Nous avons donc décidé, dans la table *FONCTIONS*, de distinguer la fonction principale de chaque auteur à l'aide de valeurs booléennes illustrées par la colonne "Categorie_principale". En effet, on considérera la valeur booléenne 1 comme étant la fonction principale et la valeur booléenne 0 comme étant les fonctions secondaires. 

Voici la requête SQL permettant de connaître la fonction principale pour chaque auteur :  

``` 
SELECT ID_fonction, Intitule_fonction, Categorie_principale, Categorie_fonction FROM FONCTIONS WHERE Categorie_principale = 1
``` 

[Page de présentation](/Présentation.md)

[Structure détaillée du corpus](main/Analyses.md)

[Présentation du corpus](main/Présentation_corpus.md)

[Conclusion](main/Conclusion.md)
  


 
