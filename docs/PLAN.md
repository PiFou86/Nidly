# Nidly — Plan initial

> Document vivant. Il sert de point de départ et sera modifié au fur et à mesure.
> Les sections marquées **❓** contiennent des questions encore ouvertes.
>
> Dernière mise à jour : 2026-11-25

---

## 1. Vision

Nidly est un logiciel web qui relie **les parents**, **les éducatrices et éducateurs** et **la direction** d'une garderie autour du quotidien de l'enfant :

- savoir **qui est présent** (et qui est attendu) à tout moment;
- consigner **rapidement** comment s'est passée la journée de chaque enfant (humeur, sieste, appétit, comportement…);
- **communiquer** simplement entre la famille et l'équipe éducative;
- avoir **sous la main** les informations critiques : allergies, incidents, notes au dossier.

Principes directeurs :

1. **Rapide pour l'éducatrice.** La saisie se fait en quelques touches, sur tablette ou téléphone, souvent pour tout un groupe d'un coup.
2. **Rassurant pour le parent.** Le parent voit la journée de son enfant et peut écrire à l'équipe sans friction.
3. **Configurable par garderie.** Chaque établissement choisit ses critères d'observation, ses horaires, ses règles.
4. **Respect de la vie privée dès la conception.** Les données concernent des enfants : accès minimal, traçabilité, hébergement et conservation conformes à la Loi 25.

---

## 2. Vocabulaire

À valider, car les termes varient d'un milieu à l'autre.

| Terme | Définition proposée |
|---|---|
| **Organisation** | L'entité juridique (ex. un CPE ou une entreprise qui exploite une ou plusieurs garderies). |
| **Installation** | Un lieu physique (bâtiment, adresse, permis). Une organisation peut en avoir plusieurs. |
| **Groupe** | Un ensemble d'enfants pris en charge ensemble dans une installation (ex. « Les Poussins », 18 mois–3 ans). « Classe » est un synonyme : on utilise **groupe** partout dans l'application. |
| **Fiche enfant** | Les informations administratives, médicales et de contact de l'enfant. |
| **Journal de bord** | Les observations quotidiennes saisies par l'équipe pour un enfant. |
| **Dossier** | Les notes plus durables (suivi, développement, rencontres) liées à l'enfant. |

---

## 3. Rôles et permissions

### 3.1 Rôles

- **Parent / tuteur** : voit uniquement ses propres enfants. Plusieurs tuteurs par enfant (garde partagée possible).
- **Éducatrice / éducateur** : assigné(e) à une ou plusieurs installations, et à un ou plusieurs groupes.
- **Direction d'installation** : gère une installation (enfants, groupes, personnel, paramètres).
- **Administration de l'organisation** : gère l'ensemble des installations et les paramètres globaux.
- ❓ Rôles possibles plus tard : remplaçante, cuisine (allergies, menus), éducatrice spécialisée, comptabilité.

### 3.2 Portée des accès

Un accès est toujours **limité à une portée** :

