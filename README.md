# ElectroTeXnique <img src="parametres/github/logo_compagnons.png" align="right" height="45"/>
 
**Clean** LaTeX template of educational content for highly qualified craftsmen in electrical engineering

## Pour commencer

Canevas de rédaction et support de cours destiné au (gros) chantier de création de contenus pédagogiques pour les formations en électrotechnique octroyées à l'AOCDTF.


| Page de couverture  | Page de titre |
| :------------------: | :------------------: |
| ![Page de couverture](parametres/github/page_couverture_pied_page.png) | ![Page de titre](parametres/github/page_titre.png) |

## Pré-requis

1. Installer LaTeX avec la distribution [TexLive](https://www.tug.org/texlive/), l'éditeur [Texmaker](https://www.xm1math.net/texmaker/index_fr.html), le programme de gestion des bibliographie [Biber](http://biblatex-biber.sourceforge.net), l'éditeur d'image en format vectoriel [Inkscape](https://inkscape.org/fr/), l'extracteur de données issues de graphiques [WebPlotDigitzer](https://automeris.io/WebPlotDigitizer/) et le logiciel de géométrie [Geogebra](https://www.geogebra.org/?lang=fr).

2. Bien paramétrer l'éditeur Texmaker :

<p float="left">
  <img src="parametres/github/set1.png" width="200" />
  <img src="parametres/github/set2.png" width="200" /> 
  <img src="parametres/github/set3.png" width="200" />
</p>

5. Ajouter le package "AOCDTF" et les autres packages du dossier `/BTS-ElectroTeXnique/parametres/packages_manquants` dans le dossier contenant les packages `texlive/2020/texmf-dist/tex/latex` avec les docs correspondantes, se référer au tutoriel présent dans le même dossier "tutoriel_ajout_packages.pdf" (ne pas oublier de rafraichir la database et de le préciser).

4. Eplucher les documentations sur LaTeX (entre autre) :
    - `base_de_donnees/latex/masson-fiches_latex/...`
    - `base_de_donnees/latex/goulet-redaction_latex.pdf`

## Initiation de la programmation d'un nouveau cours

1. Cloner le dépôt BTS-ElectroTeXnique à l'aide de l'application Github Desktop et, importer le dépôt et créer une nouvelle branche nommée "Branche-votrenom".

2. Ne pas renommer les fichiers clonés mais indiquer en tête de chaque programmation pour repérer facilement le nouveaux cours :

``` bash
%--------------------------------------
%INTITULE DU COURS 
%--------------------------------------
```

3. Ajouter les informations relatives au cours en question dans les page de titre, couverture et autres informations.

4. **Rectifier l'arborescence des fichiers.bib (en s'aide du fichier `INDICATEUR_ARBORESCENCE.tex`) car celle du canevas n'est pas la même que celle pour les cours !**

5. Si des modifications sont à ajouter au préambule ou au canevas, **consulter** l'équipe pour qu'on puisse ajouter ces modifications au préambule du canevas si c'est pertinent.

## Rédaction de la programmation d'un nouveau cours

1. Utiliser la programmation "document_maitre" seulement pour accueillir les appels de sous-programmation (chapitres, préambules, sous-programmation de mise en page...).

2. Pour la rédaction de nouveaux chapitres ou de figure/tableaux complexes, créer une sous-programmation :
    - en exécutant `fichier -> nouveau à partir d'un document existant` et sélectionner `MWE.tex` (Minimal Work Environnement);
    - en enregistrant la sous-programmation dans le même dossier que le document maître du cours.

3. pour nommer le fichier du nouveau chapitre, tableau, figure... , il faut respecter une nomenclature pour faciliter le classement des fichiers :
    - objet_mot-clé-général_mot-clé-précis(_mot-clé-plus-précis) avec objet =
        
        - chap_x_mot-clé-général_mot-clé-précis(_mot-clé-plus-précis)     => chapitre
        - chap_A_mot-clé-général_mot-clé-précis(_mot-clé-plus-précis)     => annexe
        - sec_xx_mot-clé-général_mot-clé-précis(_mot-clé-plus-précis)     => section
        - tab_mot-clé-général_mot-clé-précis(_mot-clé-plus-précis)        => tableau
        - fig_mot-clé-général_mot-clé-précis(_mot-clé-plus-précis)        => figure
        - eq_mot-clé-général_mot-clé-précis(_mot-clé-plus-précis)         => équation

