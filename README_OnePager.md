# 06_OnePager — Landing page Commission Formation & Talent Tech

> Landing page complète de la commission : présentation, annonces, événements,
> recrutement (enroll), ressources téléchargeables et prise de contact.

---

## Fichiers

| Fichier | Description |
|---------|-------------|
| `index.html` | Landing page complète (standalone — ouvrir dans un navigateur) |
| `docs/presentation-commission-v1.pdf` | Présentation institutionnelle (téléchargeable depuis la page) |
| `docs/dossier-presentation-v2.pdf` | Dossier de présentation synthétique (v2 : mise en page corrigée) |
| `docs/livre-blanc-v1.pdf` | Livre blanc complet |
| `docs/charte-engagement-membre-v1.pdf` | Charte d'engagement membre |
| `docs-src/*.html` | Sources HTML des PDF générés (dossier de présentation, livre blanc) |

⚠️ Le dossier `docs/` doit rester à côté du HTML (liens relatifs).
⚠️ Tous les documents téléchargeables sont au format PDF (décision 2026-06-11 — plus de DOCX).

**Régénérer un PDF depuis sa source HTML** (après modification dans `docs-src/`) :
```powershell
& "C:\Program Files\Google\Chrome\Application\chrome.exe" --headless --no-pdf-header-footer `
  --print-to-pdf="docs/<nom>-vN.pdf" "docs-src/<nom>.html"
```

---

## Structure de la page (12 sections + CTA)

| # | Section | Ancre |
|---|---------|-------|
| 01 | Contexte & enjeux (3 fractures) | `#contexte` |
| 02 | Mission | `#mission` |
| 03 | Vision 2028 & ambitions | `#vision` |
| 04 | 4 axes stratégiques | `#axes` |
| 05 | Premières actions 90 jours | `#actions` |
| 06 | **Annonces & actualités** *(nouveau)* | `#annonces` |
| 07 | **Événements à venir** *(nouveau)* | `#evenements` |
| 08 | Parties prenantes | — |
| 09 | Impact attendu & KPIs | — |
| 10 | Gouvernance | — |
| 11 | **Équipe & profils recherchés** *(nouveau)* | `#equipe` |
| 12 | **Ressources & documents** *(nouveau)* | `#ressources` |
| — | CTA Rejoindre (boutons fonctionnels) | `#rejoindre` |
| — | Footer Connect (email, LinkedIn, WhatsApp, partage) | — |

**Fonctionnalités interactives :**
- Navigation sticky (9 ancres) + barre de progression scroll
- Sticky CTA bar (apparaît au scroll, masquée sur la section Rejoindre et sur mobile)
- Boutons « Devenir membre » / « Nouer un partenariat » → email pré-rempli structuré
- 4 documents téléchargeables (attribut `download`)
- Bouton « Partager cette page » (Web Share API mobile + copie de lien desktop)
- Print CSS : les éléments sticky sont masqués à l'impression, contact affiché en texte

---

## ⚙️ Configuration — bloc CONFIG (en haut du HTML)

Toutes les variables modifiables sont regroupées dans un seul bloc `<script>` au début du `<body>` :

```js
const CONFIG = {
  EMAIL_VP: "o.mazouzi.pro@gmail.com",   // email de contact
  WHATSAPP_URL: "",                       // lien groupe WhatsApp (bouton masqué tant que vide)
  TALLY_FORM_ID: "",                      // ID formulaire Tally (fallback email tant que vide)
  LINKEDIN_VP: "https://www.linkedin.com/in/oualidmazouzi/"
};
```

**Comportements automatiques :**
- `TALLY_FORM_ID` vide → le bouton « Devenir membre » ouvre un email pré-rempli structuré.
  Renseigné → il ouvre le formulaire Tally (`tally.so/r/FORM_ID`).
- `WHATSAPP_URL` vide → le bouton WhatsApp du footer est masqué.
  Renseigné → il apparaît automatiquement.

---

## Mises à jour courantes

| Quoi | Où |
|------|-----|
| Ajouter une annonce | Section `#annonces` — dupliquer une `<div class="card annonce-card">` |
| Ajouter un événement | Section `#evenements` — dupliquer une `<div class="card event-card">` |
| Marquer un poste pourvu | Section `#equipe` — changer `p-status open` en `p-status taken` + ajouter le nom |
| Nouveau document | 1. Déposer dans `docs/` avec suffixe `-vN` · 2. Dupliquer une `res-card` |
| Mettre à jour un document | Créer une **nouvelle version** (`-v2`) — ne jamais écraser (cache) |

---

## Déploiement Vercel (prochaine étape — plan CEO 2026-06-10)

**🌐 SITE EN LIGNE : https://commission-formation-talent-apebi.vercel.app** ✅ (déployé 2026-06-10)
**Repo GitHub : https://github.com/Lemaaz/commission-formation-talent-apebi** ✅ (créé 2026-06-10, branche `main`)
**Auto-deploy actif** : chaque push sur `main` redéploie automatiquement le site.
Ce dossier EST le repo — tout commit pushé sur `main` se déploiera automatiquement une fois Vercel connecté.

1. ~~Créer un repo GitHub~~ ✅ Fait
2. Connecter le repo à vercel.com → déploiement automatique
3. Créer le formulaire Tally → renseigner `TALLY_FORM_ID` dans CONFIG (puis commit + push)
4. Créer le groupe WhatsApp → renseigner `WHATSAPP_URL` dans CONFIG (puis commit + push)
5. Demander le sous-domaine `formation.apebi.org.ma` (décision Binôme B-06, non bloquant)

```bash
# Workflow de mise à jour :
cd 06_OnePager
# ... éditer index.html ...
git add index.html && git commit -m "maj: ..." && git push
```

---

## Historique

- **2026-06-10 (v2)** : ajout des 4 sections (annonces, événements, équipe, ressources),
  navigation sticky, sticky CTA bar, progress bar, CTA fonctionnels (les boutons étaient morts),
  retrait du lien annexe cassé (404), footer Connect, partage social, print CSS étendu.
  QA navigateur réel : 0 erreur console, mobile/desktop/print OK.
- **v1** : one-pager initial 9 sections (designé via Claude Design).
