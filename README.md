# Bacs à sable réglementaires pour l’IA dans le nucléaire

Le site (`index.html`) est hébergé sur GitHub Pages. Il affiche le plan du rapport, en français ou en anglais, dès l'ouverture.

Les données sont dans `resources.json`, à l'intérieur du dossier SharePoint du groupe. Ce fichier est la seule source : ressources, avancement, entretiens, disponibilités, questionnaires et modèles.

## 1. Mise en place sur GitHub (une fois)

1. Créer un dépôt, par exemple `ia-surete-nucleaire`.
2. Y déposer **uniquement** `index.html`.
3. *Settings › Pages* : choisir **Deploy from a branch**, branche `main`, dossier `/ (root)`, puis *Save*.
4. Le site est en ligne à l'adresse `https://<compte>.github.io/ia-surete-nucleaire/`.

> La page GitHub est publique et contient le texte du plan, en français et en anglais. Les ressources, les entretiens, les noms des interlocuteurs et les PDF restent dans SharePoint.

## 2. Dossier du groupe sur SharePoint (une fois)

```
IA-surete/
├── resources.json      ← fichier fourni
└── PDF/                ← documents archivés, un sous-dossier par section du rapport
    ├── 1.1.1 Médical/
    ├── 1.2.1 AI Act/
    └── …               (30 sous-dossiers, de 1.1.1 à 4.5)
```

Chaque membre clique sur **Synchroniser** dans SharePoint pour retrouver ce dossier dans son explorateur de fichiers (OneDrive). Il est recommandé d'utiliser **Edge ou Chrome**.

## 3. Utilisation

### Ouverture et enregistrement
- Cliquer sur **Ouvrir le dossier** et choisir le dossier `IA-surete` synchronisé. Tant que le dossier n'est pas ouvert, seul le plan est consultable.
- À la première ouverture, le site demande votre nom. Il est enregistré avec chacune de vos modifications.
- **Enregistrement automatique** (Edge et Chrome) : chaque ajout ou modification est enregistré dans `resources.json` après un court délai. Il l'est aussi à la fermeture d'une fiche, quand vous quittez l'onglet, et toutes les minutes. L'indicateur en haut à droite affiche « Enregistré à hh:mm ».
- **Travail à plusieurs** : le site relit `resources.json` toutes les 15 secondes et intègre les modifications des autres membres. Une modification n'écrase que l'élément modifié : une ressource, un entretien ou une plage. Quand deux personnes modifient le même élément, la modification la plus récente l'emporte.
- *Firefox et Safari* : l'enregistrement automatique n'est pas possible. Un bouton « Télécharger resources.json » permet de récupérer le fichier, à replacer dans le dossier.

### Langue
- Le sélecteur **FR / EN** en haut à droite bascule tout le site : interface et plan.
- À la première visite, le site choisit la langue sans aucun appel extérieur : il s'ouvre en français si le fuseau horaire de l'ordinateur est celui de la France (métropole ou outre-mer), en anglais sinon.
- Pour envoyer le lien en anglais à un interlocuteur étranger, ajouter `?lang=en` à l'adresse (`…/ia-surete-nucleaire/?lang=en`).
- Un choix manuel FR / EN est ensuite mémorisé sur le poste.

### Ressources
- Bouton « + Ajouter ». Le code (`R-1.3.2-01`) est attribué automatiquement.
- Le titre ouvre le lien internet ; sous le titre, les deux premières lignes du **résumé** (survoler le titre pour le lire en entier). Le bouton **PDF ↗** (ou **DOCX ↗**, **PPTX ↗**) ouvre le document archivé : un PDF s'ouvre dans un onglet, un fichier Word ou PowerPoint est téléchargé pour être ouvert dans son application.
- **Fiche d'une ressource** : résumé, lien internet, et **chemin relatif** du document depuis le dossier du groupe (celui de `resources.json`), par exemple `PDF/1.3.1 REGLAB/RegLab Handbook V2.pdf`, avec un bouton pour le copier. Le site cherche le fichier à ce chemin, puis dans les autres sous-dossiers de `PDF/` s'il a été déplacé.
- La recherche porte aussi sur les résumés. L'export CSV contient le résumé et le chemin relatif.
- **Analyse** : chaque document porte un statut *À analyser / En cours d'analyse / Analyse terminée*. Il se change dans le tableau ou dans la fiche. Les lignes sont colorées selon ce statut : orangé pour *en cours*, vert pour *terminée*. Le tableau peut aussi être filtré sur ce statut.

