# Journal des versions — widgets Grist « Budget DSI »

Règles du jeu :
- **Une entrée par modification**, ajoutée en tête de ce fichier et commitée avec le widget modifié.
- Chaque widget porte un numéro de version dans l'URL configurée côté Grist (`?v=N`) :
  incrémenter à chaque commit pour contourner le cache de GitHub Pages (~10 min).
- **Rollback d'un widget** : GitHub → le fichier → *History* → ouvrir la version voulue →
  *…* → *View file* → copier le contenu → recommitter (ou bouton *Revert* sur le commit).
  Puis incrémenter `?v=` dans Grist pour forcer le rechargement.
- **Rollback du document Grist** (tables, colonnes, données) : menu ⚙ → *Historique du
  document* → choisir l'instantané ou l'action → *Restaurer*. Avant toute modification de
  structure importante, faire une copie : menu du document → *Dupliquer* (copie datée dans
  l'espace de travail).

---

## 2026-09-01

- **prepa-dsi v3** — Rapprochement budgétaire corrigé (état 189 : « Gestionnaire » = enveloppe
  D100/I261/D300 ; clé = enveloppe + nature [+ opération], repli sur le champ Enveloppe du
  contrat). Lignes budgétaires **dépliables** au clic : contrats associés (fournisseur, objet,
  statut, prix) triés par montant.
- **nav-dsi v10, reports-dsi v2, prepa-dsi v2** — Plus aucune année en dur : exercice de
  référence déduit des données (colonne Exercice, valeur majoritaire) ou de la date du jour ;
  N−1 / N+1 recalculés ; `?annee=` pour forcer ; bandeau `?titre=` personnalisable.
- **prepa-dsi v1, echeancier-dsi v1** — Nouvelle page « Prépa budget » : projection N+1 par
  ligne budgétaire (tuiles Total / Renouvelés / À arbitrer / Économies) + échéancier des
  renouvellements (tri par échéance, badge échu / J−n).
- **nav-dsi v9** — Onglets additionnels paramétrables : `?tabs=<page>|<libellé>|<icône>,…`
  (utilisé pour 📋 Contrats puis 🎯 Prépa budget). Plus de modification de fichier pour
  ajouter une page.
- **nav-dsi v8, pie-dsi v9** — Plan B de détection du document sans jeton d'accès
  (origine du référent + getDocName) : la navigation fonctionne aussi en accès anonyme.
- **nav-dsi v7** — Nouvelles icônes : 💶 Factures, 🛒 Engagements & BC, 🤝 Marchés,
  🚚 Fournisseurs, ⏩ Reports.
- **nav-dsi v6** — N° de la page Reports paramétrable (`?reports=N`) ; pastille de diagnostic
  (verte = document hôte détecté, rouge = cause au survol) ; échecs de détection jamais mis
  en cache, délai max 4 s.
- **nav-dsi v5** — Correctif majeur : chargement de `grist-plugin-api.js` (oublié en v3/v4,
  la navigation était muette) ; pré-chargement de l'URL du document au démarrage.
- **reports-dsi v1** — Page « Reports » : entrants N−1→N (colonne Reports de l'état 189),
  à reporter vers N+1 (ENS investissement), à solder (ENS fonctionnement).

## 2026-08-29 et avant

- **nav-dsi v3-v4** — Passage au 100 % générique : auto-détection du document hôte
  (getAccessToken), plus aucune URL codée en dur ; `?base=` en surcharge.
- **pie-dsi v7** — Générique (auto-détection) ; clic → page Factures filtrée via localStorage.
- **etats-dsi v3** — Sélecteur d'états : colonnes nb/montant alignées.
- **etats-dsi v2** — Source = table Factures + setSelectedRows (corrige le filtrage par
  row id) ; bouton « Tous les états » (retour à aucun filtre).
- **pie-dsi v3-v6** — Camembert adaptatif (jamais tronqué), % dans les parts, clic filtrant.
- **nav-dsi v2** — Hauteur de barre fixe 48 px (rendu identique quelle que soit la hauteur
  de section).
- **kpi-dsi v1** — 6 tuiles KPI style « cards » (3 styles disponibles via `?style=`).
- **table-dsi v1** — Matrice des lignes budgétaires (tri, recherche, jauge de taux, alertes).
- **axes-dsi v1** — Top des axes en barres cumulées (mandaté + ENS vs budgété).
- **nav-dsi v1 / pie-dsi v1** — Premières versions (URLs alors codées en dur).