4. Si une sous-programmation demande des dossiers de fichiers spécifiques (image, données brutes...), regrouper ces fichiers dans un sous-dossier mais pas la sous-programmation en elle-même pour regrouper toutes les programmations et sous-programmations dans un seul dossier et éviter les arborescences foireuses pour les appels de sous-programmation dans les programmations maitres :
    - se référer au cours de pré-requis pour les sous-programmations-types à suivre (tableau, figure, graphe...);
    - pour structurer son texte et les listes, se référer au cours de pré-requis et à la nomenclature approuvée tous ensemble avec entre autre :
        - `\\` + un seul retour à la ligne : nouveau sujet dans le même paragraphe
        - `\\` + deux retour à la ligne (saut de ligne) : nouveau paragraphe dans la même division
        - `\description` et `\itemize` : les listes et les définitions
        - `\compactitemize` `\tabdescription` : liste compacte pour les listes et descriptions dans les tableaux (voir commentaire de code en préambule)
        - respecter les règles de typographie française (voir `/bases_de_donnees/latex/goulet-redaction_latex.pdf` et `/bases_de_donnees/latex/hufflen-typographie_conventions_latex.pdf`)
    - grands classiques de typographie avec entre autre :
        - Gestion des tirets et des cadratins voir `/bases_de_donnees/latex/goulet-redaction_latex.pdf`
        - Accent même pour les majuscule `\’E` ou `\È` ou `\À`
        - Guillemets français `\og \fg{}`
        - Liste d’éléments se terminant par l'instruction `\,;` quand ce sont des phrases (sauf la dernière)
        - Bien faire attention à `\oe{}`,  `\iere{}`, `\Dr`, les points de suspensions `\ldots...`
		- Voir les tableaux et les environnement mathématiques pour les canevas d'écritures
      	- Consulter le `package{SIunitx}` pour l’écriture de unités de physique et utiliser la commande `\SI{nombre}{unitéenanglais}` pour respecter l'espacement

5. Rédiger les équations dans le nouvel environnement `\begin{equa}` qui va référencers les équations dans une liste d'équations et décrire les équations dans les nouveaux environnements `\begin{numvariables}`(description des variables numériquement) et `\begin{textvariables}` (description des variables mathématiquement).
                
