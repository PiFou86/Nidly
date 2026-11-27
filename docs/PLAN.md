# Nidly — Plan

> Document vivant. Il sert de point de départ et sera modifié au fur et à mesure.
> Le plan est organisé **par fonctionnalité**. Pour chacune : l'objectif, ce qui est **inclus**, ce qui est **hors périmètre** (les limites) et les **questions ouvertes** (❓).
>
> Dernière mise à jour : 2026-11-27

---

## 1. Vision

Nidly est un logiciel web qui relie **les parents**, **les éducatrices et éducateurs** et **la direction** d'une garderie autour du quotidien de l'enfant :

- savoir **qui est présent** (et qui est attendu) à tout moment;
- consigner **rapidement** comment s'est passée la journée de chaque enfant;
- **communiquer** simplement entre la famille et l'équipe éducative, y compris par des **photos, dessins et courtes vidéos**;
- avoir **sous la main** les informations critiques : allergies, incidents, notes au dossier.

Principes directeurs :

1. **Rapide pour l'éducatrice.** La saisie se fait en quelques touches, sur tablette ou téléphone, souvent pour tout un groupe d'un coup.
2. **Rassurant pour le parent.** Le parent voit la journée de son enfant et peut écrire à l'équipe sans friction.
3. **Configurable par garderie.** Chaque milieu choisit ses critères d'observation, ses horaires, ses règles de conservation.
4. **Respect de la vie privée dès la conception.** Les données concernent des enfants : accès minimal, traçabilité, hébergement et conservation conformes à la Loi 25.

---

## 2. Vocabulaire

| Terme | Définition |
|---|---|
| **Organisation** | L'entité juridique (ex. un CPE ou une entreprise qui exploite une ou plusieurs garderies). |
| **Installation** | Un lieu physique (bâtiment, adresse, permis). Une organisation peut en avoir plusieurs. |
| **Groupe** | Les enfants pris en charge ensemble dans une installation (ex. « Les Poussins », 18 mois–3 ans). « Classe » est un synonyme : on utilise **groupe** partout. |
| **Groupe d'attache** | Le groupe fixe de l'enfant. |
| **Groupe éphémère** | Un groupe formé pour un temps, en réunissant des enfants de plusieurs groupes d'attache quand il n'y a pas assez d'enfants (ex. début ou fin de journée, journée creuse). |
| **Fiche enfant** | Les informations administratives, médicales et de contact de l'enfant. |
| **Journal de bord** | Les observations quotidiennes saisies par l'équipe pour un enfant. |
| **Mot du personnel** | Un message ou commentaire de l'équipe adressé à la famille. |
| **Dossier de l'enfant** | Tout ce qui est rattaché à l'enfant. Il a une **partie partagée** (visible par les parents : journal, mots, médias partagés) et une **partie interne** (équipe seulement : notes au dossier). |
| **Média** | Une photo, une courte vidéo ou un document (PDF, dessin numérisé…). |

---

## 3. Rôles et permissions (transversal)

### 3.1 Rôles

- **Parent / tuteur** : voit uniquement ses propres enfants. Un enfant peut avoir **plusieurs tuteurs**, chacun avec **son propre compte** pour se connecter (garde partagée possible).
- **Ancien parent** : parent dont l'enfant ne fréquente plus le milieu. Accès en **lecture seule** à la partie partagée du dossier, pendant une durée configurable (voir F6).
- **Éducatrice / éducateur** : assigné(e) à une ou plusieurs installations, et à un ou plusieurs groupes.
- **Direction d'installation** : gère une installation (enfants, groupes, personnel, paramètres).
- **Administration de l'organisation** : gère l'ensemble des installations et les paramètres globaux.
- ❓ Rôles possibles plus tard : remplaçante, cuisine, éducatrice spécialisée, comptabilité.

### 3.2 Portée des accès

