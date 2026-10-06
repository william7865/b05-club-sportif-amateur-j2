# Carnet de bord · J2

Binôme : b05 · Membres : William et Nicolas · Nos réglages sont dans `atelier/cahier-personnel.json` : ne les recopiez pas ici.

## Mon positionnement (chacun de vous deux)

Pour chaque notion, chacun écrit « à l'aise » ou « à renforcer ». Ce n'est ni évalué ni classé : c'est votre point de départ pour le bilan individuel de fin de module.

| Notion | Membre 1 : William | Membre 2 : Nicolas |
|---|---|---|
| Structure HTML | | |
| CSS et responsive | | |
| JavaScript | | |
| DOM et événements | | |
| Git | | |
| Tests | | |

Chacun, en une phrase, son objectif personnel pour J2 et J3.

Membre 1 :

Membre 2 :

## R1 · Les tests automatisés

Les tests rouges du départ, et ce que vous en avez fait :

| Test rouge | Cause trouvée (une phrase) | Fichier | Message du commit `fix:` |
|---|---|---|---|
| refuse le vide et les espaces seuls | Le test du vide était fait avant `trim()`, donc un message d'espaces passait. | `public/js/brain.js` | fix: un message fait seulement d'espaces est refusé |
| accepte 320 caractères et refuse 321 | La longueur était comparée à 280 écrit en dur, pas à `LIMITE`. | `public/js/brain.js` | fix: la longueur est comparée à LIMITE, plus à 280 |
| mesure la longueur après avoir retiré les espaces | Même cause : 320 caractères dépassaient le 280 écrit en dur. | `public/js/brain.js` | même commit que la ligne précédente |
| ignore la casse et les espaces autour | `replyTo` mettait le message en minuscules sans retirer les espaces autour. | `public/js/brain.js` | fix: replyTo ignore les espaces autour du message |
| reconnaît les deux mots du cahier personnel, quelles que soient la casse et les espaces autour | Même cause : « ␣␣PRAIRIE␣ » n'était pas reconnu à cause des espaces. | `public/js/brain.js` | même commit que la ligne précédente |
| répond à une phrase inconnue par un repli distinct | Une phrase inconnue recevait la réponse de « aide » au lieu d'un repli à part. | `public/js/brain.js` | fix: une phrase inconnue reçoit un repli distinct de la réponse à aide |
| view.js affiche du texte et ne décide pas des réponses | `view.js` écrivait le message avec `innerHTML`, donc `<b>gras</b>` devenait du gras. | `public/js/view.js` | fix: view.js affiche le message avec textContent, plus avec innerHTML |

Contrôle final : `node --test tests/contrat/brain.contrat.test.js` affiche `pass 15`, `fail 0` ; `git diff --stat depart -- tests cahier-personnel.json` n'affiche rien ; les 8 tests navigateur du contrat passent, dont « le texte reste du texte, jamais du HTML ».

Avec l'agent : ce qu'il a proposé et que vous avez refusé, et pourquoi. L'agent dsh n'a pas été utilisé pour ce round ; les corrections ont été écrites avec un assistant IA de code, une par commit, chaque diff relu avant le commit. Rien n'a été refusé.

Pour aller plus loin : le nom renommé par votre commit `refactor:`, et pourquoi le nouveau est plus clair. Dans `brain.js`, `liste` devient `motsDuCahier` (commit « refactor: liste devient motsDuCahier ») : `liste` ne disait pas de quoi, et le même nom désigne la liste des messages dans `app.js`.

## R2 · Documenter le projet

Vos trois documents sont dans `atelier` : `README.md`, `SPEC.md` et `AGENTS.md`. Rien à recopier ici.

Pour aller plus loin, avec l'agent, les demandes du formateur :

| Demande | Ce qu'a fait l'agent | Votre décision | Règle d'`AGENTS.md` concernée (ou ajoutée) |
|---|---|---|---|
| 1 | | | |
| 2 | | | |
| 3 | | | |

## R3 · Premiers tests unitaires

| À remplir | Votre réponse |
|---|---|
| Fonction tirée | À confirmer selon le tirage du formateur. Les trois fonctions de la fiche sont faites ; la première traitée est F1, `synonyme(message)`. |
| Le rouge vu (message exact) | `SyntaxError: The requested module '../public/js/brain.js' does not provide an export named 'synonyme'` |
| Identifiant du commit `test:` | `e3ef060` (test: synonyme, critères C1 à C5) |
| Identifiant du commit `feat:` | `631975f` (feat: synonyme) |
| Casse volontaire : la ligne changée | Dans `synonyme`, le `return texte;` final remplacé par `return '';` |
| Casse volontaire : le test devenu rouge | « C4 : un autre message revient en minuscules, sans les espaces autour » (48 réussis, 1 échoué), puis tout vert après `git restore` |
| Pour aller plus loin : la deuxième fonction | F2 `compterMots` : commits `3bbdab3` (test) et `21ec3ff` (feat) ; rouge vu `does not provide an export named 'compterMots'` ; casse `return 1;` → C1 et C2 rouges. F3 `estEnMajuscules` : commits `ceffef5` (test) et `2741150` (feat) ; rouge vu `does not provide an export named 'estEnMajuscules'` ; casse `return false;` → C1 et C4 rouges. |

Les critères C1 à C5 de votre fonction, recopiés de la fiche :

F1, `synonyme(message)`, donne le mot de référence. C1 : `'coucou'`, `'hello'` et `'bonsoir'` donnent `'salut'`. C2 : `'help'` et `'sos'` donnent `'aide'`. C3 : la casse et les espaces autour ne comptent pas, `'  HELLO '` donne `'salut'`. C4 : un autre message revient en minuscules, sans les espaces autour, `'  Météo '` donne `'météo'`. C5 : ce qui n'est pas du texte (`undefined`, `null`, `42`) donne `''`, sans erreur.

## R4 · La revue de code

| Patch | Accepté ou refusé | Fichier et ligne | Raison |
|---|---|---|---|
| 1 | | | |
| 2 | | | |
| 3 | | | |

Pour aller plus loin : le patch que vous avez corrigé, et ce que vous avez changé.

## Fin de journée

Chacun, une phrase : ce que vous savez faire ce soir et que vous ne saviez pas faire ce matin. Relisez votre positionnement : une notion est-elle passée de « à renforcer » à « à l'aise » ?
