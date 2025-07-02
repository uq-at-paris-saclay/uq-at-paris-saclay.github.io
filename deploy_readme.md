# 🚀 Déploiement manuel d’un site Jekyll sur GitHub Pages (`gh-pages`)

Cette procédure permet de publier un site Jekyll en construisant le site en local, puis en déployant le contenu de `_site/` sur une branche `gh-pages` via `git worktree`.

---

## 🧱 Préparation initiale (à faire **une seule fois**)

### 1. Créer la branche `gh-pages` sans historique

```sh
git checkout --orphan gh-pages
git rm -rf .
echo "gh-pages branch" > README.md
git add README.md
git commit -m "Initial gh-pages"
git push origin gh-pages
````

### 2. Ajouter un worktree pour accéder à `gh-pages` dans un dossier séparé

```sh
git worktree add ../_deploy gh-pages
```

> 💡 Si une erreur indique que le dossier est déjà enregistré :
> `git worktree prune` puis réessayez.

---

## 🔁 Déploiement (à refaire après chaque modification du site)

### 1. Revenir sur la branche principale (`main`, `master`, etc.)

```sh
git checkout main
```

### 2. Construire le site localement

```sh
bundle exec jekyll build
```

Cela génère le site statique dans le dossier `_site/`.

### 3. Synchroniser `_site/` vers le dossier `../_deploy/` (sans écraser `.git`)

```sh
rsync -av --delete --exclude=".git" --exclude=".gitignore" _site/ ../_deploy/
```

### 4. Commit & push dans la branche `gh-pages`

```sh
cd ../_deploy
git add .
git commit -m "Déploiement du site le $(date +%F)"
git push origin gh-pages
cd -
```

---

## ⚙️ Configuration GitHub Pages

Dans l'interface GitHub :

* Allez dans **Settings > Pages**
* **Source** : `gh-pages`
* **Dossier** : `/ (root)`

Le site sera alors publié à l’adresse :

```
https://<utilisateur>.github.io/<nom-du-repo>/
```

---

## 💡 Script facultatif `deploy.sh`

Vous pouvez créer un script automatisé :

```bash
#!/bin/bash
set -e

echo "🛠  Compilation Jekyll"
bundle exec jekyll build

echo "🔄  Synchronisation vers gh-pages"
rsync -av --delete --exclude=".git" --exclude=".gitignore" _site/ ../_deploy/

echo "✅  Commit & push"
cd ../_deploy
git add .
git commit -m "Déploiement du site le $(date +%F)"
git push origin gh-pages
cd -
```

Rendez-le exécutable :

```sh
chmod +x deploy.sh
```

Et lancez :

```sh
./deploy.sh
```