### Disponibilités et planification (onglet dédié)
Les onglets sont : Accueil, Rapport, Ressources, Entretiens, Disponibilités. L'onglet Disponibilités s'ouvre sur trois choix : on clique sur ce que l'on veut faire.

**1. Saisir les disponibilités**
- Choisir la personne (« Pour qui ? »), puis une date et une ou plusieurs plages (« + Autre plage ce jour »), et cliquer sur *Ajouter*.
- Pour plusieurs semaines, *Coller une liste* : une date par ligne, par exemple `05/11/2026 9h-12h, 14h-17h`.
- Le tableau « Plages de … » se modifie directement : date, début et fin. Une modification qui sortirait un créneau candidat ou retenu des disponibilités est refusée.
- Des lignes cochées peuvent être copiées sur la semaine suivante, répétées sur plusieurs semaines ou supprimées.
- Les colonnes *Favorable à US / AS* sont calculées automatiquement : au moins une heure entre 8h et 18h à Washington ou à Tokyo, changements d'heure compris.
- **Fichier de disponibilités (.txt)**, pour la mise à jour hebdomadaire.
  - Format : une ligne `# Nom` par personne, puis une date par ligne (`20/10/2026 9h-12h, 14h-17h`). Les lignes commençant par `//` sont ignorées.
  - *Exporter les plages (.txt)* produit ce fichier à partir des disponibilités actuelles. *Enregistrer disponibilites.txt dans le dossier* le dépose dans le dossier du groupe.
  - Après chaque modification du fichier (par exemple dans le Bloc-notes), le site le signale (« Nouvelle version à importer »). On clique sur *Mettre à jour depuis ce fichier*, ou on importe un autre fichier avec *Importer un fichier .txt*.
  - Le site affiche d'abord les changements par personne : plages ajoutées, supprimées et inchangées. Il indique aussi les conséquences : les créneaux candidats qui ne sont plus possibles sont retirés, les créneaux déjà retenus qui ne sont plus couverts sont signalés sans être modifiés. On applique ensuite les changements.
  - Mode *Remplacer* (par défaut) : sur la période couverte par le fichier, les plages de chaque personne citée sont remplacées par celles du fichier. Mode *Ajouter* : seules les nouvelles plages sont ajoutées.
- *Équipe* : rôles et **adresses électroniques**, utilisées comme destinataires des messages .msg et comme participants des invitations .ics. On peut aussi ajouter une personne, ou en retirer une avec le bouton × : ses plages de disponibilité sont alors supprimées, et elle est retirée des entretiens et des réunions où elle figurait. Le contact ASNR ne peut pas être retiré.
- *Importer des adresses copiées depuis Outlook* : coller la liste telle qu'Outlook l'affiche (`SEFTA Faiza, NEA/SAF <…>; ioualalen <…>; …`), puis cliquer sur *Analyser*. Le site propose la personne correspondante, ou une nouvelle personne ; on vérifie, puis on clique sur *Appliquer*.

**2. Voir le calendrier de l'équipe**
- Choisir les personnes affichées (chacune a sa couleur), puis la vue *Mois*, *Semaine* ou *Jour*.
- Trois lectures :
  - *Chacun* : les plages de chaque personne ;
  - *Recouvrement* : en vert, les moments où tout le monde est disponible ;
  - *Hors recouvrement* : en hachuré, les moments où il manque quelqu'un, avec ses initiales.
- Un clic sur une plage ou dans une zone vide ramène au volet 1, prêt à modifier ou à ajouter une plage.

