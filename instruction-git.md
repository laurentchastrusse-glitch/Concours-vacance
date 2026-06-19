# Instructions Git — À lire avant tout projet de code

## ⚠️ Règle absolue : jamais de `git init` à la racine du home

Ne jamais initialiser un dépôt Git directement dans `/Users/laurent.chastrusse/` ou `~`.

Cela a déjà causé l'accumulation de **301 Go** de données fantômes sur le disque (juin 2026), sans aucun commit ni sauvegarde réelle.

---

## ✅ Comment bien créer un projet Git

Toujours créer un sous-dossier dédié avant d'initialiser Git :

```
~/Desktop/[PERSO]-IA/nom-du-projet/
~/Desktop/AO/nom-du-projet/
~/Projets/nom-du-projet/
```

Exemple correct :
```
mkdir ~/Desktop/[PERSO]-IA/mon-nouveau-projet
cd ~/Desktop/[PERSO]-IA/mon-nouveau-projet
git init
```

---

## ✅ Pour déposer un projet sur GitHub (via Antigravity, Codex, Claude)

Toujours préciser explicitement le dossier cible lors de la demande, par exemple :

> "Crée le projet dans `~/Desktop/[PERSO]-IA/nom-du-projet/` et dépose-le sur GitHub"

Ne jamais dire simplement "mets-le sur Git" sans préciser le dossier — l'outil pourrait initialiser Git au mauvais endroit.

---

## ✅ Comment vérifier qu'un Git fantôme n'existe pas

Dans le Terminal :

```
ls ~/.git
```

Si la commande retourne des fichiers → problème, prévenir Laurent ou supprimer avec `rm -rf ~/.git`.
Si elle retourne "No such file or directory" → tout va bien.

---

## ✅ Les `.venv`, `node_modules`, `.local` dans les projets

Ces dossiers sont créés automatiquement par les outils de code (Python, Node.js). Ils sont **recréables à tout moment** et ne doivent jamais être committés dans Git ni conservés si le projet est abandonné.

Ils peuvent être supprimés librement pour récupérer de l'espace :
- `.venv/` → environnement Python
- `node_modules/` → dépendances JavaScript
- `.local/` → runtime Node.js

---

*Créé le 3 juin 2026 suite au nettoyage de 322 Go sur le disque de Laurent.*
