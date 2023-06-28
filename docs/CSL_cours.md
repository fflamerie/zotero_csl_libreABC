
# Zotero : contribuez! Créer des styles bibliographiques CSL

## Objectifs

A la fin de cet atelier, vous aurez créé un style bibliographique simple, en apportant quelques modifications à un style existant.

Après un rappel concernant les styles bibliographiques et leur rôle dans la rédaction bibliographique, nous aborderons de façon détaillée la structure d'un style CSL. Nous passerons également en revue les outils et ressources utiles pour créer un style CSL.  	👉**30 minutes**

Au cours de la partie pratique de création d'un style, nous verrons les différents types de modification qui peuvent être apportés à un fichier de style CSL, du simple changement de la valeur d'un attribut à la création d'une commande de mise en forme conditionnelle. 👉**60 minutes**

## Sommaire

<!-- MDTOC maxdepth:1 firsth1:0 numbering:0 flatten:0 bullets:1 updateOnSave:0 -->

- [Objectifs](#objectifs)   
- [Sommaire](#sommaire)   
- [1-Introduction, rappels concernant Zotero](#1-introduction-rappels-concernant-zotero)   
- [2-Rappels concernant les styles](#2-rappels-concernant-les-styles)   
- [3-Structure d’un style CSL](#3-structure-d’un-style-csl)   
- [4-Ressources et outils pour la partie pratique](#4-ressources-et-outils-pour-la-partie-pratique)   
- [5-Installer un style créé avec l'éditeur de style Zotero](#5-installer-un-style-créé-avec-léditeur-de-style-zotero)   
- [6-Modifier une macro simple](#6-modifier-une-macro-simple)   
- [7-Focus sur les noms](#7-focus-sur-les-noms)   
- [8-Modifier une macro conditionnelle](#8-modifier-une-macro-conditionnelle)   
- [9-Focus sur les différents types de condition](#9-focus-sur-les-différents-types-de-condition)   
- [10-Les appels de citation et les notes](#10-les-appels-de-citation-et-les-notes)   
- [11-La bibliographie](#11-la-bibliographie)   
- [12-Miscellanées](#12-miscellanées)   

<!-- /MDTOC -->
<div style="page-break-after: always;"></div>

## 1-Introduction, rappels concernant Zotero

Pour davantage de détails concernant les rappels 1 à 4 (destinés principalement aux utilisateurs de Zotero), consultez le support de la formation Urfist Bordeaux [Gérer facilement sa bibliographie avec Zotero](https://github.com/fflamerie/zotero_gerer_biblio).

### Rappel 1, le répertoire `styles`
Où trouver les styles CSL dans Zotero ? Localisez le répertoire de données `Zotero`, puis le répertoire `styles`.

[Documentation Zotero : Le répertoire de données Zotero](https://docs.zotero-fr.org/zotero_data)

### Rappel 2, qualité des données
Tous les problèmes de mise en forme ne proviennent pas des styles bibliographiques, vérifiez la qualité et la complétude des données de votre bibliothèque Zotero en premier lieu !

### Rappel 3, bon usage des outils de rédaction bibliographique
Un usage inapproprié des outils de rédaction peut être une autre source d'anomalies dans les citations ou la bibliographie. Assurez-vous d'utiliser correctement les modules pour traitement de texte, s'agissant notament de l'insertion de préfixes, suffixes et localisateurs pour les citations.

[Documentation Zotero : Utiliser le module Zotero pour Word](https://docs.zotero-fr.org/word_processor_plugin_usage)

### Rappel 4, documentation Zotero

Les styles bibliographiques sont abordés dans les pages suivantes de la documentation **utilisateur**. Si vous ne les avez pas encore consultées, c'est le moment de le faire car pour la suite nous considérons comme acquise la connaissance de leur contenu.

* [Documentation Zotero : Préférences > Citer](https://docs.zotero-fr.org/preferences/cite)
* [Documentation Zotero : Utiliser le module Zotero pour Word](https://docs.zotero-fr.org/word_processor_plugin_usage)
* [Documentation Zotero : Les styles bibliographiques](https://docs.zotero-fr.org/styles)

Aujourd'hui nous nous concentrerons sur ce qui relève de la documentation **développeur**.

* [Documentation Zotero dev : Les styles bibliographiques (en anglais)](https://www.zotero.org/support/dev/citation_styles)
* [Documentation Zotero dev : Editer des styles CSL - Guide pas à pas (en anglais)](https://www.zotero.org/support/dev/citation_styles/style_editing_step-by-step)

Et commune aux 2, cette page de la base de connaissance : [Documentation Zotero : Les types de documents et les champs associés dans Zotero](https://docs.zotero-fr.org/kb/item_types_and_fields)

## 2-Rappels concernant les styles

Un style bibliographique définit la façon dont les éléments bibliographiques d’un document :

*   appels de citation,
*   **notes** si applicable,
*   **bibliographie**,

doivent être organisés et mis en forme.

On distingue différents types de style bibliographiques, correspondant à des formats de style Zotero différents. On trouve ainsi dans [le dépôt des styles Zotero](https://www.zotero.org/styles), plus de 10'000 styles regroupés en 2 grands ensembles.

*   Les styles _**in-text**_, dans lesquels un appel de citation dans le texte renvoie à une entrée de la bibliographie : on distingue principalement les styles **numériques** (ex: Vancouver) et **auteur-date** (ou Harvard).
*  Les styles _**note**_, dans lesquels un marqueur (symbole, nombre, etc.) pointe vers une note de bas de page ou de fin, qui permet d’identifier le document cité.

_Chaque type de style a sa logique propre, il peut être tentant de les mélanger, mais cela peut (souvent) aboutir à un résultat incohérent ou difficile à comprendre._

### Les styles  numériques

Dans le texte, chaque référence citée est appelée par un **numéro**.

>Yeast cells were grown at 25°C in batch cultures on 0.5% methanol for 36 hours <span style="color:#0000CD;">[21, 22]</span>.

Dans la bibliographie, les références sont classées par **ordre d’apparition dans le texte**.

><span style="color:#0000CD;">21\.</span> Zwart KB, Veenhuis M, Harder W (1983) Significance of yeast peroxisomes in the metabolism of choline and ethanolamine. Antonie Van Leeuwenhoek 49: 369-385.
>
><span style="color:#0000CD;">22\.</span> van der Klei IJ, Harder W, Veenhuis M (1991) Methanol metabolism in a peroxisome-deficient mutant of Hansenula polymorpha: a physiological study. Arch Microbiol 156: 15-23.

### Les styles  auteur-date

Dans le texte, chaque référence citée est appelée par  **le nom de l'auteur et la date de publication**.

> Yeast cells were grown at 25°C in batch cultures on 0.5% methanol for 36 hours <span style="color:#0000CD;">(van der Klei et al. 1991; Zwart et al. 1983)</span>
>
>Yeast cells were grown at 25°C in batch cultures on 0.5% methanol for 36 hours <span style="color:#0000CD;">(van der Klei et al.; Zwart et al.)</span></cite>

Dans la bibliographie, les références sont généralement classées par **ordre alphabétique d'auteur**, puis par date ; d'autres critères de tri peuvent intervenir.

>van der Klei IJ, Harder W, Veenhuis M (1991) Methanol metabolism in a peroxisome-deficient mutant of Hansenula polymorpha: a physiological study. Arch Microbiol 156: 15-23.
>
>Zwart KB, Veenhuis M, Harder W (1983) Significance of yeast peroxisomes in the metabolism of choline and ethanolamine. Antonie Van Leeuwenhoek 49: 369-385.

### Les styles _note_

Dans le texte, on ne trouve pas d'appels de citation mais des **appels de note**.

>"In the Island of St. Kilda, according to Martin, <span style="color:#0000CD;">[*]</span> the men do not acquire beards until the age of thirty or upwards, and even then the beards are very thin. “
>
><span style="color:#0000CD;">[*]</span>'Voyage to St. Kilda' (3rd edit. 1753), p. 37.

Dans la bibliographie, les références sont en général classées **par ordre alphabétique d'auteur**  ; d'autres critères de tri peuvent intervenir. Notez que certains styles _note_ omettent la bibliographie récapitulative de tous les documents cités.

Le format du marqueur de l'appel de note doit être paramétré dans le **traitement de texte**.

**Exemple dans Word 2010**

![marqueur_note_word](img/word_note.png)

### Clarté des consignes
Le plus difficile n'est pas forcément d'encoder le style, mais de disposer de consignes claires et précises, traduisibles dans un langage informatique.

_Deux exemples : les styles "Université de Lausanne - Histoire (Français)" et "Université de Bordeaux - École doctorale de droit (Français)", qui fournissent chacun une documentation détaillée, pour une utilisation avec ou sans logiciel de gestion bibliographique._

Grandjean, M., Rochat, T., & Chachereau, N. (2020). Lausanne : Style bibliographique et intégration à Zotero. https://lausannecitationstyle.github.io/support/

URFIST de Bordeaux. (2019). Citer des références juridiques : Guide et style Zotero de l’école doctorale Droit (Université de Bordeaux). http://weburfist.univ-bordeaux.fr/citer-des-references-juridiques-guide-et-style-zotero/

## 3-Structure d’un style CSL
### Structure générale d’un style CSL
Un style CSL est structuré en plusieurs éléments.

*   `style` : élément racine - précise notamment la version de CSL et le type de style ; permet des paramétrages globaux : gestion des noms à particules avec l'attribut `demote-non-dropping`, de l’indication du nombre de pages, abréviation des prénoms composés. [Spécification CSL : élément `style`](http://docs.citationstyles.org/en/stable/specification.html#the-root-element-cs-style)

*   `info` : métadonnées décrivant le style (nom, auteur, etc.) - il faut notamment modifier les éléments `title` et `id` du nouveau style que l'on crée à partir d'un autre, sinon le style créé sera écrasé lors des mises à jour du style duquel il est dérivé. [Spécification CSL : élément `info`](http://docs.citationstyles.org/en/stable/specification.html#info)

*   `citation` : décrit la façon dont les citations (dans le texte ou en note de bas de page) sont mises en forme. [Spécification CSL : élément `citation`](http://docs.citationstyles.org/en/stable/specification.html#citation)

*   `bibliography` : décrit la façon dont la bibliographie est mise en forme. [Spécification CSL : élément `bibliography`](http://docs.citationstyles.org/en/stable/specification.html#bibliography)

*   `locale` : permet de spécifier des termes, formats de date et options de mise en forme différents de ceux prévus par défaut pour une ou plusieurs langues données. [Spécification CSL : élément `locale`](http://docs.citationstyles.org/en/stable/specification.html#locale)

*   `terms` : permet la modification de chaînes de caractères spécifiques (ex. remplacer « edited by » par « ed. by »). [Spécification CSL : élément `terms`](http://docs.citationstyles.org/en/stable/specification.html#terms)

*   `macro` : permet la réutilisation des règles de mise en forme (notamment dans `citation` et `bibliography`) et des styles plus compacts. [Spécification CSL : élément `macro`](http://docs.citationstyles.org/en/stable/specification.html#macro)

Une `macro` CSL permet de définir des règles et d'attribuer à cet ensemble de règles un nom : appeler la macro en indiquant son nom exécutera la commande et appliquera les règles définies. On peut ainsi écrire une seule fois une longue séquence de paramétrage pour un élément donné, et y faire ensuite référence lorsque l'on souhaite l'appliquer.

Les `macro` économisent du code, et surtout facilitent la réutilisation et la modification des styles. Pour modifier la mise en forme des noms d'auteur par exemple, il suffit ainsi de modifier la `macro` correspondante, ou encore de copier-coller la `macro` d'un autre style.

L'utilisation des macro fait partie des bonnes pratiques recommandées par Sebastian Karcher (plus connu des utilisateurs de Zotero sous son pseudonyme "**adamsmith**").

>Bonne pratique 2 : Utilisez abondamment les macros. Gardez les éléments `citation` et `bibliography` brefs et ne leur intégrez qu'au minimum des éléments `choose`. [Traduction libre]

Karcher, S. (2013, octobre 28). Writing CSL - Features and Best Practices. The Zoteroist. https://zoteromusings.wordpress.com/2013/10/28/writing-csl-features-and-best-practices/

Retenons également la bonne pratique 3 recommandées dans ce billet, nous reviendrons sur la bonne pratique 1 un peu plus tard.

>Bonne pratique 3 : Utilisez des `terms` et des `labels`. N'ajoutez pas de termes ou d'expressions dans des affixes ou en utilisant `text value=`. [Traduction libre]

### Anatomie des éléments `style` et `info`

#### Type de style, l’attribut `class`

#### Style agnostique du point de vue de la langue vs. style localisé
On en parlera dans les _Miscellanées_ ; pour rendre agnostique du point de vue de la langue un style localisé, il suffit de supprimer l'attribut `default-locale`.

#### Style dépendant vs. style indépendant
Dans un souci d'économie, certains styles sont dépendants d'un autre style. Dans ce cas, le fichier CSL se réduit à un élément `info`. La référence au style principal est indiquée par l'attribut `rel="independent-parent"`.

Exemple du style [Loisir et Société / Society and Leisure](https://www.zotero.org/styles/loisir-et-societe-society-and-leisure)

```
<?xml version="1.0" encoding="utf-8"?>
<style xmlns="http://purl.org/net/xbiblio/csl" version="1.0" default-locale="en-US">
  <!-- Generated with https://github.com/citation-style-language/utilities/blob/master/generate_dependent_styles/data/taylor-and-francis -->
  <info>
    <title>Loisir et Société / Society and Leisure</title>
    <id>http://www.zotero.org/styles/loisir-et-societe-society-and-leisure</id>
    <link href="http://www.zotero.org/styles/loisir-et-societe-society-and-leisure" rel="self"/>
    <link href="http://www.zotero.org/styles/apa" rel="independent-parent"/>
    <link href="http://www.tandfonline.com/action/authorSubmission?journalCode=RLES20&amp;page=instructions" rel="documentation"/>
    <category citation-format="author-date"/>
    <category field="political_science"/>
    <issn>0705-3436</issn>
    <eissn>1705-0154</eissn>
    <updated>2014-05-17T16:39:46+00:00</updated>
    <rights license="http://creativecommons.org/licenses/by-sa/3.0/">This work is licensed under a Creative Commons Attribution-ShareAlike 3.0 License</rights>
  </info>
</style>
```

### Les principaux types d’éléments

On manipule dans les citations et la bibliographie des données de nature différente, auxquelles des paramétrages spécifiques peuvent être appliqués. A chaque type de donnée correspond ainsi un type d'élément CSL.

D'autres élements, `group` et `choose` par exemple, permettent de construire et structurer le code ; ils ne sont pas associés à un type de donnée bibliographique.

*   `text` : le texte à afficher peut être celui d’une `variable`, d’une `macro`, d’un `term` ou d’une `value`

*   `date` : date de publication, date de consultation, etc.

*   `names` : noms des auteurs, des éditeurs scientifiques, des éditeurs commerciaux, etc.

*   `number` : volume, numéro, numéro dans la série, etc.

*   `choose` : pour créer des conditions - voir _infra_ les différents types de condition

*   `label` : pour paramétrer l'affichage et la mise en forme de l'étiquette applicable aux variables `page` ou `locator` et aux variables de type nombre

*   `group` : pour paramétrer la ponctuation au niveau d’un groupe d’éléments plutôt qu’élément par élément ; cela évite de générer une ponctuation incohérente et peut permettre d'économiser du code en définissant.

C'est le moment de revenir sur les bonnes pratiques d'écriture recommandées par Sebastian Karcher, avec la bonne pratique 1.

>Bonne pratique 1 : Préférez les `group` et les `group delimiters` aux affixes pour la ponctuation et les espaces entre les objets. [Traduction libre]

Et rappelons la bonne pratique 3.

>Bonne pratique 3 : Utilisez des `terms`et des `labels`. N'ajoutez pas de termes ou d'expressions dans des affixes ou en utilisant `text value=`. [Traduction libre]

Karcher, S. (2013, octobre 28). Writing CSL - Features and Best Practices. The Zoteroist. https://zoteromusings.wordpress.com/2013/10/28/writing-csl-features-and-best-practices/


## 4-Ressources et outils pour la partie pratique

* Importez dans votre bibliothèque Zotero le [fichier form_CSL.rdf](https://raw.githubusercontent.com/fflamerie/zotero_csl_libreABC/main/docs/form_CSL.rdf)
* Installez le style [_Elsevier - Harvard (with titles)_](https://www.zotero.org/styles/elsevier-harvard).
* Téléchargez les [consignes du style Garni](https://github.com/fflamerie/zotero_csl_libreABC/blob/main/docs/CSL_consignes_garni.pdf).
* Téléchargez les [énoncés des exercices de style](https://github.com/fflamerie/zotero_csl_libreABC/blob/main/docs/CSL_exercices_style.pdf).

Le billet du blog Zotero francophone [Quel outil pour éditer des styles CSL?](https://zotero.hypotheses.org/758) détaille les différents outils disponibles pour l'édition de styles CSL.

L'éditeur visuel en ligne CSL est par ailleurs présenté dans le billet du blog Zotero francophone [Apporter de petites modifications à un style bibliographique](https://zotero.hypotheses.org/3746).

Aujourd'hui nous nous limitons à:

* l'éditeur de styles Zotero,
* l'outil de validation en ligne,
* l'outil de formatage en ligne.

### Les outils CSL intégrés à Zotero
Zotero possède un outil intégré pour éditer les styles, accessible depuis les _Préférences > Citer_.

![pref_styles_outils](img/pref_styles_outils.png)

Comme on le voit sur cette copie d'écran, Zotero dispose en fait de deux outils de style, l'_Aperçu des styles_ et l'_Editeur de style_.
Commençons par une brève présentation du premier.

![apercu](img/apercu_styles.png)

L'_Aperçu des styles_ vous permet de comparer rapidement tout ou partie des styles que vous avez installés, en générant des appels de citation et une bibliographie à partir de documents sélectionnés dans votre bibliothèque.

Afin que cet aperçu soit significatif et parlant, il importe de s'assurer de deux points.

Tout d'abord, assurez-vous que ces documents reflètent la **diversité de types de document** que vous allez citer (article, chapitre, mais aussi thèse ou encore brevet ou film ) : vous vérifierez ainsi que tous ces types sont bien pris en compte par les styles que vous comparez. Le style _Nature_, par exemple, ne sera pas le plus adapté si vous citez des documents non publiés comme les thèses. La revue _Nature_ demande aux auteurs de citer un nombre restreint de types de document (voir les [instructions aux auteurs](http://www.nature.com/nature/for-authors/formatting-guide), rubrique _References_), aussi le style CSL _Nature_ encode-t-il la mise en forme des citations uniquement pour ces types de document.

Ensuite, et surtout, assurez-vous que ces documents sont complets et exacts.

*  **S'il manque des informations bibliographiques**, il est logique que le style ne puisse pas les afficher lorsqu'il génère les citations et la bibliographie.
*  **Si vous faites un usage inadéquat ou détourné de certains champs**, vous générerez également une bibliographie détournée ou inadéquate, ne correspondant pas au résultat que produit le style normalement.

Ces deux points sont tout aussi importants lorsque vous utilisez l'_Editeur de style_.

Si l'_Aperçu des styles_ permet de manipuler plusieurs styles à des seules fins de visualisation, l'_Editeur de style_ se limite à l'affichage d'un seul style mais en vue de sa modification.

![editeur](img/editeur_style.png)

L'écran est composé de 3 zones, avec, de bas en haut :

* le panneau de **prévisualisation**, dans lequel vous voyez évoluer en temps réel la mise en forme des citations et de la bibliographie au fur et à mesure des modifications que vous apportez au code,
* le panneau d'**édition**,
* la barre d'outils.

Pourquoi recommandons-nous cet outil, qui semble rudimentaire et pourvu de fonctionnalités limitées?

#### Avantages de l'éditeur de styles Zotero
* Toute erreur de syntaxe XML donne lieu à un message d'erreur immédiat : le panneau de prévisualisation affiche le message suivant, aussi voit-on tout de suite que son fichier n’est pas bien formé.

```
Erreur dans la syntaxe du style :
Error: File is not valid XML
```

* On prévisualise en direct les modifications de paramétrage du style, et ce à partir des exemples de document de sa bibliothèque.
* On peut tester en direct les paramétrages liés à des situations de citation particulières : ainsi lorsque l'on précise un localisateur  (menu déroulant _Page_), ou que l'on omet le nom de l'auteur d'un appel de citation  dans un style de type auteur-date. Ou encore, dans un style de type _note_, lorsque l'on cite à plusieurs reprises la même référence (gestion des _ibid_, _op. cit._, etc. - menu déroulant _Position de la citation_).

![copie écran editeur_style_zotero_barre_outils](img/editeur_style_barre_outils.png)

#### Limites de l'éditeur de style Zotero
*   L'éditeur n'intègre pas d'aide à la saisie comme la **[coloration syntaxique](https://fr.wikipedia.org/wiki/Coloration_syntaxique)** ou **[l'indentation](https://fr.wikipedia.org/wiki/Style_d%27indentation)** du code.
*   Il ne contrôle pas la **validité** CSL : on peut créer un style dont la syntaxe XML est correcte, mais qui ne soit pas conforme aux spécifications CSL et qu'on ne pourra donc pas installer dans Zotero.
*   L'écran est partagé en 2 bandeaux horizontaux, ce qui peut occasionner une lisibilité réduite en fonction de la taille et de l'orientation de son écran.


### Les outils en ligne pour valider et formater son code
L'éditeur Zotero n'assure pas la **validation CSL**, indispensable pour installer et utiliser votre style, et bien sûr pour [le soumettre au dépôt CSL](https://github.com/citation-style-language/styles/blob/master/CONTRIBUTING.md) si son champ d'application dépasse un usage personnel ou local.

Le validateur en ligne [http://validator.citationstyles.org/](http://validator.citationstyles.org/) vérifie la validité CSL de votre fichier, et surtout affiche le cas échéant de façon détaillée les erreurs à corriger.


**Validateur en ligne : vue d'ensemble**

![valideur_1](img/csl_validate_error_1.png)

L'outil de formatage en ligne [https://formatter.citationstyles.org/](https://formatter.citationstyles.org/) apportera ensuite automatiquement diverses modifications à votre code, pour que votre fichier soit conforme aux standards du dépôt CSL (notamment indenter correctement votre code ou encore réordonner les éléments enfant de l'élément `info`). Cet outil contrôle également la validité de votre fichier, mais il s'arrête dès la première erreur rencontrée. Il est ainsi préférable de recourir d'abord au validateur, qui affichera lui **toutes** les erreurs de votre code.

## 5-Installer un style créé avec l'éditeur de style Zotero

Une fois votre nouveau style créé, il faut générer le fichier CSL correspondant et installer ce fichier dans Zotero.

### Etape 1. Rendre son style unique pour se prémunir de l'écrasement de son style
Chaque style est identifié dans l'élément `info` par :

*   un nom (élément `title`),
*   et surtout un identifiant (élément `id`).

Avant tout travail de modification d'un style existant, modifiez le contenu de ces éléments pour ne pas confondre votre nouveau style avec le style dont il est dérivé, et surtout pour éviter qu'il ne soit écrasé par une mise à jour de ce dernier.

```
<info>
  <title>Mon style</title>
    <id>http://www.zotero.org/styles/mon_style</id>
    <link href="http://www.zotero.org/styles/nature"/>
...
```

### Etape 2. Générer le fichier CSL
Le bouton _Enregistrer sous..._ de l'éditeur de style génère un fichier CSL, qu'il suffit d'enregistrer en veillant à bien spécifier l'extension **.csl** (et à ne pas laisser Windows ajouter une extension .txt).

**NB** : Vos modifications ne sont pas sauvegardées ni enregistrées tant que vous n'avez pas généré le fichier CSL.

### Etape 3. Installer le style dans Zotero

Pour installer votre nouveau style, cliquez sur le bouton _+_  du _Gestionnaire de styles_ pour afficher une fenêtre de navigation vous permettant de retrouver votre fichier et de l'ouvrir.

**NB** : Les styles ne sont pas synchronisés : si vous utilisez Zotero sur plusieurs ordinateurs, il vous faudra installer votre nouveau style sur tous ces ordinateurs.

## 6-Modifier une macro simple

### Exercice de style 1

✒️ _Pour cet exercice, vous travaillez en équipe avec un collègue :_

* _l'un est le conducteur et assure la saisie du code,_
* _l'autre est le navigateur et apporte au conducteur, aide, commentaires et suggestions._

Modifiez le style _Elsevier - Harvard (with titles)_ pour que les **auteurs** soient mis en forme selon les consignes du style Garni.

* Attention, il faut bien considérer à la fois les appels de citation **ET** la bibliographie.
* Attention, certains paramétrages par défaut sont **implicites** : si on souhaite les modifier il ne faut pas seulement modifier la valeur d'un attribut mais ajouter un nouvel attribut avec la valeur appropriée.

## 7-Focus sur les noms

### Spécifiques aux noms
Nous avons vu les attributs suivants dans notre exemple.

*   `sort-separator` : chaîne de caractères à afficher comme séparateur entre le nom et le prénom
*   `delimiter` : chaîne de caractères à afficher comme séparateur entre chaque nom d’auteur - si cet attribut  n’est pas présent, une virgule est utilisée comme séparateur
*   `and` : affichage du _et_ entre le pénultième et le dernier nom d’auteur - valeurs `symbol` ou `text`
*   `initialize-with` : remplace le prénom par une initiale et par le caractère  précisé comme valeur de l'attribut - si cet attribut  n’est pas présent, les prénoms sont restitués en entier
*   `delimiter-precedes-last` : paramétrage de l'affichage du séparateur avant le nom du dernier auteur - valeurs `contextual`, `after-inverted-name`, `always` ou `never` - lorsque le séparateur n'est pas affiché, une espace lui est substituée
*   `name-as-sort-order` : affichage du nom du ou des auteurs selon l’ordre nom-prénom - valeurs `all` ou `first`

L'élément `et-al` définit quant à lui le texte à afficher et la mise en forme à appliquer au _et al_. [Spécification CSL : élément `et-al`](http://docs.citationstyles.org/en/stable/specification.html#et-al)

### Non spécifiques aux noms mais utiles pour les noms (graisse, casse, etc.)
Les attributs suivants permettent de modifier facilement des caractéristiques telles que la casse ou la graisse.

*   `font-style="normal"`, `"italic"` ou `"oblique"`
*   `font-variant="normal"` ou `"small-caps"`
*   `font-weight="normal"`, `"bold"` ou `"light"`

### Modifier une partie du nom
Exemple : nom de famille en petites capitales et prénom en minuscules

```
<names variable="author">
      <name sort-separator=" " name-as-sort-order="all" et-al-min="4" et-al-use-first="3">
        <name-part name="family" font-variant="small-caps"/>
      </name>
      ...
```

### Définir un susbtitut au nom d'auteur
L'élément `substitute` définit le substitut au nom de l'auteur à utiliser lorsque le champ _Auteur_ de la notice Zotero est vide. Il doit faire référence à une `macro` ou à une `variable`, on ne peut pas utiliser un élément de type `text term` ou `text value`.

[Spécification CSL : élément `substitute`](http://docs.citationstyles.org/en/stable/specification.html#substitute)

Le style _Elsevier-Harvard (with titles)_ utilise :
* l'éditeur scientifique,
* à défaut le traducteur,
* à défaut le titre.

```
<macro name="author">
    <names variable="author">
      <name name-as-sort-order="all" sort-separator=", " initialize-with="." delimiter=", " delimiter-precedes-last="always"/>
      <label form="short" prefix=" (" suffix=")" text-case="capitalize-first"/>
      <substitute>
        <names variable="editor"/>
        <names variable="translator"/>
        <text macro="title"/>
      </substitute>
    </names>
  </macro>
```

## 8-Modifier une macro conditionnelle

### Exercice de style 2

✒️ _Pour cet exercice, vous travaillez en équipe avec un collègue :_

* _l'un est le conducteur et assure la saisie du code,_
* _l'autre est le navigateur et apporte au conducteur, aide, commentaires et suggestions._

_Si vous avez conservé la même équipe que pour l'exercice 1, vous inversez les rôles._

Modifiez le style _Elsevier - Harvard (with titles)_ pour que les **titres** soient mis en forme selon les consignes du style Garni.

La `macro name="title"` du style est un peu plus complexe que la `macro name="author"`, car elle définit une mise en forme conditionnelle en fonction du type de document. Les conditions sont exprimées dans l'élément `choose`.

*   `if` définit la 1ère condition : si le document est une thèse ou un rapport , le titre est affiché, suivi entre parenthèses du type de thèse ou de rapport et de son numéro.
*   `else-if` définit les autres conditions : si le document, par exemple, est une page web, le titre est affiché, suivi de : [WWW Document].
*   `else` définit ce qui s'applique dans tous les autres cas : si le document est d'un autre type que ceux indiqués dans les éléments `if` et `else-if`, le titre est affiché.

### Exercice de style 3

✒️ Modifiez le style _Elsevier - Harvard (with titles)_ pour que la mise en forme des volumes, numéros et pages pour les articles de revues corresponde aux consignes du style Garni.

## 9-Focus sur les différents types de condition
L'élément `choose` peut avoir pour parent un autre élément que `macro` : il peut être élément enfant de l'élément `layout` pour le **paramétrage des notes** par exemple.

Les différents types de condition sont exprimés par les attributs possibles pour les éléments `if` et `else-if`.

**/!\\** A l'exception de l'attribut `desambiguate`, tous les attributs peuvent être **multi-valués**. Les différentes valeurs sont séparées par des espaces.

*   `desambiguate="true"` (seule valeur possible de l’attribut) : la condition n’est réalisée que si elle permet de désambiguïser
*   `is-numeric="XXX YYY ZZZ"` valeur de l’attribut = variable qui doit avoir un contenu numérique pour que la condition se réalise
*   `is-uncertain-date="XXX YYY ZZZ"` valeur de l’attribut = date qui doit être incertaine pour que la condition se réalise [NB Zotero ne gère pas les dates incertaines]
*   `locator="XXX YYY ZZZ"` valeur de l’attribut = localisateur auquel la condition s’applique
*   `position="XXX YYY ZZZ"` cf. _infra_, utilisée pour les notes de bas de page ou de fin
*   `type="XXX YYY ZZZ"` valeur de l’attribut = type de document auquel la condition s’applique
*   `variable="XXX YYY ZZZ"` valeur de l’attribut = variable dont l’absence ou la présence conditionne la réalisation de la condition

L'attribut `match` définit l'opérateur à utiliser.

*   `match="any"` = OU = la condition se réalise si au moins un des critères est rempli

ex : `<if type="book thesis" match="any">` la condition se réalise si le document est de type livre OU thèse

*   `match="all"` = ET = la condition se réalise si TOUS les critères sont remplis
*   `match="none"`= NON = la condition se réalise si AUCUN des critères n’est rempli

ex : `<if variable="volume" match="none">` la condition se réalise si la variable volume est absente, _i. e_. si le champ _Volume_ de la  notice Zotero est vide.

[Spécification CSL : élément `choose`](http://docs.citationstyles.org/en/stable/specification.html#choose)

## 10-Les appels de citation et les notes

### Structure de l'élément `citation`
L'élément `citation` permet de paramétrer les appels de citation pour les styles _**in-text**_ et les notes (de bas de page ou de fin) pour les styles **_note_**. Il comporte deux éléments.

*   `sort` : définit les critères de tri des citations multiples,
*   `layout` : spécifie les informations à inclure (et leur mise en forme si elle n'a pas été définie dans des `macro`).

Les attributs et les possibilités de mise en forme diffèrent en fonction du type de style.

Le paramétrage pour les styles **numériques** demeurant simple et sommaire, nous nous concentrons sur les spécificités des styles auteur-date et note.

```
<citation nom_attribut="valeur_à_appliquer"/>
  <sort>
    <key variable="variable_critère_de_tri_pour_les_citations_multiples"/>
    <key macro="résultat_de_la_macro_critère_de_tri_pour_les_citations_multiples" sort="ascending" ou "descending"/>
  </sort>
  <layout >
    <text variable="variable_à_afficher"/>
    <text macro="résultat_de_la_macro_à_afficher"/>
  </layout>
</citation>
```

### Exercice de style 4

✒️ Comment les appels de citation sont-ils mis en forme dans ce style ?

```
<citation collapse="citation-number">
    <sort>
      <key variable="citation-number"/>
    </sort>
    <layout vertical-align="sup" delimiter=",">
      <text variable="citation-number"/>
    </layout>
  </citation>
```

### Styles auteur-date
#### Désambiguïser
Dans les styles auteur-date, l'élément `citation` doit comporter des règle de désambiguïsation des citations, afin de distinguer des documents ayant les mêmes auteurs et la même date de publication. CSL envisage cette désambiguïsation selon 3 étapes, exprimées par des attributs de l'élément `citation`.

Présentons en bref les 3 étapes détaillées dans [Spécification CSL : Disambiguation](http://docs.citationstyles.org/en/stable/specification.html#disambiguation)

##### Etape 1
`disambiguate-add-names` : par l’ajout d’un nom, sans tenir compte du paramétrage du `et-al`

##### Etape 2
`disambiguate-add-givenname` : par l’ajout d’un prénom, par ex. J. Doe, 2005 et M. Doe, 2005

`givenname-disambiguate-rule` : traitement des prénoms (tous les prénoms, initiales, etc.)

##### Etape 3
`disambiguate-add-year-suffix` : par l’ajout d’un suffixe à l’année, par ex. : 2007a, 2007b etc.


#### Grouper
Il s'agit de regrouper les citations multiples par auteur. Ce regroupement est activé par l'attribut `cite-group-delimiter`. Ainsi (Doe 1999; Smith 2002; Doe 2006; Doe et al. 2007) devient (Doe 1999; Doe 2006; Smith 2002; Doe et al. 2007).

[Spécification CSL  : Cite Grouping ](http://docs.citationstyles.org/en/stable/specification.html#cite-grouping)

#### Compacter
Il s'agit non seulement de regrouper, mais plus encore de compacter les citations multiples. L'attribut `collapse` active le regroupement et le compactage et peut avoir les valeurs suivantes.

*  `"citation-number"` : compacte les numéros de citation (styles numériques).
*   `"year"` : compacte les citations d’un même auteur aux dates, par ex. :  (Doe 2000, Doe 2001) devient (Doe 2000, 2001).
*   `"year-suffix"` : idem que le précédent, mais compacte aussi des années identiques, par ex. : (Doe 2000a, Doe 2000b) devient (Doe 2000a, b).
*   `"year-suffix-ranged"` : idem que le précédent, mais compacte aussi les suffixes, par ex. : (Doe 2000a, b, c, e) devient (Doe 2000a-c, e).

[Spécification CSL : Cite Collapsing](http://docs.citationstyles.org/en/stable/specification.html#cite-collapsing)

#### Paramétrer le `et-al`
Plusieurs attributs de l'élément `citation` permettent de définir les paramètres d'affichage du `et-al`.

*   `et-al-min` : nombre d’auteurs minimum pour afficher la mention `et-al`
*   `et-al-use-first` : nombre d’auteurs à inclure avant `et-al`
*   `et-al-subsequent-min`  et `et-al-subsequent-use-first` : idem que les précédents, pour les références déjà citées
*   `et-al-use-last` : remplace `et-al` par « … » et le nom du dernier auteur
*   `delimiter-precedes-et-al` : paramétrage de l'affichage du `delimiter`avant la mention `et-al`  - valeurs `contextual`, `after-inverted-name`, `always` ou `never` - lorsque le séparateur n'est pas affiché, une espace lui est substituée

### Exercice de style 5
✒️Modifiez le style _Elsevier - Harvard (with titles)_ pour que la mise en forme des appels de citation corresponde aux consignes du style Garni.

### Styles note
Pourquoi l'élément `citation` est-il plus complexe dans les style **_note_**?

D'une part, les citations affichent davantage de composants (titre, éditeur, etc.) pour constituer une référence bibliographique abrégée.

D'autre part, les éléments à afficher peuvent différer en fonction de la **position** relative de la référence citée, et de la présence ou non d'un  localisateur.

#### Ibid, op. cit., etc.
On retrouve ici l'élément `choose` et la définition de conditions.

C'est en effet l’attribut `position` d’un élément `if` ou `else-if` qui détermine le contenu à afficher en fonction de la position de la citation par rapport à des occurrences précédentes.

Il peut avoir différentes valeurs.

*   `first` : première occurrence de la référence citée,
*   `ibid`, `ibid-with-locator`, `subsequent` : une référence citée précédemment a la position `subsequent`. Elle peut aussi avoir la position `ibid` ou `ibid-with-locator` si les deux occurrences sont contiguës. C'est le cas si l'une des deux conditions suivantes est satisfaite.

1.  La référence citée est la même que celle qui la précède immédiatement dans la même note.
2.  La référence citée est la première de la note, et elle est la même que celle de la note précédente, qui est une citation unique.

C'est alors la présence d'un localisateur qui détermine la position attribuée.

##### La citation précédente n'inclut pas de localisateur.

Si la citation comporte un localisateur, la position est `ibid-with-locator`.

Si elle n'en comporte pas, la position est `ibid`.

##### La citation précédente inclut un localisateur.

Si la citation comporte le même localisateur, la position est `ibid`.

Si la citation comporte un localisateur différent, la position est `ibid-with-locator`.

Si elle ne comporte pas de localisateur, la position est seulement `subsequent`.

*   `near-note` : position d'une citation `subsequent` distante d'un nombre _n_ de notes de sa première occurrence. L’attribut `near-note-distance` permet en effet de paramétrer la distance maximale entre les 2 notes. Ainsi, une citation très éloignée de sa première occurrence pourra être restituée sous la forme d'une version plus détaillée de la référence bibliographique.

#### Exemple de style note
Style [Presses Universitaires de Rennes (Français)](https://www.zotero.org/styles/presses-universitaires-de-rennes)

```
<citation>
    <layout suffix="." delimiter="&#160;; ">
      <choose>
        <if position="ibid-with-locator">
          <group delimiter=", ">
            <text term="ibid" text-case="capitalize-first" font-style="italic" suffix="."/>
            <text macro="point-locator"/>
          </group>
        </if>
        <else-if position="ibid">
          <text term="ibid" text-case="capitalize-first" font-style="italic"/>
        </else-if>
        <else-if position="subsequent">
          <group delimiter=", ">
            <text macro="author"/>
            <choose>
              <if type="bill book graphic legal_case motion_picture report song thesis" match="any">
                <text variable="title" form="short" font-style="italic"/>
              </if>
              <else>
                <text variable="title" text-case="capitalize-first" form="short" quotes="true" font-style="normal"/>
              </else>
            </choose>
            <text term="cited" font-style="italic" suffix="."/>
            <text macro="point-locator"/>
          </group>
        </else-if>
        <else>
          <group delimiter=", ">
            <text macro="author"/>
            <text macro="title"/>
            <text macro="translator"/>
            <text macro="edition"/>
            <text macro="pub-place"/>
            <text macro="publisher"/>
            <text macro="collection"/>
            <text macro="yearpage"/>
          </group>
        </else>
      </choose>
    </layout>
  </citation>
```

## 11-La bibliographie

### Structure de l'élément `bibliography`

Comme l'élément `citation`, l'élément `bibliography`a pour élément enfant les 2 éléments suivants :

*   `sort` : définit les critères de tri des références dans la bibliographie,
*   `layout` : spécifie les informations à inclure (et leur mise en forme si elle n'a pas été définie dans des `macro`).

Si certaines options (et donc certains attributs) sont les mêmes que pour `citation` (nombre d’auteurs pour l’affichage de `et-al`), d'autres sont spécifiques (marges et saut de ligne, mise en forme des noms d’auteur déjà cités).

### Exercice de style 6
✒️ Voici l'élément `bibliography` du style _Elsevier-Harvard (with titles)_.

* Pouvez-vous comprendre le paramétrage défini par chacun des 3 attributs de `bibliography`?
* Quels sont les critères de tri des références dans la bibliographie?
* Quel est le dernier caractère affiché dans une référence bibliographique? Est-il toujours identique? Pourquoi?

```
<bibliography hanging-indent="true" entry-spacing="0" line-spacing="1">
    <sort>
      <key macro="author"/>
      <key macro="issued" sort="descending"/>
    </sort>
    <layout>
      <group suffix=".">
        <text macro="author" suffix=","/>
        <text macro="issued" prefix=" "/>
        <group prefix=". ">
          <text macro="title"/>
          <text macro="container"/>
          <text macro="locators"/>
        </group>
      </group>
      <text macro="access" prefix=". "/>
    </layout>
  </bibliography>
```

### Paramètres spécifiques
#### Gestion du `et-al`
On retrouve les mêmes attributs que pour l'élément `citation`.

*   `et-al-min` : nombre d’auteurs minimum pour afficher la mention `et-al`
*   `et-al-use-first` : nombre d’auteurs à inclure avant `et-al`
*   `et-al-subsequent-min`  et `et-al-subsequent-use-first`: idem que les précédents, pour les références déjà citées
*   `et-al-use-last` : remplace `et-al` par « … » et le nom du dernier auteur
*   `delimiter-precedes-et-al` : paramétrage de l'affichage du séparateur  avant la mention `et-al`- valeurs `contextual`, `after-inverted-name`, `always` ou `never` - lorsque le séparateur n'est pas affiché, une espace lui est substituée

#### Espacements
Les attributs suivants sont applicables uniquement à l'élément `bibliography` et non à l'élément `citation`.

*   `hanging-indent` : retrait  par rapport à la marge
*   `second-field-align` : `flush` ou `margin`  (`margin` : permet de placer les numéros de citation dans la marge)
*   `entry-spacing` : espacement entre chaque entrée de la bibliographie, exprimée en nombre d'interlignes
*  `line-spacing` : valeur de l'interligne dans la bibliographie

[Spécification CSL : Whitespace](http://docs.citationstyles.org/en/stable/specification.html#whitespace)

#### Grouper par nom d'auteur
Il s'agit, lorsque des références adjacentes ont le(s) même(s) auteur(s), de remplacer les occurrences suivantes de ce(s) nom(s) par un substitut, défini par la valeur de l'attribut `subsequent-author-substitute`.

L'attribut `subsequent-author-substitute-rule` paramètre les règles de substitution qui s'appliquent.

[Spécification CSL : Reference Grouping](http://docs.citationstyles.org/en/stable/specification.html#reference-grouping)

### Créer une bibliographie par type de document
#### Créer une `macro`
On va assigner à chaque type de document (ou groupe de types de document) un numéro, correspondant à son numéro d'ordre d'apparition dans la bibliographie.

Dans l'exemple suivant, les livres et chapitres de livre seront tous cités en premier, puis les articles de revues, puis tous les autres types de documents.

```
<macro name="sort-key">
  <choose>
    <if type="book bookSection" match="any">
      <text value="1"/>
    </if>
    <else-if type="article-journal" match="any">
      <text value="2"/>
    </else-if>
    <else>
      <text value="3"/>
    </else>
  </choose>
</macro>`
```

#### Référencer cette `macro` dans l'élément `bibliography`
Dans l'exemple suivant, dans la bibliographie :

*   les références sont regroupées par type de document;
*   à l’intérieur de chaque regroupement, elles sont classées par auteur, puis par date, puis par titre.

```
<bibliography et-al-min="11" et-al-use-first="10">
  <sort>
    <key macro="sort-key"/>
    <key macro="author"/>
    <key macro="issued"/>
    <key variable="title"/>
  </sort>`
```

## 12-Miscellanées
### Date originale
La date originale d’un document est exprimée par une  variable de type `date`, `original-date.`

Ex :

```
<date variable="original-date"/>`
  <date-part name="year"/>
</date>
```

La date originale doit être saisie dans le champ _Extra_ de la notice Zotero, sous la forme : `original-date: 1876`.

#### Exercice de style date originale

✒️Modifiez le style _Elsevier Harvard (with titles)_ pour afficher la date originale selon les consignes du style Garni.

### Langues
Certains styles sont agnostiques du point de vue de la langue, d'autres sont "localisés".

Dans un cas comme dans l'autre, ils utilisent par défaut des traductions communes pour les termes bibliographiques, encodées dans les fichiers `locale`. Exemple : [Fichier locale fr-FR](https://github.com/citation-style-language/locales/blob/master/locales-fr-FR.xml)

Dans un cas comme dans l'autre, si les traductions par défaut ne correspondent pas aux consignes du style, il est possible de recourir à des termes autres, en les encodant dans un élément `locale` du fichier CSL (voir _supra_ exemple de l'abréviation de numéro pour le style Garni).

Dans un cas comme dans l'autre, limiter au maximum le recours à des `text value=" "` pour définir des chaînes de caractère et aux affixes pour paramétrer la ponctuation assure que son style soit le plus **réutilisable** possible.

#### Styles génériques
Les styles agnostiques du point de vue de la langue ne comportent pas d'attribut `default-locale`. Ils peuvent être utilisés dans toutes les langues.

#### Styles localisés
Comme nous l'avons vu, la localisation est encodée dans l'élément `style`, par l'attribut `default-locale`.

```
<style xmlns="http://purl.org/net/xbiblio/csl" class="in-text" version="1.0" demote-non-dropping-particle="never" default-locale="en-US">
```

Les styles non localisés en `en-` comporte en clair dans leur intitulé la langue dans laquelle ils sont utilisables.

Dans l'entrepôt des styles Zotero on peut retrouver les styles localisés dans une langue en indiquant le nom de la langue dans le formulaire de recherche : _français_ affichera ainsi tous les styles ayant un attribut `default-locale="fr-XX"`.

##### Dans quel cas localiser un style?
Limiter l'utilisation d'un style à une langue déterminée permet d'éviter les erreurs de la part des utilisateurs : quelle que soit la langue par défaut de l'utilisateur, ce dernier ne pourra pas rédiger les éléments bibliographiques dans une autre langue que celle prévue par le style bibliographique. Une revue publiant des articles dans une unique langue se prémunira ainsi des erreurs de langue en localisant son style bibliographique.

### Rechercher un style à partir de caractéristiques précises
[L'entrepôt des styles Zotero](https://www.zotero.org/styles) vous permet de naviguer dans les styles existants par des facettes portant sur :

* le type de style (numérique, auteur-date, etc.),
* le champ disciplinaire.

La case _Show only unique styles_ vous permet d'afficher uniquement les styles non dépendants. Si vous souhaitez utiliser un fichier de code existant pour l'adapter, cocher cette case vous évitera d'afficher inutilement les styles dépendants, qui se résument à une référence au style duquel ils sont dérivés et sont donc d'un intérêt relatif pour l'activité d'édition de style.

Vous pouvez également interroger l'entrepôt en saisissant des termes de recherche, mais cette recherche porte uniquement sur l'intitulé du style, qui ne rend pas compte de toutes ses caractéristiques.

#### Comment procéder si vous souhaitez retrouver tous les styles qui utilisent la mention _Ibid._?

Il suffit pour ce faire de lancer une recherche dans l'entrepôt [CSL officiel sur GitHub](https://github.com/citation-style-language/styles).

![github_recherche_styles](img/github_recherche_styles.png)