**3. Planifier une réunion ou un entretien** (assistant en 4 étapes)
- En haut, choisir un entretien, une réunion interne déjà créée, ou *+ Nouvelle réunion interne*.
- **Étape 1 — Quoi ?** Type de réunion, objet, durée, format (Teams, présentiel, téléphone), lieu et fuseau de l'interlocuteur. Le type *Réunion d'avancement* est numéroté automatiquement (« Réunion d'avancement n° 1, 2, 3… », « Progress meeting No. … » en anglais). *Autre réunion* laisse le titre libre. L'ordre du jour et les informations pour les participants sont repris dans l'invitation.
- **Ordre du jour : une seule source, reprise partout.**
  - *Entretien* : il est généré à partir de la fiche (présentation de l'étude et des objectifs de l'entretien, échanges sur le questionnaire avec les points à examiner, documents éventuels et suites à donner), avec des durées proportionnelles à celle de l'entretien. Il se modifie dans l'assistant ou depuis le bouton *Modifier* de la fiche. La même version figure dans la fiche, le guide d'entretien, le message de confirmation et l'invitation .ics. *Régénérer depuis la fiche* revient à la version générée.
  - *Réunion d'avancement* : il est prérempli à partir de l'état du projet : décisions de la réunion précédente, avancement du rapport, ressources et analyses, entretiens réalisés, planifiés (avec leur propre ordre du jour), en attente de réponse ou à planifier. *Mettre à jour depuis l'état du projet* le recalcule.
- **Étape 2 — Qui ?** Par défaut, pour une nouvelle réunion, seuls Ben Mekki Ayadi et Arnault Ioualalen sont obligatoires ; tous les autres sont facultatifs. Seuls les obligatoires limitent les créneaux. Pour un entretien, les participants de la fiche sont repris, ainsi que les interlocuteurs. On peut ajouter d'autres invités par leur adresse.
- **Étape 3 — Quand ?** Le site cherche la combinaison qui réunit le plus de monde. L'encadré *Meilleures combinaisons* propose les trois créneaux qui rassemblent le plus de facultatifs, avec les absents, et on peut les cocher d'un clic. Le tableau, trié par défaut des meilleurs créneaux aux moins bons, montre la présence de chacun (★ pour les meilleurs).
  - Les créneaux déjà pris par une autre réunion ou un autre entretien sont écartés.
  - Le filtre *Créneaux* (heures ouvrées US ou Asie) se règle seul selon le fuseau de l'interlocuteur.
  - On coche les créneaux, puis *Ajouter aux créneaux candidats*. Une nouvelle réunion est alors enregistrée dans `resources.json`.
- **Étape 4 — Proposer, retenir, inviter**, en deux temps. Les messages se téléchargent en **.msg** : ce sont des brouillons Outlook, destinataires et pièces jointes déjà en place. Pour une réunion interne, tout le monde est en « À ». Pour un entretien, l'interlocuteur est en « À » et l'équipe en copie.
  - **A. Proposer : message d'accroche.**
    - Pour un entretien, c'est le courriel d'invitation de la fiche. Il présente l'étude, liste les créneaux candidats et invite l'interlocuteur à en choisir un ou à en proposer d'autres. Le questionnaire Word est joint (case à cocher, ainsi que le guide d'entretien).
    - Pour une réunion interne, le message présente la réunion. L'ordre du jour Word est joint.
    - *Voir ou modifier le message* ouvre le texte à gauche et l'aperçu mis en forme à droite. Pour un entretien, les modifications enregistrées sont reprises dans la fiche, et inversement.
    - Aucune invitation .ics n'est envoyée à ce stade.
  - **Réponse de l'interlocuteur.** On clique sur *Convient ?* pour chaque créneau accepté, dans l'ordre de préférence (choix n° 1, 2, 3…), puis on clique sur *Retenir*. Les autres créneaux acceptés restent enregistrés comme **options de repli**.
  - **B. Confirmer et inviter.**
    - Une fois le créneau retenu, *Message de confirmation (.msg)* joint les documents Word, sans fichier .ics ; l'invitation agenda se télécharge à part (*Invitation agenda (.ics)*).
    - Le message et l'invitation reprennent les mêmes informations : date, heure locale, durée, format, participants, puis, pour un entretien, l'objectif et les documents support.
    - En cas d'empêchement, *Basculer sur cette option* retient une option de repli sans redemander de disponibilités. On renvoie alors la confirmation et l'invitation (.ics) : la nouvelle invitation remplace l'ancienne dans les agendas.
    - *Libérer* remet le créneau parmi les candidats.

- **Suivi des réunions et des entretiens** (en bas) : tout ce qui est en cours, avec son statut. Un clic reprend l'élément dans l'assistant.

### Entretiens
- **Calendrier des entretiens** : une frise montre, jour par jour, les créneaux proposés (pointillés), les entretiens retenus (bleu foncé) et réalisés (gris). Un clic ouvre la fiche de l'entretien.
- **Planifier depuis la fiche** : la planification d'un entretien part de sa fiche (*Planifier dans l'onglet Disponibilités*). L'assistant affiche alors un bandeau *← Retour à la fiche* pour y revenir à tout moment, ainsi qu'un bouton de retour en bas de l'étape 4. Les choix faits dans l'assistant sont enregistrés dans la fiche.
- **Interlocuteurs** : dans la fiche (*Modifier*), une ligne par interlocuteur avec son prénom, son nom, sa fonction et son adresse électronique. Les interlocuteurs qui ont une adresse sont destinataires du courriel d'invitation et invités dans le fichier .ics. Un champ *Remarques* reste disponible.
- **Équipe et contraintes** : pour chaque entretien, on coche les participants : Arnault Ioualalen par défaut ; les autres membres de l'équipe au choix. Le titre « Créneaux libres communs à » reprend tous les participants cochés. Pour chaque participant, la case **« contraignant »** indique si ses disponibilités limitent les créneaux possibles.
  - Les créneaux proposables sont ceux où **tous les participants contraignants** sont disponibles en même temps.
  - Un participant non contraignant est présent sans bloquer le choix.
  - Un participant contraignant qui n'a saisi aucune disponibilité est signalé et ignoré.
  - Un créneau déjà proposé ou retenu pour un autre entretien n'est plus proposé si un participant contraignant y est déjà engagé.
