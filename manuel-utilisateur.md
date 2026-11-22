# Manuel utilisateur — Synchronisation multi-appareils

Cette fonctionnalité permet d'ouvrir l'application depuis la tablette **et** depuis l'ordinateur, via l'URL en ligne (https://epscrozier69.github.io/tournoiUNSS/tournoiUNSS.html), en ayant toujours les données les plus à jour, sans avoir à exporter/importer manuellement un fichier.

## 1. Mise en place

L'adresse de synchronisation (Google Apps Script) est déjà intégrée dans l'application : il n'y a rien à configurer sur les appareils, la synchronisation fonctionne dès l'ouverture de la page.

Cette adresse a été mise en place une fois pour toutes via :
1. Une feuille Google Sheets dédiée.
2. Un script Apps Script (menu **Extensions → Apps Script**) qui lit/écrit les données de l'application dans cette feuille.
3. Un déploiement du script en **Application Web** (accès : Tout le monde), dont l'URL est intégrée directement dans le code de `tournoiUNSS.html` (constante `SYNC_URL`).

Si un jour il faut changer de feuille Google Sheets ou redéployer le script, il suffit de remplacer la valeur de `SYNC_URL` dans `tournoiUNSS.html`.

## 2. Utilisation au quotidien

- À l'ouverture de l'application, elle va automatiquement chercher en ligne si des données plus récentes existent (par exemple saisies sur l'autre appareil) et les charge si c'est le cas.
- Après chaque modification (score, création de tournoi, etc.), les données sont automatiquement envoyées en ligne quelques secondes plus tard — aucune action nécessaire.
- Le bouton **🔁 Synchroniser** permet de forcer une synchronisation immédiate (utile avant de changer d'appareil).
- Le badge affiche l'état :
  - ✅ **Synchronisé** — tout est à jour.
  - 🔄 **Synchronisation…** — envoi ou récupération en cours.
  - ⚠️ **Hors ligne** — pas de connexion internet ; l'application continue de fonctionner normalement avec les données locales, la synchronisation reprendra automatiquement à la prochaine ouverture ou au clic sur "Synchroniser" une fois la connexion revenue.
  - ⚙️ **Non configurée** — ne devrait normalement jamais apparaître, l'adresse étant déjà intégrée dans l'application.

## 3. Points importants

- Une connexion internet est nécessaire pour synchroniser (pas pour utiliser l'application, qui fonctionne aussi hors ligne avec les dernières données connues).
- Si deux appareils modifient les données **en même temps** sans synchroniser entre les deux, c'est la modification la plus récente qui est conservée lors de la prochaine synchronisation (l'autre est perdue). Pensez à synchroniser avant de changer d'appareil pour éviter ce cas.
- L'export/import manuel de fichier JSON (boutons "💾 Exporter une sauvegarde" / "📂 Importer") reste disponible en complément, pour une sauvegarde de secours.
