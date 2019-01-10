# Séance 1: Unix, Vim, Markdown et Git

## 1 - Établir une connexion SSH

Dans le cadre de ce cours, des comptes ont été créés pour chacun d'entre vous
sur le serveur Java (`java.labunix.uqam.ca`). Pour vous y connecter, vous devez
connaître votre identifiant MS (2 lettres suivies de 6 chiffres) ainsi que
votre NIP.

Familiarisez-vous avec les étapes de base pour établir une connexion SSH. Le
mécanisme sera différent selon que vous travaillez sous Windows, Mac OS ou
Linux. Il s'agit d'une partie très importante, car vos deux premiers travaux
pratiques devront minimalement fonctionner sur le serveur Java.

Parfois, certains comptes étudiants ne sont pas activés sur les serveurs, alors
envoyez-moi un courriel si c'est votre cas et le problème devrait être réglé
rapidement.

NOTE: Dans votre vie professionnelle vous serez confrontés à plusieurs environnnement
et votre propre laptop (pc, mac) restera surement à la maison.  Dans un environnnement
corporatif vous devez travailler avec les outils et standards de la firme. Linux est très
probablement celui avec lequel vous aurez à travailler.  Habituez-vous maintenant.

## 2a - Vim optionnel (seulement pour ceux qui veulent l'utiliser)

Complétez le tutoriel intégré de Vim. Pour cela, il suffit d'ouvrir un terminal
et de taper la commande

```shell
vimtutor
```

Puis suivez les instructions.

Ensuite, téléchargez le fichier `.vimrc` disponible dans le répertoire
`exemples` et placez-le dans le répertoire home. Il faut également installer le
greffon [Vim-plug](https://github.com/junegunn/vim-plug). Ces étapes sont un
peu longues, mais elle vous donneront une configuration minimale pour
travailler efficacement sous Vim pendant tout le cours.

## 2b - GNU nano (requis pour ceux qui n'utilisent pas Vim)

Voici quelques commandes pour configurer votre environnement de developpement.
Il est aussi possible de le configurer pour faire du Java.  Cet exemple est pour
le langage C. Mais regarder les fichiers disponibles pour les autres langages.

```shell
$ ls -lahs /usr/share/nano

$ cd ; cat /usr/share/nano/c.nanorc >> .nanorc

$ pwd
```


## 3 - Compilation d'un programme C

- Créez un programme C nommé `hello.c` qui affiche le traditionnel "Hello,
  world!" et sauvegardez-le. Vous pouvez simplement copier les lignes suivantes:

    ```c
    #include <stdio.h>

    int main(int argc, char *argv[]) {
        printf("Hello, world!\n");
        return 0;
    }
    ```

- Compilez le fichier en une seule étape

    ```shell
    gcc hello.c
    ```

et exécutez le fichier résultant en entrant `./a.out` pour vous assurer que
tout fonctionne.

## 4 - Markdown

Dans le même répertoire que le fichier `hello.c` que vous avez conçu à
l'exercice précédent, créez un fichier nommé `README.md` qui décrit brièvement
votre projet. Indiquez minimalement le titre du projet, l'auteur du projet et
une ou deux phrases qui décrivent ce qu'il fait, ainsi qu'une section qui
décrit tous les fichiers présents dans le répertoire. Profitez-en pour explorer
la syntaxe Markdown:

- Titres et sections;
- Paragraphes;
- Bouts de code;
- Italique et gras;
- Insertion d'une image;
- etc.

## 5 - Création d'un projet avec Git

- Rendez-vous tout d'abord sur le site de [GitLab](https://gitlab.com/) pour
  vous créer un compte. Prenez un nom d'utilisateur significatif (par exemple,
  le mien est `ablondin`), car il est probable que vous le réutiliserez plus
  tard dans un cadre autre que ce cours. Évitez les noms bizarres, comme
  `demoniacbrain` ou `lord-of-the-ring`, car il y a de bonnes chances pour que
  ce compte vous soit utile après le cours dans un contexte professionnel
  (évidemment, ce n'est qu'une suggestion !).

- Créez un nouveau dépôt, donnez-lui un nom significatif, laissez la
  description vide et les autres options par défaut puis confirmez la création.

- Maintenant, à l'aide de nano, ouvrez le fichier `~/.gitconfig` et entrez les
  lignes suivantes :

    ```ini
    [user]
        name = <votre nom>
        email = <votre courriel>
    [color]
        ui = auto
    [core]
        editor = nano  # ou vim
    ```

    (Lorsque vous deviendrez plus à l'aise avec Git, il est possible que vous
    ayez à modifier ce fichier à nouveau, mais ça devrait vous suffire pour la
    première partie du cours.)

    Notez que quand vous créez un nouveau dépôt dans GitLab ou GitHub, il vous
    est demandé de taper les commandes suivantes:

	```
	git config --global user.name "Nom Prénom"
	git config --global user.email "email@domaine.ext"
	```

    La commande `git config --global <clé> <valeur>` sert à modifier le fichier
    `~/.gitconfig`. Lors de la cŕeation de vos prochains dépôts, vous n'aurez
    pas besoin de taper ces commandes car votre configuration est déjà définie.

- Dans un terminal, rendez-vous dans le répertoire qui contient votre projet
  avec les fichiers `hello.c` et `README.md`. Entrez la commande

    ```shell
    git init
    ```

    qui initialise le projet.

- Ensuite, indiquez à Git que vous souhaitez versionner les deux fichiers
  décrits plus haut

    ```shell
    git add hello.c README.md
    ```

- Si vous tapez `git status`, vous devriez voir que les deux fichiers sont
  ajoutés, mais que d'autres fichiers (comme `a.out`) n'ont pas été ajoutés.
  **Ne les ajoutez pas**, car ils ne doivent pas être versionnés par Git.

- Toujours dans le répertoire courant, créez un fichier nommé `.gitignore` (le
  point initial est important) dans lequel vous insérez ce qui suit :

    ```shell
    a.out
    ```

- Ajoutez ce fichier également à l'aide de la commande `git add .gitignore`.

- Ensuite, entrez

    ```shell
    git commit
    ```

- Cela devrait ouvrir l'editeur pour que vous écriviez un message de commit. Écrivez
  quelque chose du genre

    ```shell
    Première version de mon programme Hello, world!
    ```

- Ensuite, il vous faut établir le lien entre votre dépôt local et celui sur
  GitLab. Pour cela, il suffit d'entrer la commande

    ```shell
    git remote add origin git@gitlab.com:<nom d'utilisateur>/<nom du projet>.git
    ```

    (Au début, je ne me rappelais jamais de la commande par coeur, alors je me
    rendais sur le site de GitLab et je cliquais sur le nouveau dépôt créé, qui
    indique les commandes à entrer dans une boîte sur la page d'accueil vers le
    bas.)

- Finalement, entrez la commande

    ```shell
    git push origin master
    ```

- Ceci devrait avoir pour effet de "pousser" vos modifications locales sur le
  dépôt à distance. Vous pouvez le visualiser dans un fureteur. En particulier,
  votre fichier `README.md` devrait apparaître sous forme HTML dans le bas de
  la page d'accueil du projet. Assurez-vous toujours de bien respecter le
  format Markdown pour que la génération du fichier HTML apparaisse
  correctement en visualisant l'ensemble du fichier.