- **Contact ASNR** : Ben Mekki Ayadi est le contact ASNR sur les documents et signe les invitations.
- **Créneaux** : renseigner le fuseau horaire de l'interlocuteur (Washington, Ottawa, Tokyo…). Les créneaux s'affichent avec son heure locale. Pour un interlocuteur américain ou asiatique, les créneaux situés dans ses heures ouvrées (8h–18h locales) sont mis en avant, et on peut n'afficher qu'eux. On coche les créneaux à proposer ; le courriel d'invitation les liste avec l'heure locale. On clique sur **Retenir** quand l'interlocuteur a choisi.
- **Documents** : guide d'entretien, courriel d'invitation (aussi téléchargeable en brouillon Outlook .msg), questionnaire et trame de compte rendu, en français ou en anglais. Chacun est modifiable pour l'entretien, puis téléchargeable en Word (.doc). Le questionnaire commun (FR et EN) et les modèles de courriel se modifient en bas de l'onglet Entretiens. En anglais, le courriel et la confirmation commencent par « Dear » suivi du prénom et du nom des interlocuteurs de la fiche (champ {interlocuteurs}), ou « Dear Sir or Madam » si aucun nom n'est renseigné. Les questions fournies sont un **projet à valider par le groupe**.
- **Mettre à jour les fiches d'entretien** (bouton sous le questionnaire) : les documents qui n'ont pas été personnalisés suivent automatiquement le questionnaire. Pour ceux qui ont été modifiés pour un entretien, le site signale les questions absentes, et on choisit pour chaque document :
  - **Synchroniser** : les nouvelles questions sont ajoutées à la fin, sous « Nouvelles questions (à consolider) ». La consolidation se fait ensuite manuellement.
  - **Écraser** : le document est remplacé par la version générée à partir du questionnaire actuel.
  - **Ne pas importer** : le document reste tel quel.
- L'invitation agenda (.ics) est disponible une fois le créneau retenu.
- La page d'accueil affiche le **prochain entretien** et le fil d'Ariane des phases.

### Gestion et suivi (onglet Suivi)
- **Fil d'Ariane de l'étude** : lancement, puis les 4 phases du rapport (avec leur avancement), puis les jalons. L'étape en cours est encadrée.
- **Frise chronologique** : les jalons (losange pour une date, bande pour une période), les réunions et les entretiens, avec la date du jour. Un clic sur une réunion ou un entretien ouvre sa planification ou sa fiche. Jalons par défaut : début le 02/10/2026, fin le 30/01/2027, restitution finale / calage restreinte à la DERT en février 2027, grande restitution en mars–avril 2027. **Modifier les jalons** permet de changer un libellé ou une date, d'ajouter un jalon (une date, ou un début et une fin pour une période) ou d'en supprimer un.
- **Réunions passées** : réunions et entretiens dont la date est passée, avec leurs documents (fiche, guide, questionnaire, trame de CR, ordre du jour, invitation .ics). Pour une réunion : lien du compte rendu et relevé de décisions (une décision par ligne), et **+ Action issue de cette réunion**.
- **Réunions planifiées** : dates retenues à venir, avec leurs documents et l'état de l'invitation.
- **Réunions à planifier** : sans date retenue (créneaux en attente de réponse, ou aucun créneau proposé), avec **Planifier →**, et **+ Réunion d'avancement n° N** pour préparer la suivante.
- **Plan d'actions** : le suivi de ce qui a été décidé. Chaque action a un numéro (A1, A2…), un libellé, un **rattachement** (un chapitre ou sous-chapitre du rapport, un entretien, ou rien), la réunion où elle a été **décidée**, un responsable, une échéance, un état (*À faire*, *En cours*, *Fait*) et des précisions. L'état se change directement dans le tableau ; un clic sur l'action l'ouvre pour la modifier. Filtres : état (à faire et en cours, en retard, faites, toutes), responsable, rattachement. Les actions en retard sont signalées. Une action se crée avec **+ Nouvelle action**, depuis une réunion passée (**+ Action issue de cette réunion**) ou depuis la fiche d'un entretien, qui affiche aussi les actions qui lui sont rattachées.
- **Lien avec les réunions d'avancement** : l'ordre du jour de la réunion n° N reprend le relevé de décisions de la réunion n° N-1 et le plan d'actions (actions en cours ou à faire, dont celles en retard).