- un parent → ses enfants;
- une éducatrice → les enfants de ses groupes, dans ses installations (❓ lecture seule sur les autres groupes de l'installation, pour les remplacements ?);
- la direction → toute son installation;
- l'administration → toute l'organisation.

### 3.3 Matrice de permissions

Légende : ✅ permis · 👁️ lecture seule · ➖ ses propres enfants seulement · ❌ interdit

| Action | Parent | Éducatrice | Direction | Admin org. |
|---|:-:|:-:|:-:|:-:|
| Voir la fiche de l'enfant (contacts, santé) | ➖ | 👁️ | ✅ | ✅ |
| Modifier la fiche de l'enfant | ❓ ➖ (contacts) | ❌ | ✅ | ✅ |
| Déclarer les prévisions de présence | ➖ | ❌ | ✅ | ✅ |
| Saisir arrivée / départ | ❓ | ✅ | ✅ | ✅ |
| Valider les présences de la journée | ❌ | ✅ | ✅ | ✅ |
| Saisir le journal de bord | ❌ | ✅ | ✅ | ❌ |
| Lire le journal de bord | ➖ | ✅ | ✅ | 👁️ |
| Écrire à l'équipe d'un groupe | ➖ | ✅ | ✅ | ❌ |
| Déposer un média pour un enfant | ➖ (via message) | ✅ | ✅ | ❌ |
| Déposer un média pour un groupe | ❌ | ✅ | ✅ | ❌ |
| Voir les médias partagés | ➖ | ✅ | ✅ | 👁️ |
| Retirer un média | ❌ | ➖ (les siens) | ✅ | ✅ |
| Déclarer un incident | ❌ | ✅ | ✅ | ❌ |
| Voir les incidents | ➖ | ✅ | ✅ | ✅ |
| Notes au dossier | ❌ | ✅ (créer) | ✅ | 👁️ |
| Configurer critères, conservation, quotas | ❌ | ❌ | ✅ | ✅ |
| Gérer groupes et assignations | ❌ | ❌ | ✅ | ✅ |
| Gérer les installations | ❌ | ❌ | ❌ | ✅ |
| Consulter le journal d'audit | ❌ | ❌ | ✅ | ✅ |

---

## 4. Fonctionnalités

### F1. Organisations, installations, groupes et comptes

**Objectif.** Modéliser la structure réelle d'un milieu de garde et qui y travaille.

**Inclus**
- Une organisation possède une ou plusieurs installations; une installation a des groupes (capacité, tranche d'âge).
- Un enfant est inscrit dans une installation et rattaché à un **groupe d'attache** (fixe), avec un historique daté de ses changements de groupe d'attache.
- **Groupes éphémères** : quand il n'y a pas assez d'enfants, des enfants sont placés pour un temps dans un autre groupe. Le tableau des présences montre où se trouve chaque enfant à l'instant présent; le groupe d'attache ne change pas.
- Une éducatrice peut être assignée à plusieurs installations et plusieurs groupes, avec un rôle par installation.
- Invitation des comptes (parents, personnel) par courriel; liens parent ↔ enfant.
- **Plusieurs tuteurs par enfant**, chacun avec son compte et ses préférences de notification. Un même tuteur peut être lié à plusieurs enfants (fratrie).
- Fin d'inscription d'un enfant : la date de départ fait passer les parents en « ancien parent ».

**Hors périmètre**
- Gestion des horaires de travail du personnel, paie.
- Inscription en ligne et liste d'attente.

**❓ Questions**
- Affichage des ratios éducatrice/enfants en temps réel ?

---

### F2. Fiche enfant, santé et allergies

**Objectif.** Avoir les informations critiques de l'enfant visibles en un coup d'œil.

**Inclus**
- Identité, date de naissance, groupe, contacts d'urgence, personnes autorisées à venir chercher l'enfant, médecin.
- Consentements (photos, sorties, crème solaire…), datés et révocables.
- Allergies (gravité, réaction, conduite à tenir, auto-injecteur), conditions médicales, médicaments autorisés.
- **Pastille allergie** partout où l'enfant apparaît (liste du groupe, saisie des repas).

**Hors périmètre**
- Gestion de l'administration de médicaments (registre de doses).
- Dossier médical complet.

**❓ Questions**
- Le parent peut-il modifier lui-même les contacts ?
- Vue « cuisine » listant les allergies des enfants présents du jour ?

---

### F3. Présences et prévisions

**Objectif.** Savoir qui est attendu, qui est là, et garder un registre fiable.

**Inclus**
- **Prévisions** par le parent : horaire récurrent et exceptions (absence, arrivée tardive, départ hâtif, vacances).
- Vue agrégée des prévisions pour la direction (enfants attendus par groupe et par plage horaire).
- **Présences réelles** : arrivée et départ saisis par l'éducatrice.
- **Tableau du groupe** : attendus / arrivés / partis / absents; écarts prévu/réel mis en évidence.
- **Validation** de fin de journée; corrections ensuite tracées.

**Hors périmètre**
- Facturation basée sur les présences.
- Borne physique ou lecteur de cartes à l'entrée.

**❓ Questions**
- Le parent peut-il pointer l'arrivée et le départ lui-même ?
- Délai limite pour modifier une prévision (ex. la veille à 18 h) ?
- Le parent peut-il indiquer qui viendra chercher l'enfant ce jour-là ?
- Exports pour le ministère de la Famille ?

---

### F4. Journal de bord quotidien

**Objectif.** Consigner rapidement la journée de chaque enfant et la partager avec la famille.

**Inclus**
- **Critères configurables** par installation ou organisation, avec suggestions par défaut :

| Critère | Type de réponse | Fréquence suggérée |
|---|---|---|
| Humeur | Échelle (😀 🙂 😐 🙁 😢) | Matin / après-midi |
| Sieste / sommeil | Heure de début, de fin, qualité | Par sieste |
| Appétit (dîner, collations) | Échelle (tout / un peu / rien) | Par repas |
| Comportement / participation | Échelle + commentaire | Journée |
| Hygiène (couches, toilette) | Compteur ou case à cocher | Plusieurs fois par jour |
| Activités réalisées | Texte ou liste | Journée (souvent pour tout le groupe) |
| Mot du personnel | Texte | Journée |

- Types de critères : échelle, choix unique, choix multiples, oui/non, heure ou plage, nombre, texte libre. Fréquence (journée, demi-journée, par événement) et activation par tranche d'âge.
- **Saisie par groupe** (grille enfants × critères, « appliquer à tous ») et **saisie par enfant**, pensées pour la tablette.
- Le parent voit les observations et le mot du personnel.

**Hors périmètre**
- Évaluation du développement ou portfolio pédagogique structuré.

**❓ Questions**
- Le résumé est-il visible en continu ou publié à heure fixe (ex. 16 h) ?

---

### F5. Communication parent ↔ équipe

**Objectif.** Permettre des échanges simples et traçables entre la famille et l'équipe.

**Inclus**
- Le parent écrit **à l'équipe du groupe** de son enfant; l'équipe répond; la direction voit les fils de son installation.
- Le personnel (éducatrices, direction) choisit le **destinataire** d'un message :
  - **le groupe** : tous les tuteurs de tous les enfants du groupe;
  - **l'enfant** : l'ensemble de ses tuteurs;
  - **un tuteur en particulier** : seul ce tuteur voit le message et la conversation.
- Annonces de **groupe** et d'**installation** (fermeture, sortie, rappel).
- **Pièces jointes** (photos, vidéos, documents) dans les deux sens, versées au dossier de l'enfant (voir F6).
- Notifications courriel et web, préférences réglables par le parent.

**Hors périmètre**
- Appels audio ou vidéo, clavardage en direct avec indicateur « en train d'écrire ».
- Messagerie entre parents.

**❓ Questions**
- Garder aussi la possibilité d'écrire à une éducatrice précise ?
- Quand un tuteur écrit à l'équipe, sa conversation est-elle visible par les autres tuteurs de l'enfant, ou seulement par lui ?
- Garde partagée avec restrictions (ex. ordonnance du tribunal) : faut-il pouvoir limiter ce qu'un tuteur voit ou reçoit ?
- Plages horaires de la messagerie (éviter les notifications à 22 h au personnel) ?

---

### F6. Médias et documents du dossier

**Objectif.** Partager photos, dessins, courtes vidéos et documents avec la famille, en toute sécurité, et les conserver dans le dossier de l'enfant.

**Inclus**
- **Types de médias** : photos, courtes vidéos, documents (PDF, dessin numérisé…).
- **Trois façons de déposer**, qui aboutissent toutes au dossier de l'enfant :
  1. depuis une **communication** (mot du personnel, message, journal de bord) que les parents voient;
  2. directement dans le **répertoire de documents** de l'enfant;
  3. pour **tout un groupe** : l'éducatrice dépose une fois et le média apparaît dans la partie partagée du dossier de **tous les enfants du groupe** (ex. photo de l'activité, sortie), présents ou non ce jour-là. « Groupe » veut dire ici le **groupe d'attache**, à la date de publication : un enfant qui arrive plus tard dans le groupe ne voit pas les anciennes photos, un enfant qui change de groupe garde celles de sa période.
- **Consentement photo** : au dépôt d'un média de groupe, l'application signale les enfants du groupe sans consentement photo, pour que l'éducatrice vérifie avant de publier (règle exacte à décider, voir questions).
- **Répertoire de l'enfant** : vue chronologique, filtres par type et par période, téléchargement par le parent.
- **Accès après le départ** : les anciens parents gardent un accès en lecture seule à la partie partagée pendant une durée **configurable par le milieu** (par défaut **1 an**, réglable en années). Rappel envoyé avant la fin de l'accès, avec **téléchargement de l'ensemble en archive** (.zip).
- À la fin de la durée : retrait de l'accès, puis suppression des médias selon la règle de conservation du milieu.

**Sécurité des fichiers déposés** (tout dépôt peut venir d'un compte usurpé)
- **Liste blanche de formats** (ex. JPEG, PNG, HEIC, MP4, PDF), vérifiés par le contenu réel du fichier et non par l'extension.
- **Taille maximale** par fichier et **durée maximale** des vidéos (ex. 60 s ❓); **quota** de stockage par installation.
- **Analyse antivirus** de chaque fichier (ex. ClamAV) : le fichier reste **en quarantaine**, invisible, tant que l'analyse n'est pas passée; rejet et alerte à la direction si suspect.
- **Réencodage** des images et vidéos et **retrait des métadonnées** (position GPS, appareil) avant publication; les PDF sont aplatis ou convertis en aperçu ❓.
- Stockage **privé** hors du serveur web, liens de téléchargement **signés et temporaires**, jamais de lien public.
- **Limite de débit** des dépôts par compte, journal d'audit des dépôts, consultations et téléchargements.
- Possibilité pour la direction de **retirer** un média et de suspendre un compte.

**Hors périmètre**
- Reconnaissance faciale ou floutage automatique des visages.
- Partage public, lien externe, publication sur les réseaux sociaux.
- Diffusion vidéo en direct (caméras).
- Retouche ou montage dans l'application.
- Empêcher les captures d'écran ou la rediffusion par un parent (impossible techniquement : on affiche plutôt un rappel des conditions d'utilisation).

**❓ Questions**
- Photo prise pendant un **groupe éphémère** : proposition par défaut, elle va aux enfants présents dans le groupe éphémère, et l'éducatrice peut ajuster la liste avant de publier. À confirmer.
- Si un enfant sans consentement apparaît sur une photo de groupe : on bloque le dépôt, ou l'éducatrice confirme qu'il n'y figure pas ?
- Les parents peuvent-ils déposer dans le répertoire, ou seulement via un message ?
- Faut-il aussi des documents **internes** (équipe seulement), rattachés aux notes au dossier ?
- Durée maximale des vidéos et quota par installation ?
- Après la fin de l'accès des anciens parents : suppression immédiate ou archivage interne pour une durée légale ?

---

### F7. Incidents

**Objectif.** Déclarer rapidement un incident et en informer la famille.

**Inclus**
- Déclaration : type (blessure, chute, morsure, conflit/bagarre, malaise, autre), heure, lieu, description, soins donnés, témoins, photo ❓.
- Notification au parent et, selon la gravité, accusé de lecture ou signature.
- Historique sur la fiche, indicateur « incident aujourd'hui ».

**Hors périmètre**
- Déclarations officielles à la CNESST ou au ministère (export possible plus tard).

**❓ Questions**
- Incident impliquant deux enfants : comment informer chaque famille sans divulguer l'identité de l'autre enfant ?

---

### F8. Notes au dossier

**Objectif.** Garder un suivi interne de l'enfant pour l'équipe.

**Inclus**
- Notes datées et signées, classées par catégorie (développement, comportement, rencontre parent, santé…).
- **Internes seulement** (éducatrices du groupe et direction), **jamais visibles par les parents**.
- Pas de suppression : modifications tracées.

**Hors périmètre**
- Plan d'intervention structuré (pourra venir plus tard).

---

## 5. Exigences transversales

### 5.1 Vie privée et Loi 25

- Accès minimal par rôle et par portée (section 3).
- **Journal d'audit** : qui a consulté, déposé ou modifié quoi, et quand.
- **Consentements** explicites et révocables (photos, partage).
- **Conservation configurable** par milieu, avec suppression ou anonymisation à échéance.
- **Hébergement** au Canada idéalement; évaluation des facteurs relatifs à la vie privée (EFVP) si hors Québec.
- **Responsable de la protection des renseignements personnels** désigné par organisation.
- Gestion des **incidents de confidentialité** (registre, avis à la Commission d'accès à l'information).

### 5.2 Sécurité

- Chiffrement en transit et au repos.
- Authentification forte pour le personnel (❓ 2FA obligatoire pour la direction ?).
- Séparation stricte des données entre organisations (multi-locataire).
- Sécurité des fichiers déposés (voir F6).

### 5.3 Autres

- **Langue** : français d'abord; anglais ❓.
- **Mobile** : application web responsive (PWA) au départ; applications natives ❓ plus tard.
- **Hors ligne** : tolérer un Wi-Fi instable pour la saisie ❓.

---

## 6. Choix techniques

### 6.1 Décidé

- **Backend : .NET 10** (ASP.NET Core). .NET 10 est une version LTS, supportée jusqu'en novembre 2028.

### 6.2 Base de données — à trancher

**Recommandation : PostgreSQL**, avec Entity Framework Core (fournisseur Npgsql).

- Gratuit et libre, sans coût de licence quand le nombre d'installations augmente.
- **Row-Level Security** : la base elle-même peut empêcher une organisation de voir les données d'une autre (multi-locataire, section 5.2), en plus des contrôles du code.
- **JSONB** : pratique pour stocker les réponses aux critères configurables du journal de bord (F4), qui varient d'une garderie à l'autre.
- Offert en service géré dans les régions canadiennes des grands hébergeurs (Azure Canada Central, AWS ca-central-1, et d'autres), ce qui aide pour la Loi 25.
- Très bien supporté par EF Core et par .NET Aspire pour le développement local.

Alternatives :
- **SQL Server / Azure SQL** : l'intégration la plus naturelle avec .NET et l'outillage Microsoft, et des tables temporelles utiles pour l'historique. En contrepartie, la licence ou le service géré coûtent plus cher.
- **SQLite** : seulement pour les tests ou une démo locale, pas pour la production multi-garderie.

Dans tous les cas, les **fichiers (F6)** ne vont pas dans la base, mais dans un stockage objet privé hébergé au Canada (Azure Blob Storage ou S3 compatible), la base ne gardant que les métadonnées.

### 6.3 Frontend — à trancher

Contraintes qui pèsent dans le choix : saisie rapide sur **tablette**, Wi-Fi parfois instable en garderie, **PWA** (installable, notifications), prise de photos et vidéos, et peut-être une application mobile plus tard.

**Recommandation : React + TypeScript** (Vite), en PWA, qui consomme une API ASP.NET Core.

- Le meilleur écosystème pour les PWA, le mode hors ligne (service workers, file d'attente de saisies) et l'accès à la caméra.
- Chemin simple vers une application mobile plus tard (Capacitor ou React Native) en réutilisant le code.
- Grand choix de composants accessibles et adaptés au tactile.
- En contrepartie : deux langages (C# et TypeScript); on génère le client TypeScript à partir de la spécification OpenAPI de l'API pour limiter la duplication.

Alternatives :
- **Blazor WebAssembly (.NET 10)** : tout en C#, modèles et validations partagés avec le backend. C'est le choix le plus productif si on veut rester dans un seul langage. Limites : premier téléchargement plus lourd sur tablette, mode hors ligne et écosystème de composants moins riches. À éviter en mode *Blazor Server*, qui exige une connexion permanente (mauvais avec un Wi-Fi instable).
- **Vue 3 + TypeScript** : mêmes avantages que React pour la PWA, avec une courbe d'apprentissage souvent jugée plus douce; écosystème mobile un peu plus restreint.

### 6.4 Autres briques à prévoir

- **Authentification** : ASP.NET Core Identity ou un fournisseur OpenID Connect; 2FA pour le personnel.
- **Tâches de fond** : analyse antivirus (ClamAV en conteneur), réencodage des médias, notifications, purge à échéance (services hébergés .NET ou Hangfire).
- **Temps réel** : SignalR pour la messagerie et le tableau des présences.
- **Développement local** : .NET Aspire pour lancer l'API, la base, le stockage et ClamAV ensemble.

---

## 7. Découpage proposé (MVP et phases)

| Phase | Contenu |
|---|---|
| **0 — Fondations** | Choix techniques, authentification, multi-organisation, F1. |
| **1 — MVP « une journée à la garderie »** | F2 (fiche et allergies), F3 (présences réelles), F4 (journal avec critères par défaut). |
| **2 — Communication** | F5 (messagerie, annonces, notifications), F3 (prévisions des parents). |
| **3 — Médias** | F6 (dépôt sécurisé, répertoire, médias de groupe, accès après départ). |
| **4 — Dossier et suivi** | F7 (incidents), F8 (notes au dossier), critères configurables, journal d'audit consultable. |
| **Plus tard** | Hors ligne, rapports et exports, facturation, applications mobiles. |

❓ Les médias (F6) sont un attrait fort pour les parents : faut-il les remonter avant les incidents ?

---

## 8. Questions ouvertes générales

1. Public cible au départ : CPE, garderies subventionnées, privées, milieux familiaux ? Une garderie pilote ?
2. Contraintes réglementaires de présence ou de rapport (ministère de la Famille) ?
3. Projet personnel, produit commercial, ou logiciel libre ?
4. Base de données et frontend : voir les recommandations de la section 6.
5. Hébergeur (Azure, AWS, hébergeur québécois) ?

Les questions propres à chaque fonctionnalité sont dans sa section.

---

## 9. Journal des décisions

| Date | Décision |
|---|---|
| 2026-11-25 | Création du plan initial. |
| 2026-11-25 | « Groupe » et « classe » sont synonymes; on utilise **groupe**. |
| 2026-11-25 | Les notes au dossier sont internes; les parents voient seulement les mots du personnel et les observations de la journée. |
| 2026-11-25 | Ajout des médias (photos, vidéos, documents) au dossier, avec médias de groupe, analyse des fichiers et accès des anciens parents pendant une durée configurable (1 an par défaut). |
| 2026-11-25 | Plan réorganisé par fonctionnalité (inclus / hors périmètre / questions). |
| 2026-11-25 | Un média de groupe est accessible à tous les enfants du groupe. |
| 2026-11-25 | Chaque enfant a un groupe d'attache fixe, et peut être placé dans un groupe éphémère quand il n'y a pas assez d'enfants. |
| 2026-11-27 | Un enfant peut avoir plusieurs tuteurs, chacun avec son compte. Le personnel peut écrire au groupe, à l'enfant (tous ses tuteurs) ou à un tuteur en particulier. |
| 2026-11-27 | Backend en .NET 10. Base de données et frontend à trancher (section 6). |
