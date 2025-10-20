# Telmi Stories — Le Mystère de l’École (FR, 5 ans)

Ce dépôt contient des histoires interactives au format Telmi. Cette Pull Request ajoute un nouveau package complet en français pour des enfants de 5 ans.

Nouvelle histoire
- Titre: Le Mystère de l’École
- Thème: Enquête coopérative à l’école (choix guidés, ton rassurant)
- Âge: 5 ans
- Catégorie: Enquête
- Version: 2

Structure du package (dossier stories/telmi/le-mystere-de-l-ecole)
- metadata.json: métadonnées (titre, uuid v4, image de couverture, description, âge)
- nodes.json: scènes et transitions (actions, conditions, inventaire, contrôle)
- notes.json: tous les textes de l’histoire (titres lisibles et paragraphes)
- title.png (640x480): image de titre (placeholder)
- cover.png (640x480): couverture (placeholder)
- title.mp3: fichier audio présentiel (silencieux court, placeholder)
- images/
  - i0.png (128x128): icône Indices (placeholder)
  - i1.png (128x128): icône Clé du local (placeholder)
- audios/: dossier réservé (aucun audio de scène, autoplay gère la navigation)

Inventaire
- Indices (item 0): compteur (incrémenté sur bons choix)
- Clé du local (item 1): booléen (0/1), obtenu dans certaines conséquences

Topologie et règles
- startAction: a0 (index 0)
- Universal Home Rule: chaque scène déclare home: { action: "backAction", index: 0 }
- backStage, backAction, backChildAction inclus pour se conformer au template
- 3 phases: chacune comprend 1 scène narrative (autoplay true), 3 choix (autoplay false), et des conséquences (autoplay true) conditionnées sur l’inventaire
- Toutes les scènes ont image: null et audio: null (les médias sont optionnels côté OS)

Contrôles
- Scènes narratives: { ok: true, home: true, autoplay: true }
- Scènes de choix: { ok: true, home: true, autoplay: false }
- Conséquences: { ok: true, home: true, autoplay: true }

Comment tester
1) Ouvrir le projet dans l’outil Telmi/OS attendu (ou dans votre navigateur/outil interne).
2) Charger le dossier stories/telmi/le-mystere-de-l-ecole.
3) Lancer l’histoire: vérifiez que l’inventaire se met à jour, que le bouton Home renvoie bien vers backAction, et que les transitions respectent les phases.

Édition / extension
- Les textes sont centralisés dans notes.json (français simple, phrases courtes). Ajoutez/éditez des scènes en veillant à garder la clé de scène identique entre nodes.json (stages/actions) et notes.json.
- Les conditions d’inventaire se définissent dans nodes.json (actions.*[].conditions). Les comparateurs utilisés: 4 (>=) et 2 (==).
- Les images sont des placeholders. Remplacez-les par vos visuels finaux si nécessaire (mêmes dimensions recommandées).

Licence
- Contenu éducatif démo/placeholder. À adapter selon les besoins du produit final.
