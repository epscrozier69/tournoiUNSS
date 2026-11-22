# Manuel utilisateur — Synchronisation multi-appareils

Cette fonctionnalité permet d'ouvrir l'application `tournoiUNSS.html` depuis la tablette **et** depuis l'ordinateur, en ayant toujours les données les plus à jour, sans avoir à exporter/importer manuellement un fichier.

## 1. Mise en place (une seule fois)

1. Créez une nouvelle feuille Google Sheets (vide, peu importe son contenu).
2. Menu **Extensions → Apps Script**.
3. Supprimez le code par défaut et collez le script de synchronisation fourni (voir fichier `Code.gs` / instructions données par Claude lors de la mise en place).
4. Enregistrez (icône disquette).
5. **Déployer → Nouveau déploiement** → type **Application Web**.
   - Exécuter en tant que : **Moi**
   - Qui a accès : **Tout le monde**
6. Cliquez sur **Déployer**, puis autorisez l'accès à votre compte Google.
7. Copiez l'URL de l'application Web obtenue (elle se termine par `/exec`).
8. Dans `tournoiUNSS.html`, cliquez sur le badge en haut à gauche (près du bouton "🔁 Synchroniser") et collez cette URL dans la fenêtre qui s'ouvre. Validez.
9. **Répétez l'étape 8 sur chaque appareil** (tablette et ordinateur) avec la **même URL**, afin que les deux appareils pointent vers le même Google Sheet.

## 2. Utilisation au quotidien

- À l'ouverture de l'application, elle va automatiquement chercher en ligne si des données plus récentes existent (par exemple saisies sur l'autre appareil) et les charge si c'est le cas.
- Après chaque modification (score, création de tournoi, etc.), les données sont automatiquement envoyées en ligne quelques secondes plus tard — aucune action nécessaire.
- Le bouton **🔁 Synchroniser** permet de forcer une synchronisation immédiate (utile avant de changer d'appareil).
- Le badge affiche l'état :
  - ✅ **Synchronisé** — tout est à jour.
  - 🔄 **Synchronisation…** — envoi ou récupération en cours.
  - ⚠️ **Hors ligne** — pas de connexion internet ; l'application continue de fonctionner normalement avec les données locales, la synchronisation reprendra automatiquement à la prochaine ouverture ou au clic sur "Synchroniser" une fois la connexion revenue.
  - ⚙️ **Non configurée** — l'URL de synchronisation n'a pas encore été saisie sur cet appareil (voir étape 8 ci-dessus).

## 3. Points importants

- Une connexion internet est nécessaire pour synchroniser (pas pour utiliser l'application, qui fonctionne aussi hors ligne avec les dernières données connues).
- Si deux appareils modifient les données **en même temps** sans synchroniser entre les deux, c'est la modification la plus récente qui est conservée lors de la prochaine synchronisation (l'autre est perdue). Pensez à synchroniser avant de changer d'appareil pour éviter ce cas.
- L'export/import manuel de fichier JSON (boutons "💾 Exporter une sauvegarde" / "📂 Importer") reste disponible en complément, pour une sauvegarde de secours.