6. Pour labeliser les sous-programmations (avec le même intitulé que les noms de fichier de ces sous-programmations quand c'est le cas), figures, équation... :
    - \label{objet:mot-clé-général_mot-clé-précis(_mot-clé-plus-précis)} avec objet =
        
        - chap:mot-clé-général_mot-clé-précis(_mot-clé-plus-précis)     => label chapitre
        - ann:mot-clé-général_mot-clé-précis(_mot-clé-plus-précis)      => label annexe
        - sec:mot-clé-général_mot-clé-précis(_mot-clé-plus-précis)      => label section
		- subsec:mot-clé-général_mot-clé-précis(_mot-clé-plus-précis)	=> label subsection
        - fig:mot-clé-général_mot-clé-précis(_mot-clé-plus-précis)      =>label figure
        - tab:mot-clé-général_mot-clé-précis(_mot-clé-plus-précis)      => label tableau
        - pas:mot-clé-général_mot-clé-précis(_mot-clé-plus-précis)      => label pastille d'annotation                
        - eq:mot-clé-général_mot-clé-précis(_mot-clé-plus-précis)       => label équation
		- def:mot-clé-général_mot-clé-précis(_mot-clé-plus-précis)	=> label définition

7. Ne pas oublier de référencer les sources à l'aide de la bibliographie que l'on alimente au fur et à mesure de la rédaction et d'inclure des liens de références internes à l'aide des labels.

8. Vérifier dans package "AOCDTF.sty" toutes les macros qui ont pu y être ajoutées (bien souvent précédées d'une instruction type `\newcommand{nouvelleinstruction}{cequecette instructionexecute}`.

9. Une fois la rédaction de la sous-programmation effectuée, l'appeler dans sa programmation maitre en suivant bien les consignes en début de programmation avec le `\package{comment}` qui permet de mettre en commentaire toute la portion de code se situant dans cet environnement et l'instruction `%` qui aura le même effet sur une ligne.

``` bash
%utiliser les environnement \begin{comment} \end{comment} pour mettre en commentaire 
le préambule une fois la programmation appelée dans le document maître 
(!ne pas oublier de mettre en commentaire \end{document}!)
```

10. Une fois tout le cours rédigé, vérifier que la compilation du document maître du cours s'effectue correctement (bibliographie, position d'image, table des matières...), compiler plusieurs fois et réorganiser le document avec `\newpage` et `\pagebreak` si des images ou des parties de paragraphes doivent sauter une page (fonctionne aussi dans les tableaux avec la consigne `\noalign{\break}`). Pour forcer le placement de figures, utiliser la commande `\begin{figure}[h]`, `\begin{figure}[h!]` voire même `\begin{figure}[H]`.

## Charte graphique des figures

1. Maximiser au possible les programmations sous LaTeX pour les figures (en utilisant la couche PGF-Tikz) pour conserver une unité graphique. 

2. Pour les graphiques, extraire les données à l'aide de WebPlotDigitzer dans un fichier "donneesdugraphique.csv" qui sera simplement renommé en "donneesdugraphique.txt" pour importer ces données dans un graphique codé sous PGF-Tikz et conserver ainsi l'unité graphique (légende, référençage...)

## Bibliographie

- Référencer les documents et sites utilisés dans les fichiers de bibliographie correspondants en n'ajoutant pas trop de métadonnées et en choisissant le bon type de références(book, incollection, report...);
 
- classement des références **dans l'ordre alphabétique** des clés :
    - si il s'agit de plusieurs référénces d'un site même site internet (wikipedia, cours en ligne, Guide de l'électrotechnique...à) sont identiques comme suit : `@PremièreSlettreSdusite:acronymedutitre` (ex. : `@wiki:TPE`pour l'article sur le tableau périodique des éléments de Wikipédia)
    - Pour les normes, utiliser la classe @manual et la clé d'appel de la référence comme suit : 
    `@typedenorme:numérodenorme-année`
    - si il s'agit de plusieurs référénces d'un site même site internet (wikipedia, cours en ligne, Guide de l'électrotechnique...à) sont identiques comme suit : `@PremièreSlettreSdusite:acronymedutitre` (ex. : `@wiki:TPE`pour l'article sur le tableau périodique des éléments de Wikipédia)
	- Pour les cours et polycopiés, clé d'appel de la référence comme suit : `@Etablissementcoursannée` ou si l'intitulé du cours est trop long pour une clé compacte, utiliser son acronyme)
    - Pour les livres et similaires, clé d'appel de la référence comme suit (si plusieurs auteurs, mettre chaque nom dans l'ordre alphabétique) : `@Nomdel'auteurannée`
    - Si l'auteur et l'année sont identiques comme suit : 

```
@Nomdel'auteurannéeA 
@Nomdel'auteurannéeB
``` 

- Si citation ou référence à un passage spécifique d'un ouvrage, référencer les page/chapitre/section, exemple instruction :

```
\bookpagination = {chapitre},
\pages = {1-2, 8},
```

- Se référer aux documents présents dans la base de donnée (entre autre) pour plus d'informations :
``` bash
base_de_donnees/latex/masson-fiches_latex/biblatexmichu.pdf
base_de_donnees/latex/gaborit-latex_bibliograhie.pdf
```

- Vérifier, ne sait-on jamais, jamais que deux références identiques n'ont pas été ajoutées à la même bibliographie;

- Pour ajouter une nouvelle bibliographie à un document maître d'un cours, s'aider de l'instruction `\include{INDICATEUR_ARBORESCENCE}` pour indiquer l'arborescence du fichier.bib à ajouter;

