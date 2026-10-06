# Conventions du projet Cap Web

Ces conventions valent pour toute personne et tout agent qui modifie ce projet. Ce que Cap Web doit faire est décrit dans [SPEC.md](SPEC.md).

## Nommage

- Une fonction porte un verbe qui dit ce qu'elle fait, en camelCase : `validateMessage`, `replyTo`, `renderMessages`, `sauvegarder`.
- Une constante de réglage s'écrit en majuscules : `LIMITE`, `MOTS`, `REPONSES`, `CLE`. Une valeur comme la limite n'est écrite qu'à un seul endroit.
- Une variable dit ce qu'elle contient, sans abréviation : `historique`, `motsDuCahier`, pas `liste` ni `tmp`.
- Un fichier de `public/js` porte un nom court en minuscules qui dit son rôle : `brain.js` (les règles), `view.js` (l'affichage), `app.js` (le câblage).
- Un fichier de test finit par `.test.js` et se range dans `tests/`.
- Un message de commit commence par son type, puis dit ce qui change en une phrase : `fix:`, `feat:`, `test:`, `docs:`, `refactor:`. Exemple : « fix: replyTo ignore les espaces autour du message ».

## Interdits

1. Ne modifie jamais `tests/contrat/`, `browser/contrat.spec.js` ni `cahier-personnel.json`. Si un test te semble faux, arrête-toi et explique pourquoi.
2. N'écris jamais un message dans la page avec `innerHTML`, `outerHTML` ou `insertAdjacentHTML` : le texte reste du texte, avec `textContent`.
3. Ne mélange pas les rôles : `brain.js` ne touche ni à `document`, ni à `window`, ni à `localStorage` ; `view.js` n'appelle ni `replyTo` ni `validateMessage` ; `app.js` ne crée pas de `li`.
4. N'ajoute aucune dépendance et ne modifie ni `package.json`, ni `package-lock.json`, ni `dependances-autorisees.json`.
5. N'écris aucune clé, aucun mot de passe ni aucune donnée personnelle dans un fichier, et ne crée pas de fichier `.env`.
6. Ne lance aucune commande Git (`commit`, `push`, `reset`, `tag`) : les commits sont faits par le binôme, après relecture du diff.
7. Ne fais qu'un changement par demande, dans les seuls fichiers nommés. Pour un test rouge, corrige le code, jamais le test.