### Règles de cohérence de la planification
Les mêmes règles s'appliquent partout (fiche de l'entretien, formulaire, assistant de l'onglet Disponibilités, onglet Suivi) et à l'ouverture du fichier :
- **Créneau retenu** : il remplace les créneaux candidats. Les créneaux acceptés par l'interlocuteur deviennent des options de repli ; les autres sont mémorisés.
- **Changer de créneau retenu** (option de repli, formulaire) : l'invitation .ics passe à une nouvelle version, qui remplace l'ancienne dans les agendas ; l'invitation est signalée « pas encore envoyée » jusqu'à son renvoi.
- **Libérer le créneau retenu** (fiche, assistant, ou « Non fixé » dans le formulaire) : le créneau retenu, les options de repli et les autres créneaux proposés encore à venir redeviennent candidats.
- **Statut d'un entretien** : « Planifié » si et seulement si un créneau est retenu. Il passe à « Planifié » quand on retient un créneau et revient à « Contacté » quand on le libère ; les choix incompatibles sont grisés. « Réalisé » et les statuts suivants ne sont jamais modifiés automatiquement. Une fois la date passée, la fiche et l'onglet Suivi invitent à mettre à jour le statut (**Marquer réalisé**).
- **Disponibilités** : modifier ou supprimer une plage au tableau a les mêmes effets que l'import du fichier texte. Les créneaux candidats (entretiens et réunions) qui ne sont plus couverts sont listés, retirés après confirmation ; les créneaux retenus qui ne sont plus couverts sont signalés sans être modifiés.
- **Créneaux candidats passés** : signalés dans la fiche, l'assistant et l'onglet Suivi.
- **Ordre du jour d'une réunion d'avancement** : généré à partir de l'état du projet (décisions de la réunion précédente, actions, rapport, ressources, entretiens) et tenu à jour tant qu'il n'est pas modifié à la main. Il est figé à l'envoi de l'invitation, ou quand on renseigne le compte rendu ou les décisions de la réunion.
- **Suppressions** : supprimer une réunion ou un entretien conserve les actions qui en sont issues, sans lien.

### Navigation
- **Rapport** : tout est déplié à l'ouverture. Un clic sur le titre d'un chapitre, d'un sous-chapitre ou d'une carte le plie ou le déplie. Les boutons « Tout plier / Tout déplier » agissent sur tout le rapport, « Plier / Déplier » sur un chapitre ; ces boutons sont toujours sur la ligne sous le titre du chapitre. Le bouton ⤢ affiche une carte, un sous-chapitre ou un chapitre en pop-up ; « Voir dans le rapport » y ramène. Un clic sur une section du sommaire la déplie.
- **Modifier le texte du rapport** : le bouton ✎ d'une carte (ou « ✎ Modifier » d'un chapitre) ouvre l'éditeur, avec le titre, l'illustration et le contexte, l'objectif et les points à examiner, et pour un chapitre sa méthode. La mise en forme simple est possible : `**gras**`, `*italique*`, `[texte](https://lien)`. La modification est enregistrée dans `resources.json` avec son auteur ; elle s'applique au sommaire, aux filtres et aux documents d'entretien. Un ✎ orangé signale une section modifiée, et « Rétablir le texte d'origine » revient au texte de la note. Le texte français et le texte anglais se modifient séparément, selon la langue affichée.
- Les fiches s'ouvrent en cascade (par exemple, un document ouvert depuis la fiche d'un entretien). Le bouton **←** ou la touche Échap ramène à la fiche précédente.

## Paramètres
- **Cadre de l'étude** : programme Expertise augmentée de l'ASNR, perspective de déclinaison du REGLAB au niveau national, contexte de l'industrie nucléaire française, étude exploratoire menée par Numalis pour le compte de l'ASNR et conduite par Arnault Ioualalen, diffusion dans le cadre du REGLAB. Le texte se modifie dans **Paramètres** (une ligne « Libellé : texte » par élément, en français et en anglais) et est enregistré dans `resources.json`.
- *Votre nom* : mémorisé sur le poste.
- *Adresse du dossier PDF sur SharePoint* : facultative. Elle sert seulement lorsque le dossier n'est pas synchronisé sur le poste.
