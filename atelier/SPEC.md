# Spécification de Cap Web

Chaque critère dit ce que Cap Web fait, puis ce qui le vérifie. Les tests cités sont dans `tests/contrat/brain.contrat.test.js` (lancés par `npm test`) et dans `browser/contrat.spec.js` (lancés par `npm run test:browser`).

1. Quand on envoie un message vide ou fait seulement d'espaces, Cap Web le refuse, affiche une erreur dans le statut et n'ajoute aucune ligne à la conversation.
   Vérifié par : test « refuse le vide et les espaces seuls » et test navigateur « un message fait d’espaces est refusé avec une erreur visible ».

2. Quand on envoie 321 caractères, Cap Web refuse et l'erreur cite 320 ; avec 320 caractères, il accepte. La longueur est mesurée après avoir retiré les espaces autour.
   Vérifié par : tests « accepte 320 caractères et refuse 321 » et « mesure la longueur après avoir retiré les espaces ».

3. Quand on écrit « salut », « bonjour », « aide » ou « test », en majuscules ou en minuscules, avec ou sans espaces autour, Cap Web donne la réponse de ce mot ; « bonjour » reçoit la même réponse que « salut ».
   Vérifié par : tests « ignore la casse et les espaces autour » et « donne la même réponse à « bonjour » et à « salut » ».

4. Quand on écrit « prairie » ou « mission », Cap Web donne à chacun sa propre réponse ; quand on écrit une phrase qu'il ne connaît pas, il répond par un repli différent de toutes les autres réponses.
   Vérifié par : tests « reconnaît les deux mots du cahier personnel, quelles que soient la casse et les espaces autour » et « répond à une phrase inconnue par un repli distinct ».

5. Quand on envoie `<b>gras</b>`, Cap Web l'affiche tel quel, chevrons compris, sans rien mettre en gras.
   Vérifié par : test « view.js affiche du texte et ne décide pas des réponses » et test navigateur « le texte reste du texte, jamais du HTML ». Essai à la main en 30 secondes : `npm start`, envoyer `<b>gras</b>`, lire la ligne affichée.
