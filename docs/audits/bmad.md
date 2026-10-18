# Audit de BMAD

- **Dépôt examiné :** https://github.com/bmad-code-org/BMAD-METHOD
- **Paquet npm :** bmad-method
- **Version :** 6.12.4
- **Date :** 18/10/2026
- **Auditeur :** Amal nekhdou

## Ce que l'installation ajoute au projet
À compléter après l'installation (résultat de `git status`).

## Scripts ou téléchargements externes
- Aucun script `preinstall`, `install` ou `postinstall` dans package.json.
- Recherche dans `tools/installer/` : aucun accès à `.ssh`, aucun envoi
  de données vers un domaine inconnu.
- Appels réseau : registre npm et API GitHub (lecture des versions).
- Commandes lancées par l'installeur : `npm view`, `git clone/fetch`
  et `npm install` (seulement pour les modules externes), `npx yaml-lint`,
  `uv --version`.
- channel-resolver.js relu en entier : le token GitHub (s'il existe) n'est
  envoyé qu'à `https://api.github.com`.
- Dépendance @kayvan/markdown-tree-parser : pas encore vérifiée.

## Accès à des données ou secrets
- Variables lues : BMAD_DEBUG, BMAD_VERBOSE_INSTALL, USER/USERNAME,
  GITHUB_TOKEN (optionnel).
- Écriture hors du dépôt : cache dans `~/.bmad/cache`.
- Mesure : aucun GITHUB_TOKEN défini pendant l'installation.

## Conclusion
Installation autorisée avec précautions : module de base uniquement,
aucun module externe ou personnalisé, aucun secret exposé.