- un parent → ses enfants;
- une éducatrice → les enfants des groupes qui lui sont assignés, dans les installations qui lui sont assignées (❓ et en lecture seule les autres groupes de l'installation, pour les remplacements ?);
- la direction → toute son installation;
- l'administration → toute l'organisation.

### 3.3 Matrice de permissions (première version)

Légende : ✅ permis · 👁️ lecture seule · ➖ ses propres éléments seulement · ❌ interdit

| Action | Parent | Éducatrice | Direction | Admin org. |
|---|:-:|:-:|:-:|:-:|
| Voir la fiche de l'enfant (contacts, santé) | ➖ | 👁️ | ✅ | ✅ |
| Modifier la fiche de l'enfant | ❓ ➖ (contacts) | ❌ | ✅ | ✅ |
| Voir les allergies et la santé | ➖ | 👁️ | ✅ | ✅ |
| Déclarer les prévisions de présence | ➖ | ❌ | ✅ | ✅ |
| Saisir arrivée / départ | ❓ | ✅ | ✅ | ✅ |
| Valider les présences de la journée | ❌ | ✅ | ✅ | ✅ |
| Saisir le journal de bord | ❌ | ✅ | ✅ | ❌ |
| Lire le journal de bord | ➖ | ✅ | ✅ | 👁️ |
| Écrire à l'équipe d'un groupe | ➖ | ✅ | ✅ | ❌ |
| Déclarer un incident | ❌ | ✅ | ✅ | ❌ |
| Voir les incidents | ➖ | ✅ | ✅ | ✅ |
| Notes au dossier | ❌ | ✅ (créer) | ✅ | 👁️ |
| Configurer les critères d'observation | ❌ | ❌ | ✅ | ✅ |
| Gérer groupes et assignations | ❌ | ❌ | ✅ | ✅ |
| Gérer les installations | ❌ | ❌ | ❌ | ✅ |
| Consulter le journal d'audit | ❌ | ❌ | ✅ | ✅ |

Les **notes au dossier sont internes** : les parents ne les voient jamais. Ce que le parent voit, ce sont les **mots du personnel** (messages et commentaires adressés à la famille) et les **observations de la journée** (journal de bord).

---

## 4. Structure : organisations, installations, groupes

- Une **organisation** possède une ou plusieurs **installations**.
- Une installation a des **groupes**, chacun avec une capacité, une tranche d'âge et un ou plusieurs locaux.
- Un **enfant** est inscrit dans une installation et rattaché à un groupe principal (❓ peut-il changer de groupe en cours de journée, ex. regroupement en fin de journée ?).
- Une **éducatrice** peut être assignée à plusieurs installations et plusieurs groupes, avec un rôle par installation.
- Les **ratios** éducatrice/enfants pourraient être affichés en temps réel à partir des présences (utile pour la direction).

---

## 5. Présences

### 5.1 Prévisions (parents)

- Le parent indique l'**horaire prévu** de son enfant : récurrent (ex. lundi au vendredi, 7 h 30 à 16 h 30) et exceptions ponctuelles (absence, arrivée tardive, départ hâtif, vacances).
- ❓ Délai limite pour modifier une prévision (ex. la veille à 18 h) ?
- ❓ Le parent peut-il indiquer **qui viendra chercher** l'enfant (personne autorisée) ?
- La direction voit les prévisions agrégées : nombre d'enfants attendus par groupe et par plage horaire, utile pour planifier le personnel.

### 5.2 Présences réelles

- Arrivée et départ saisis par l'éducatrice (ou ❓ par le parent à l'entrée, via code ou borne).
- Vue « **tableau du groupe** » : tous les enfants du groupe, attendus / arrivés / partis / absents, en un coup d'œil.
- Écart entre prévu et réel mis en évidence (ex. enfant attendu à 8 h, pas arrivé à 9 h).
- **Validation** des présences en fin de journée par l'éducatrice ou la direction; correction ensuite tracée.
- ❓ Exports nécessaires pour la facturation ou les rapports au ministère ?

---

## 6. Journal de bord quotidien

### 6.1 Critères configurables par garderie

Chaque installation (ou organisation) choisit ses critères. À la création, on propose des **suggestions par défaut** :

| Critère | Type de réponse | Fréquence suggérée |
|---|---|---|
| Humeur | Échelle (😀 🙂 😐 🙁 😢) | Matin / après-midi |
| Sieste / sommeil | Heure de début, heure de fin, qualité | Par sieste |
| Appétit (dîner, collations) | Échelle (tout mangé / un peu / rien) | Par repas |
| Comportement / participation | Échelle + commentaire | Journée |
| Hygiène (couches, toilette) | Compteur ou case à cocher | Plusieurs fois par jour |
| Activités réalisées | Texte libre ou liste | Journée (souvent pour tout le groupe) |
| Commentaire libre | Texte | Journée |

Types de critères à prévoir : **échelle**, **choix unique**, **choix multiples**, **oui/non**, **heure ou plage horaire**, **nombre**, **texte libre**. Chaque critère a une **fréquence** (journée, demi-journée, par événement) et peut être activé selon la **tranche d'âge** (ex. couches seulement pour les poupons).

### 6.2 Saisie rapide

- Saisie **par groupe** : grille enfants × critères, avec valeurs pré-remplies et action « appliquer à tous » (ex. activité du matin).
- Saisie **par enfant** : fiche du jour d'un seul enfant.
- Pensée pour la **tablette** et une utilisation d'une seule main.
- Le parent voit les observations de la journée et le **mot du personnel** (commentaire libre adressé à la famille).
- Le parent reçoit le résumé de la journée (❓ en continu ou à heure fixe, ex. 16 h ?).

---

## 7. Communication parent ↔ équipe

