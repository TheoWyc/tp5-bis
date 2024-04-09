## TP1
# 1. Configuration de GIT (mettre la liste après la config mais avant les get)
>git config –list

diff.astextplain.textconv=astextplain
<br>
filter.lfs.clean=git-lfs clean -- %f
<br>
filter.lfs.smudge=git-lfs smudge -- %f
<br>
filter.lfs.process=git-lfs filter-process
<br>
filter.lfs.required=true
http.sslbackend=schannel
<br>
...

>git config –global user.name “Théo Wychowski”
>git config –global user.email wychowski.theo@gmail.com
>git config --global core.editor vsCode

>git config user.name
Théo Wychowski
>git config user.email
wychowski.theo@gmail.com
>git config core.editor
vsCode


# 2. Création d’un dépôt GIT sur une machine locale

J’ai été dans un répertoire que j’ai créé pour la SAE et j’ai fait les commandes :
>mkdir courseGIT
>cd courseGIT
>mkdir tp1

Et dans le répertoire tp1, la commande [color=#fa9a00]pwd[color=#fa9a00] me donne ce chemin :

>/c/Users/wtwhy/OneDrive/Bureau/ds/IUT/TP/s2/sae2.03_Installation_de_services_résseau/courseGIT/tp1

Dans ce répertoire j’ai fait la commande 
>git init


Cela à créé un nouveau répertoire caché .git qu’on peut voir avec la commande 
>ls -a
>./ ../ .git/


La commande **git** status affiche

Car on n’a pas encore changé quelque chose dans le répertoire tp1.

# 3. Création d’un fichier README.md

Pour crée le fichier on fait la commande touch README.md

Dans le fichier on met nom, prénom, etc... (voir le début du fichier)

Après avoir enregistrer le fichier, la commande git status affiche :
$:>git status
On branch master

No commits yet

Untracked files:
  (use "git add <file>..." to include in what will be committed)
        README.md

nothing added to commit but untracked files present (use "git add" to track)

Il y a "Untracked files" pour dire que git ne suit pas ce fichier, pour cela il faut donc faite git add README.md
La commande git status affiche maintenant :
$:>git status
On branch master

No commits yet

Changes to be committed:
  (use "git rm --cached <file>..." to unstage)
        new file:   README.md


Pour valider l'inclusion du fichier, on fait la commande :
$:> git commit -m "Ajoute du fichier README.md"
[master (root-commit) 00a6ae9] Ajoute du fichier README.md
 1 file changed, 85 insertions(+)
 create mode 100644 README.md

Maintenant qu'on a enregistré une première version du fichier, la commande git status affiche maintenant :
$:>git status
On branch master
nothing to commit, working tree clean


Étapes pour suivre un fichier dans Git :
1) Modification d’un fichier existant ou création d’un nouveau fichier.
2) git status pour voir les fichiers à inclure dans le dépôt git.
3) git add <fichier> pour sélectionner le fichier (stage) que nous voulons suivre dans le dépôt git.
4) git commit -m "Ajoutez ici un petit commentaire pour décrire ce commit" pour valider/enregistrer les changements dans le dépôt git.
5) Enfin, la commande git log nous permet de voir toutes les différentes versions enregistrées dans notre dépôt. Tapez git log pour voir le
   Journal des différentes versions. Chaque entrée du log correspond à une version différente du fichier validée (commit).


# 4. Gestion de version d’un programme Java*
On crée un dossier qui contiendra les sources du projet avec mkdir src.
Dans ce dossier, on crée le programme avec la commande touch Cryptomonnaie.java.

Dans le programme on met le code : 
public class Cryptomonnaie{
    private String nom;
    private double valeurDeJeton; // Imaginons en euros

    public Cryptomonnaie(String nom, double valeurDeJeton){
        this.nom = nom;
        this.valeurDeJeton = valeurDeJeton;
    }
}


Pour ajouter et valider ce fichier, il faut se rendre dans le répertoire tp1 puis faire la commande :
>git add src 
Pour suivre le répertoire qui contient le fichier, puis la commande :
>git commit -m "Première version du fichier Cyptomonnaie.java"
Pour valider les changements.

On peut voir que git status met :
$ git status
On branch master
nothing to commit, working tree clean

La commande git log affiche :
Author: Théo <wychowski.theo@gmail.com>
Date:   Sun Apr 7 16:46:16 2024 +0200

    Première version du fichier Cyptomonnaie.java

commit 00a6ae9bab65951cb90c64e1b83e32fc50e78047
Author: Théo <wychowski.theo@gmail.com>
Date:   Sun Apr 7 16:13:04 2024 +0200

    Ajoute du fichier README.md

On compile le fichier Cryptomonnaie.java (javac Cryptomonnaie.java)

Donc git status affiche :
On branch master
Untracked files:
  (use "git add <file>..." to include in what will be committed)
        Cryptomonnaie.class

nothing added to commit but untracked files present (use "git add" to track)

Il n’est pas nécessaire d’ajouter dans git les fichier .class car si on n’a déjà le fichier java, cela fait des informations redondantes et ce sont des fichier non modifiable.
Pour ne plus qu’il apparaissent dans la commande git status, il faut aller dans le fichier tp1 et créé le fichier .gitignore
>touch .gitignore

Dans ce fichier, on met tous les fichiers que git doit ignore, ici on met :
*.class

(puis pour l’exercice :)
Compiled class file
*.class

Package Files 
*.jar
*.war
*.nar
*.ear
*.zip
*.tar.gz
*.rar


On sélectionne et valide le fichier avec :
git add .gitignore
git commit -m “Ajout du fichier gitignore pour ignorer les fichiers .class”

Maintenant, quand on fait la commande git status :
On branch master
nothing to commit, working tree clean

