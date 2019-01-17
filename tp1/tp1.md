# Travail pratique 1

  L'objectif est de vous initier à la programmation avec le langage C, en  manipulant
  des données, des fichiers, ainsi que la gestion des arguments provenant de la ligne de commande.

  De plus, vos sources seront maintenues dans un gestionnaire de version/source de type git.
  
  Vous allez aussi vous familiariser avec `make` et le fichier `Makefile` afin `d'automatiser` plusieurs tâches utiles.

# Description du travail

  Le programme doit découvrir des `nombres parfaits`.  Un nombre est dit parfait lorsque la somme des tous ses diviseurs (excluant lui-même bien sûr) est égal à lui-même.

  Le programme `tp1` doit pouvoir être lancé en `ligne de commande` avec _minimalement_ les deux syntaxes suivantes :

*   ./tp1 -c CODE_permanent -i nom_du_fichier_en_entree.ext -o fichier_sortie.ext
*   ./tp1 -c CODE_permanent **<** nom_du_fichier_en_entree.ext **>** fichier_sortie.ext

  Avec la deuxième méthode, vous avez compris que le programme accepte les données par l'entrée standard `stdin` et produit le résultat dans la sortie standard `stdout`. Les symboles `<` et `>` sont des redirections.
 
*  -c `<CODE permanent>`
*  -i `<fichier source en entrée>`
*  -o `<fichier traité en sortie>`

  **Note**: il se pourrait que la sortie standard `stdout` soit utilisée avec `-i`.

#### Vous devez réaliser le travail selon les contraintes suivantes:

- Les `#include` standard sont tous permis. Tel que `#include <stdio.h>`;
- Vous ne pouvez pas utiliser des librairies `#include` d'un tiers;
- Seulement un `header` `#include "tp1.h"` de votre création est permis;
- En plus de sortir les résultats dans `stdout` ou un fichier de résultats, un fichier nommé `code.txt` doit être produit au moment de l'exécution de votre programme et contiendra uniquement votre `CODE PERMANNENT` qui est passé par l'argument `-c`;
- Les intervalles de découverte sont uniquement des entiers positifs.

# Exemple

### Un nombre parfait

Les diviseurs de 6 sont : { 1, 2, 3 }
~~~~
1 + 2 + 3 = 6 
~~~~

### Le fichier en entrée

Vous devez découvrir s'il existe des nombres parfaits entre 1 et 19
~~~~
1 19
~~~~

### Le fichier de résultats

Le contenu du fichier de résultats aura un résultat par ligne et sera similaire à celui-ci:
~~~~
6
~~~~


# Makefile

  Il est obligatoire d'inclure un fichier `Makefile` dans votre projet pour
  faciliter la compilation et la récupération des données. Celui-ci doit
  minimalement offrir les services suivants :

- Lorsqu'on entre simplement `make`, l'exécutable `tp1` doit être produit (ou mis à jour), 
  avec les arguments suivants (obligatoire) : `-Wall -pedantic -std=c99`;

- Lorsqu'on entre `make clean`, les fichiers `.o` et l'exécutable doivent être supprimés;

- Lorsqu'on entre `make data`, le téléchargement des données (fichier) se fait
  de façon automatique dans un répertoire (./data). La décompression est nécessaire.
  https://www.github.com/guyfrancoeur/INF3135_H2019/tp1/data.zip;

- Lorsqu'on entre `make test` le programme `tp1` s'exécutera séquentiellement avec les fichiers contenus dans `./data`.
  
- Lorsqu'on entre `make resultat` le fichier `resultat.txt` sera poussé dans votre dépôt.

# Complément

+ `-std=c99` indique au compilateur de traiter le code selon le standard C99 (et donc de rejeter certaines extensions comme celles de GNU par exemple)
+ `-pedantic` permet de signaler les avertissements, ou warnings, selon la norme ISO ; et
+ `-Wall` permet de signaler un grand nombre d’autres warnings décrit dans le man gcc.
En effet, la grande permissivité de C réduit l’aide du compilateur (sans option)
pour traquer certaines erreurs et les mauvaises pratiques de programmation.

---

# README.md

  En plus du code source nommé `tp1.c` et du fichier nommé `Makefile`, votre projet doit contenir
  un fichier nommé `README.md` qui décrit le contenu et qui **respecte le
  format Markdown**. Il doit minimalement contenir les informations ci-bas :

~~~~
   # Travail pratique 1

   ## Description

   <description du projet en quelques phrases>
   <mentionner le contexte (cours, sigle, université, etc.)>

   ## Auteur

   <prénom et nom> (<code permanent>)

   ## Fonctionnement

   <expliquez brièvement comment faire fonctionner votre projet, en inscrivant
   au moins deux exemples d'utilisation (commande lancée et résultat affiché)>

   ## Contenu du projet

   <décrivez brièvement chacun des fichiers contenus dans le projet (une phrase
   par fichier)>

   ## Références

   <citez vos sources ici>

   ## Statut

   <indiquez si le projet est complété ou s'il y a des bogues>
~~~~

# Contrainte

Le travail pratique 1 est à faire individuellement. Donc chacun doit faire initialiser
son dépôt GitHub, Bitbucket ou GitLab avec un système de gestion de version type Git.

# Remise

  La totalité de votre travail doit être remis au plus tard le **10 février
  2019** à **23h59**. À partir de minuit, une pénalité de **2 points par jour** de
  retard sera appliquée.

  La remise se fait **obligatoirement** par l'intermédiaire de la plateforme
  `Bitbucket https://bitbucket.org/`__ ou `Github https://github.com/`__ 
  ou `GitLab https://gitlab.com/`__ .
  **Aucune remise par courriel ne sera acceptée** (le travail sera considéré
  comme non remis).

  Le nom de votre dépôt doit être `inf3135-h2019-tp1` (en minuscules). Vous
  devez donner un accès en mode **lecture/écriture** (pas **admin**) à
  l'utilisateur `guyfrancoeur` (moi-même). Ceci me permettra de déposer directement
  dans vos projets votre note pour le travail ainsi que mes commentaires.

  Votre projet devrait minimalement contenir les fichiers suivants :

- Un fichier `tp1.c` contenant le code source de votre projet, ainsi que votre fonction `main`;
- Un fichier `README.md` avec le titre du projet, les auteurs, les exemples, etc;
- Un fichier nommé `Makefile` supportant les appels `make`, `make clean`, `make data`, `make test` et `make resultat`;
- Un fichier ``.gitignore``. Ça aide beaucoup.

  Les travaux seront corrigés sur le serveur Java. Vous devez donc vous assurer
  que votre programme fonctionne **sans modification** sur celui-ci.

# Barème de correction

| Critère | Sous-critère | Points |
| ------- |:------------ | ------:|
| Fonctionnabilité  | 5 à 10 tests seront lancés (comparaison binaire) | 6.0 |
| Compilation       | sans avertissement ni erreur                     | 1.0 |
| Git clone         | récupération (droit lecture, écriture)  | 1.0 |
| Qualité           | temps d'exécution (performance) et code | 2.0 |
| Directives        | création de code.txt                    | 0.5 |
| Makefile          | <ul><li>make</li><li>make clean</li><li>make data</li><li>make test</li><li>make resultat</li></ul> | <ul><li>1.0</li><li>0.5</li><li>1.0</li><li>0.5</li><li>0.5</li></ul> |
| Markdown          | README.md                               | 1.0 |
| **Total**         |                                         | 15 |
