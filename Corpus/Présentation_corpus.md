# Présentation du corpus
## Corpus issu de la BNF
La création de ce corpus repose sur une volonté de collaboration entre la Bibliothèque national de France (BNF) qui est la bibliothèque la plus importante de France et la Bibliothèque du Congrès qui est la bibliothèque la plus importante des États-Unis(https://www.bnf.fr/fr/la-france-aux-ameriques). Le corpus de texte s'étend du XVIIIe au XXe siècles. Il faut néanmoins noter qu’il y a une concentration de ces ouvrages sur le XIXe siècle. Notamment dû à l’influence grandissante des États-Unis à cette période dans l’imaginaire collectif français. 

### Un corpus s'inscrivant dans un projet plus grand   
Cette collaboration avec la Bibliothèque du Congrès s’inscrit dans une collaboration beaucoup plus grande qui est le projet “Patrimoine Partagés” (https://www.bnf.fr/fr/patrimoines-partages-0) qui regroupe des corpus en lien entre la France et des pays collaborateurs. Cela va permettre de faciliter l’accès à la quasi-totalité des documents entre la France et le pays collaborateur pour toute personnes le souhaitant.  


## Informations sur le corpus 
Le corpus contient 309 ouvrages issu des 3 siècles considérer. Il y a une très grande diversité de sujets qu’ils soient économiques, religieux, géographique, politique... Dans une aussi grande diversité d’auteurs (237 en tout) venant de tout horizon et de toutes classes sociales. D’ouvrages de marins, en passant par des ouvrages de jésuites, d’écrivains, ou d’aventuriers. Ce corpus regroupe une telle diversité globale qu’il est un outil de travail rêvé pour n’importe quel sujet ayant un lien avec lui.   

### Source des données
Ces données ont été récoltés via le catalogue générale ligne de la BNF via les notices d’ouvrages de ce corpus (https://catalogue.bnf.fr/affinerAdv.do?mots0=ALL%3B1%3B0%3B&mots1=ALL%3B0%3B0%3B&pageRech=rav&corpus=FranceAm&listeAffinages=FacCor_FranceAm&afficheRegroup=false&nbResultParPage=10). 

Nous avons ensuite, via les notices d’ouvrage chercher les notices d’auteurs ainsi que les sujets rameaux qui était associés à ces notices d’ouvrages. Nous avons récupéré tous les identifiants “Ark” (à préciser que qu’avec cette méthode seul les ouvrages manuscrits du catalogue n’ont pas pu être analyser de cette manière).   


### Données récupérées par webscrapping
Une fois ces données récupérer nous avons travaillé sur le code source HTML des pages des notices bibliographiques, de personne, de sujet rameaux.  

1. Nous avons commencé par les “Notices bibliographiques” où nous avons extrait le format, les liens vers les notices personnes et notices rameaux, enfin les liens renvoyant vers Gallica (ce qui nous permet de récupérer les textes). Exemple : `<p class="notice" id="auteur"> <a href="/ark:/12148/cb13185865d" class>Montcalm de Saint-Véran, Louis-Joseph (1712-1759 ; marquis de)</a>` (lien vers les notices personnes).

2. Puis sur le code sources des pages “Notices personnes” où nous avons extrait les identifiants “Ark”. Ainsi que leur nom, prénom, nationalité, sexe, langue, lieu de naissance et de mort ainsi que les dates qui leurs sont associé (quand celles-ci étaient spécifier), enfin les fonctions recenser et les dates auxquelles ils ont exercé ces fonctions. Exemple : ` div id="nationalite class="notice"
<span class= "notice_label">Pays : </span>`(ligne de code en rapport avec la nationalité).

3. Nous avons fini par extraire des “Notices rameaux”, le numéro de la notice, son intitulé, les catégories qui lui sont associés (ce sont de grands thèmes généraux), et les thèmes spécifiques (qui sont plus spécifique, ciblés).  Exemple : `<div class="notice line" id="noticeNum">` (ligne affilié au numéro de la notice).


Récupération faite avec un script Python (O. Julien)

Récupération des textes océrisés
