# Ordonnances Rapides

Application web statique pour rechercher et copier rapidement des lignes d’ordonnance, avec une partie administration protégée par Firebase Auth.

## Structure

- index.html : page de recherche publique
- admin.html : page d’administration
- firebaseConfig.js : configuration Firebase à compléter
- style.css : styles de l’interface
- firestore.rules : règles de sécurité Firestore

## 1. Remplir firebaseConfig.js

Ouvrez [firebaseConfig.js](firebaseConfig.js) et remplacez les valeurs placeholder par celles de votre projet Firebase :

```js
const firebaseConfig = {
  apiKey: "VOTRE_API_KEY",
  authDomain: "VOTRE_PROJECT_ID.firebaseapp.com",
  projectId: "VOTRE_PROJECT_ID",
  storageBucket: "VOTRE_PROJECT_ID.appspot.com",
  messagingSenderId: "VOTRE_MESSAGING_SENDER_ID",
  appId: "VOTRE_APP_ID",
};
```

## 2. Activer Firebase Auth (Email/Password)

Dans la console Firebase :

1. Ouvrez Authentication > Sign-in method.
2. Activez Email/Password.
3. Créez un premier compte administrateur depuis la console Firebase ou via l’interface si vous préférez.

## 3. Déployer les règles Firestore

Depuis la racine du projet, exécutez :

```bash
firebase deploy --only firestore:rules
```

## 4. Déployer sur GitHub Pages

1. Poussez les fichiers sur GitHub.
2. Dans GitHub, ouvrez le dépôt > Settings > Pages.
3. Sélectionnez la branche principale et le dossier racine.
4. Publiez le site.

Commande Git :

```bash
git add .
git commit -m "Initial release"
git push
```

## 5. Créer le premier compte admin

Le plus simple est de créer un utilisateur depuis la console Firebase :

1. Ouvrez Authentication > Users.
2. Cliquez sur Add user.
3. Saisissez l’e-mail et le mot de passe de l’administrateur.
4. Connectez-vous ensuite sur /admin.html.

## Notes importantes

- La page de recherche fonctionne sans authentification pour la lecture.
- Les écritures sont autorisées uniquement aux utilisateurs authentifiés.
- Les données sont stockées dans la collection Firestore ordonnances.
