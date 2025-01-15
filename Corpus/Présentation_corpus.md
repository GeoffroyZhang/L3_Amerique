# Présentation du corpus

## Corpus issu de la BNF
La création de ce corpus repose sur une volonté de collaboration entre la [Bibliothèque national de France](https://www.bnf.fr) (BNF) qui est la bibliothèque la plus importante de France et la Bibliothèque du Congrès qui est la bibliothèque la plus importante des États-Unis. Le corpus de texte s'étend du XVIIIe au XXe siècles. Il faut néanmoins noter qu’il y a une concentration de ces ouvrages sur le XIXe siècle. Notamment dû à l’influence grandissante des États-Unis à cette période dans l’imaginaire collectif français. 

### Un corpus s'inscrivant dans un projet plus grand   
Cette collaboration avec la Bibliothèque du Congrès s’inscrit dans une collaboration beaucoup plus grande qui est le projet “Patrimoine Partagés” qui regroupe des corpus en lien entre la France et des pays collaborateurs. Cela va permettre de faciliter l’accès à la quasi-totalité des documents entre la France et le pays collaborateur pour toute personnes le souhaitant.  


## Informations sur le corpus 
Le corpus contient 309 ouvrages issu des 3 siècles relaté.  

### Source des données
Ces données ont été récoltés via le catalogue générale ligne de la BNF via les notices d’ouvrages de ce corpus. Nous avons ensuite, via les notices d’ouvrage chercher les notices d’auteurs ainsi que les sujets rameaux qui était associés à ces notices d’ouvrages. Nous avons récupéré tous les identifiants “Ark” (à préciser que qu’avec cette méthode seul les ouvrages manuscrits du catalogue n’ont pas pu être analyser de cette manière).   


### Données récupérées par webscrapping
Une fois ces données récupérer nous avons travaillé sur le code source HTML des pages des notices bibliographiques, de personne, de sujet rameaux.  

1. Nous avons commencé par les “Notices bibliographiques” où nous avons extrait le format, les liens vers les notices personnes et notices rameaux. 

2. Puis sur le code sources des pages “Notices personnes” où nous avons extrait les identifiants “Ark”. Ainsi que leur nom, prénom, nationalité, sexe, langue, lieu de naissance et de mort ainsi que les dates qui leurs sont associé (quand celles-ci étaient spécifier), enfin les fonctions recenser et les dates auxquelles ils ont exercé ces fonctions.  

3. Nous avons fini par extraire des “Notices rameaux”, le numéro de la notice, son intitulé, les catégories qui lui sont associés (ce sont de grands thèmes généraux), et les thèmes spécifiques (qui sont plus spécifique, ciblés).  


Récupération faite avec un script Python (O. Julien)

Récupération des textes océrisés

[Page de présentation](/Présentation.md)
