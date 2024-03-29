<!-- .slide: data-background-image="images/logo-git.png" data-background-size="600px" class="chapter" -->
## 10
### Rebasage


%%%


<!-- .slide: data-background-image="images/logo-git.png" data-background-size="600px" class="slide" -->
### Rebaser

**Rebasage** : autre manière d’intégrer une branche dans une autre
 - `git rebase`
 - alternative à la fusion

Les modifications apportées dans une branche sont rejouées dans la branche de destination
 - équivalent à appliquer des *patchs*
  - calculés dans une branche
  - appliqués dans une autre


%%%


<!-- .slide: class="slide" data-background-color="#7580ba" data-transition="slide-in fade-out" -->
### Schéma : situation initiale

```bash
#
git checkout master
```

<div class="fixed-height center">
	<img src="images/basic-rebase-1.png" width="700px" />
</div>


%%%


<!-- .slide: class="slide" data-background-color="#7580ba" data-transition="fade" -->
### Schéma : fusion à trois sources

```bash
#
git merge experiment
```

<div class="fixed-height center">
	<img src="images/basic-rebase-2.png" width="700px" />
</div>


%%%


<!-- .slide: class="slide" data-background-color="#7580ba" data-transition="fade" -->
### Schéma : situation initiale

```bash
#
git checkout experiment
```

<div class="fixed-height center">
	<img src="images/basic-rebase-1.png" width="700px" />
</div>


%%%


<!-- .slide: class="slide" data-background-color="#7580ba" data-transition="fade" -->
### Schéma : rebasage

```bash
#
git rebase master
```

<div class="fixed-height center">
	<img src="images/basic-rebase-3.png" width="700px" />
</div>


%%%


<!-- .slide: class="slide" data-background-color="#7580ba" data-transition="fade-in slide-out" -->
### Schéma : fusion en avance rapide

```bash
git checkout master
git merge experiment
```

<div class="fixed-height center">
	<img src="images/basic-rebase-4.png" width="700px" />
</div>


%%%


<!-- .slide: data-background-image="images/logo-git.png" data-background-size="600px" class="slide" -->
### Conséquences du rebasage

L’historique devient linéaire
 - il ne correspond plus à ce qui s’est *réellement* passé
 - les *commits* de la branche sont réécrits

Il n’y a pas de *commit* de fusion
 - puisque l’historique est linéaire

<!-- .element: class="icon warn" -->Il faut éviter de rebaser du code déjà poussé dans le dépôt distant
 - en cas de réécriture de l’historique, `git push --force`
  - ou mieux, `git push --force-with-lease`
  - si le dépôt distant le permet
  - se synchroniser si nécessaire avec les collègues : `git pull --rebase`
 - le rebasage se fait dans la copie de travail
  - avant d’avoir partagé ses modifications

Exemple : contribution à un projet libre
 - *pull request*
 - fusion en avance rapide uniquement
 - analyse du code plus simple grâce à l’historique linéaire

%%%

<!-- .slide: data-background-image="images/logo-git.png" data-background-size="600px" class="slide" -->
### Utiliser uniquement le rebasage

Il est possible de ne jamais faire de fusion à trois sources
 - mais uniquement des rebasages

Dans ce cas il faut :
 - systématiser le `git pull --rebase`
   - `git config --global pull.rebase true`
 - préférer `git push --force-with-lease`
 - *squasher* les *commits* pour éviter les conflits inutiles lors des rebasages
 - maîtriser le `rebase --onto`

%%%

<!-- .slide: data-background-color="#7580ba" class="slide" -->
### Rebaser des branches dépendantes : `rebase --onto`
<div class="center">
	<img src="images/rebase-onto.jpg" width="800px" />
</div>
[Rebaser des branches dépendantes (en)](https://coderwall.com/p/xzsr9g/rebasing-dependent-branches-with-git)<!-- .element: class="after link" -->

%%%


<!-- .slide: class="tp" -->
## [TP5](https://github.com/romain-warnan/formation-git#5-rebasage)
<div class="center">
	<img src="images/keyboard.png" width="600px" />
</div>