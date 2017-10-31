<!-- .slide: data-background-image="images/git-logo.png" data-background-size="800px" class="chapter" -->
## 1
### Opérations de base


===


<!-- .slide: class="slide" -->
### Cloner le code depuis le dépôt distant

```bash
git clone git@github.com:romain-warnan/git-au-quotidien.git
cd git-au-quotidien
```

Différence majeure par rapport à SVN
 - le dépôt entier est cloné : y compris l’historique
  - répertoire `.git/`
  - `git log`
 - dépôt local ≠ dépôt distant


===


<!-- .slide: class="slide" -->
### Ignorer des fichiers

Fichier `.gitignore`
 - à la racine du dépôt local
 - nom important

Exemple :
```
target/
.settings/

*.log

.classpath
.project
.*-credentials
```

Ignorer de nouveaux fichiers :
```bash
echo "*.class" >> .gitignore
git commit -am "Ignorer les fichiers .class"
```


===


<!-- .slide: class="slide" -->
### Modifier des fichiers

```bash
git add '*.java'
```
 - souvent on utilise plus simplement `git add .`

Voir l’état de la copie locale :
```bash
git status
```

<div class="center">
    <img src="images/git-status.png" />
</div>


===


<!-- .slide: class="slide" -->
### Commiter des fichiers

```bash
git commit -m "Message de commit."
```
 - tout ce qui est dans l’index est commité.

Si on souhaite commiter tous les fichiers modifiés : 
```bash
git commit -am "Message de commit."
```
 - ne commite pas les nouveaux fichiers
  - utiliser `add` explicitement dans ce cas

Pour un message de commit plus complet, utiliser l’éditeur de texte :
```bash
git commit
```
 - rappel pour quitter vi : __Esc__ puis « :wq », ou __Esc__ puis __Maj + zz__

__Attention__ : le travail est commité dans le dépôt local.