- Pour la faire apparaitre dans le pdf final, compiler le fichier .bib avec le compilateur BibTeX avant de faire une compilation rapide sur le document maître.

## Base de données

- Déposer dans le dossier `/base_de_données`, situé dans le Onedrive d'équipe, tous les documents utilisés pour la rédaction des cours, à inclure également dans la bibliographie;

- Règle de rédaction des documents :

    1. Attention à ne pas utiliser d'espace, ni d'accent, ni de majuscule
    2. Importer les fichiers dans les cours correspondant si le document est spécifique au cours, sinon l'importer dans le fichier ressources_communes

- Si c'est un livre ou similaire, renommer le nom du document comme suit : 
```bash
Nomdel'auteur-Titre du document(-année-établissement)
```

- Si c'est un dossier de cours ou polycopié, renommer le nom du document comme suit : 
```bash
Etablissement-Titre du document(-année-auteur)
```

## Conseils

- Pour ne pas se oublier de refermer une accolade ou un crochet, aligner les deux verticalement dans le code;
- S'aider de la structure pour naviguer entre les sous-programmation du document maître mais aussi pour vérifier que les \input{sous-programmation.tex} aboutissent bien aux sous-programmations souhaitées;
- Google est ton meilleur ami (vraiment), il y a plein de forums en tout genre (erreur, solution, nouvelles idées...);
- Ne pas désespérer si il y a une erreur insolvable, il y a toujours une solution;
- Programme pas forcément stable du coup enregistrer régulièrement;
- Ne pas oublier `\chapframe` au début de chaque chapitre du corps et réarranger le document à la fin de la rédaction;
- Etre sur de la structure de son tableau avant de le programmer et de l'échelle de son image avant de l'annoter;
- Utiliser `ctrl+f` pour naviguer au mot-clé dans le code et commenter à balle le code avec `%commentaire` pour que les autres puissent s'inspirer des fonctions appelées;
- Bien aérer son code en n'oubliant de mettre des `%` avant un retour à la ligne pour éviter que le code l'interprète comme un espace;
- Utiliser les raccourcis claviers, et deux écrans avec l'afficheur pdf en deuxième écran si possible;
- Filtrer les dossier pour n'afficher que les .tex, .bib et les images importées;
- Utiliser l'option `affichage -> source viewer` pour avoir un deuxième code à la place de l'afficheur et la colonne de navigation et ainsi jongler entre les sous-programmations;
- Bien s'assurer de l'orthographe avec le dictionnaire en préférences;
- Ne pas oublier les {} après certaines options de style de texte dans un paragraphe;
- Ne pas oublier `\hfill` pour placer deux objets sur le même alignement horizontal ou passer une première ligne dans certaines listes;
- `~` (ctrl+n) appelle un espace insécable, ça peut aider dans certains cas;
- Vérifier que les packages ne soient pas obsolètes ou remplacés;
- Vérifier qu'un package ne vienne pas en aide lors d'une programmation très compliquée;
- Bien lire les erreurs, elles donnent pas mal d'indices;
- S'aider de la grille de repère lors du codage d'une figure;
- Pour trouver une erreur, procéder par élimination de bloc de code.

**Affaire à suivre...**

## Erreurs fréquentes
    
- Packages qui se clashent entre eux => bonne chance pour les retrouver mais c'est l'erreur la plus fréquente;
- Accent ou espace dans les noms de fichier => facile à retrouver;
- Oubli de refermer les accolades ou parenthèse {} [] ; ... => les retrouver, celles qui se correspondent se surlignent quand on passe dessus, c'est pratique
- Usage de la virgule à la place du point et inversement => les retrouver également;
- Mauvaise appel de sous-programmation (nom du fichier ou arborescence...) => les retrouver, le log indique l'erreur;
- Ligne trop longue et compilation qui crashe => copier/coller sur une nouvelle programmation vierge après avoir segmenté la ligne en question avec des `%`;
- Compilation qui peuvent foirer la première fois => recompiler ou enregistrer, quitter et recopier.

**Affaire à suivre...**