- Un parent écrit **à l'équipe du groupe** de son enfant (pas à une personne en particulier, pour éviter que le message reste sans réponse quand quelqu'un est absent). ❓ Garder aussi la possibilité d'écrire à une éducatrice précise ?
- L'équipe peut répondre, et la direction peut voir les fils de son installation.
- Messages de **groupe** (annonces à tous les parents d'un groupe) et d'**installation** (fermeture, sortie, rappel).
- Pièces jointes (photos) : ❓ phase ultérieure, avec consentement photo par enfant.
- **Notifications** : courriel et notification web/mobile; préférences réglables par le parent.
- ❓ Heures de disponibilité de la messagerie (éviter les messages à 22 h aux éducatrices) ?

---

## 8. Dossier de l'enfant

### 8.1 Fiche

Identité, date de naissance, groupe, contacts d'urgence, personnes autorisées à venir chercher l'enfant, médecin, consentements (photos, sorties, crème solaire, etc.).

### 8.2 Santé et allergies — vue rapide

- **Allergies alimentaires** et autres (gravité, réaction, conduite à tenir, auto-injecteur).
- Conditions médicales et médicaments autorisés.
- Affichage **visible partout** où l'enfant apparaît (pastille sur la liste du groupe, sur la saisie des repas).
- ❓ Vue « cuisine » listant les allergies de tous les enfants présents du jour.

### 8.3 Incidents

- Déclaration rapide : type (blessure, chute, morsure, conflit/bagarre, malaise, autre), heure, lieu, description, soins donnés, témoins.
- **Notification au parent** et, selon la gravité, accusé de lecture ou signature.
- Historique des incidents visible sur la fiche, avec indicateur « incident aujourd'hui ».
- ❓ Les incidents impliquant deux enfants : comment informer chaque famille sans divulguer l'identité de l'autre enfant ?

### 8.4 Notes au dossier

- Notes datées et signées (auteur), classées par catégorie (développement, comportement, rencontre parent, santé…).
- Visibles par l'équipe seulement (éducatrices du groupe et direction), **jamais par les parents**. Ce qu'on veut partager avec la famille passe par un mot du personnel ou le journal de bord.
- Pas de suppression : modifications tracées.

---

## 9. Vie privée, sécurité et conformité (Loi 25)

Les données touchent des **mineurs** et incluent des **renseignements de santé** : à traiter comme sensibles dès le départ.

- **Accès minimal** : chaque rôle ne voit que ce dont il a besoin (section 3).
- **Journal d'audit** : qui a consulté ou modifié quoi, et quand (surtout santé, incidents, notes).
- **Consentements** explicites et révocables (photos, partage).
- **Conservation et suppression** : durée de conservation définie; procédure à la fin de l'inscription.
- **Hébergement** : idéalement au Canada / Québec; évaluation des facteurs relatifs à la vie privée (EFVP) si hébergement hors Québec.
- **Responsable de la protection des renseignements personnels** désigné par chaque organisation.
- Chiffrement en transit et au repos, authentification forte pour le personnel (❓ 2FA obligatoire pour la direction ?).
- Gestion des **incidents de confidentialité** (registre, avis à la Commission d'accès à l'information).

---

## 10. Autres points à considérer

- **Multi-établissement** : séparation stricte des données entre organisations (multi-locataire).
- **Langue** : français d'abord; anglais ❓.
- **Mobile** : application web responsive (PWA) au départ, applications natives ❓ plus tard.
- **Hors ligne** : la saisie en garderie doit tolérer une connexion Wi-Fi instable ❓.
- **Intégrations futures** : facturation, relevés fiscaux, rapports ministériels, menus.

---

## 11. Découpage proposé (MVP et phases)

### Phase 0 — Fondations
- Choix techniques (stack, hébergement), authentification, modèle multi-organisation.
- Gestion des organisations, installations, groupes, comptes et rôles.

### Phase 1 — MVP « une journée à la garderie »
- Fiche enfant avec contacts et **allergies bien visibles**.
- Liens parent ↔ enfant.
- **Présences** : arrivée/départ, tableau du groupe, validation de fin de journée.
- **Journal de bord** avec critères par défaut (humeur, sieste, appétit, comportement, commentaire) et saisie par groupe.
- Le parent consulte la journée de son enfant.

### Phase 2 — Communication et prévisions
- **Messagerie** parent ↔ équipe du groupe, annonces.
- **Prévisions de présence** par les parents et vue agrégée pour la direction.
- Notifications courriel / web.

### Phase 3 — Dossier et suivi
- **Incidents** avec notification au parent.
- **Notes au dossier** (internes, équipe seulement).
- **Critères d'observation configurables** par garderie.
- Journal d'audit consultable.

### Phase 4 — Plus tard
- Photos et consentements, mode hors ligne, rapports et exports, facturation, applications mobiles.

---

## 12. Questions ouvertes

1. Public cible au départ : CPE, garderies subventionnées, privées, milieux familiaux ? Une seule garderie pilote ?
2. Le parent peut-il pointer l'arrivée et le départ lui-même ?
3. Le résumé de la journée est-il envoyé en continu ou à heure fixe ?
4. Le parent écrit-il à l'équipe du groupe ou à une éducatrice précise ?
5. Quelles contraintes réglementaires de présence ou de rapport faut-il couvrir (ministère de la Famille) ?
6. Projet personnel, produit commercial, ou logiciel libre ?
7. Préférences techniques (langage, framework, hébergement) ?

---

## 13. Journal des décisions

| Date | Décision |
|---|---|
| 2026-11-25 | Création du plan initial. |
| 2026-11-25 | « Groupe » et « classe » sont synonymes; on utilise **groupe**. |
| 2026-11-25 | Les notes au dossier sont internes; les parents voient seulement les mots du personnel et les observations de la journée. |
