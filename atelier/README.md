# Cap Web

## À quoi sert Cap Web

Cap Web est un assistant conversationnel pour les adhérents d'un club sportif amateur.
On lui écrit un message dans une page web et il répond avec des règles fixes : il ne fait appel à aucune IA.
Il reconnaît « salut », « bonjour », « aide », « test » et deux mots du club, « prairie » et « mission » ; la conversation est gardée dans le navigateur.

## Installer et lancer

Il faut Node 24.20 ou plus récent. Toutes les commandes se lancent dans le dossier `atelier`.

```sh
node --version
npm ci
npm start
```

`npm ci` annonce une vulnérabilité : c'est normal, ne lancez pas `npm audit fix`.
Ouvrez ensuite http://127.0.0.1:3000 dans le navigateur. Ctrl+C arrête le serveur.

Pour lancer les tests :

```sh
npm test
```

Les tests navigateur sont facultatifs (environ 150 Mo à télécharger la première fois) :

```sh
npx playwright install chromium
npm run test:browser
```

On ne modifie jamais `tests/contrat/`, `browser/contrat.spec.js` ni `cahier-personnel.json`.

## Les trois modules de `public/js`

| Module | Rôle |
|---|---|
| `brain.js` | Les règles. `validateMessage` dit si un message est acceptable (du texte, non vide, 320 caractères au plus) et `replyTo` choisit la réponse. Il ne touche jamais à la page. |
| `view.js` | L'affichage. `renderMessages` écrit une ligne par message dans la liste, avec `textContent`. Il ne décide d'aucune réponse. |
| `app.js` | Le câblage. Il écoute le formulaire et le bouton « Effacer », tient l'historique, l'enregistre dans le navigateur sous la clé `capweb.historique` et demande l'affichage à `view.js`. |

Le détail de ce que Cap Web doit faire est dans [SPEC.md](SPEC.md), et les conventions du projet dans [AGENTS.md](AGENTS.md).
