# Formulaire Tally — Adhésion Commission Formation & Talent Tech

> Spécification clé en main. Créer le formulaire sur https://tally.so (compte gratuit suffisant),
> puis copier-coller chaque bloc ci-dessous. Temps estimé : 10-12 minutes.

---

## 1. Création

1. Aller sur **tally.so** → Se connecter (Google) → **+ New form** → « Start from blank »
2. Tout se construit en tapant `/` pour insérer un bloc (comme Notion)

---

## 2. Titre et introduction du formulaire

**Titre :**
```
Rejoindre la Commission Formation & Talent Tech — APEBI
```

**Texte d'introduction (bloc Text) :**
```
La commission sectorielle Formation & Talent Tech de l'APEBI recrute ses membres
actifs pour le mandat 2026–2028. Notre mission : transformer le capital humain
marocain en avantage compétitif national.

Ce formulaire prend 3 minutes. Les candidatures sont examinées au fil de l'eau
et chaque candidat reçoit une réponse sous 10 jours.

⚠️ Être membre actif implique un engagement réel : plénière mensuelle (90 min),
participation à un sous-groupe de travail, livrables. La charte d'engagement
détaillée est téléchargeable sur notre page de présentation.
```

---

## 3. Champs (dans l'ordre)

| # | Question | Type de bloc Tally | Obligatoire | Options / détails |
|---|----------|--------------------|-------------|-------------------|
| 1 | Prénom | Short answer | ✅ | — |
| 2 | Nom | Short answer | ✅ | — |
| 3 | Email professionnel | Email | ✅ | — |
| 4 | Téléphone (WhatsApp de préférence) | Phone number | ✅ | Indicatif +212 par défaut |
| 5 | Entreprise / Organisation | Short answer | ✅ | — |
| 6 | Fonction actuelle | Short answer | ✅ | Placeholder : « ex. DRH, CTO, Directeur pédagogique… » |
| 7 | Profil LinkedIn | Link/URL | ⬜ | — |
| 8 | Vous représentez | Dropdown | ✅ | Voir options A ci-dessous |
| 9 | Votre entreprise est-elle membre APEBI ? | Multiple choice | ✅ | Oui / Non / Je ne sais pas |
| 10 | Rôle(s) qui vous intéresse(nt) | Checkboxes | ✅ | Voir options B ci-dessous |
| 11 | Axe(s) de travail préféré(s) | Checkboxes | ✅ | Voir options C ci-dessous |
| 12 | Votre motivation | Long answer | ✅ | Placeholder : « En quelques lignes : pourquoi cette commission, et ce que vous pouvez y apporter concrètement. » |
| 13 | Disponibilité mensuelle estimée | Multiple choice | ✅ | Voir options D ci-dessous |
| 14 | J'ai pris connaissance de l'exigence d'engagement actif (charte à signer à l'intégration) | Checkbox (consentement) | ✅ | Une seule case |

### Options A — « Vous représentez » (Dropdown)
```
Une entreprise tech / éditeur de logiciels
Une startup ou PME numérique
Un grand groupe utilisateur de technologies
Une université / école d'ingénieurs
Un bootcamp / organisme de formation privé
Une institution publique
Une association professionnelle ou étudiante
Autre
```

### Options B — « Rôle(s) qui vous intéresse(nt) » (Checkboxes)
```
Responsable Observatoire (profil Data / RH senior)
Responsable Label Qualité (profil Formation + pédagogie)
Responsable Employabilité (profil DRH grands groupes IT)
Responsable Plaidoyer (profil expert politique publique)
Membre représentant entreprise
Membre représentant organisme de formation
Membre représentant étudiants
Contributeur ponctuel / à discuter
```

### Options C — « Axe(s) de travail préféré(s) » (Checkboxes)
```
A. Observatoire des Talents (Baromètre Talents Tech Maroc)
B. Label APEBI Tech Talent (qualité des formations)
C. Tech Talent Bridge (mise en relation talents ↔ entreprises)
D. Plaidoyer & Influence (politique de formation nationale)
```

### Options D — « Disponibilité mensuelle » (Multiple choice)
```
2 à 4 heures / mois (plénière + suivi)
4 à 8 heures / mois (plénière + sous-groupe actif)
8 heures et plus / mois (rôle de responsable d'axe possible)
```

---

## 4. Message de confirmation (après soumission)

Settings → « Thank you page » → personnaliser :
```
Merci pour votre candidature ! 🎉

Votre profil sera examiné par le VP de la commission sous 10 jours.
Vous recevrez une réponse par email, suivie d'un échange si votre profil correspond.

En attendant : téléchargez le livre blanc et la charte d'engagement sur la page
de présentation de la commission.
```

---

## 5. Paramètres à activer (Settings du formulaire)

| Paramètre | Valeur |
|-----------|--------|
| **Email notifications** → Self notifications | ✅ ON → o.mazouzi.pro@gmail.com (notification à chaque candidature) |
| **Respondent notifications** | ✅ ON (accusé de réception automatique au candidat) |
| Langue du formulaire | Français |
| Captcha | ✅ ON (anti-spam) |
| Close date | OFF (recrutement au fil de l'eau) |

**Style (optionnel, plan Pro non requis) :** couleur d'accent `#00AFD2` (Cyan APEBI) si l'option est disponible en gratuit.

---

## 6. Récupérer le FORM_ID et l'activer sur la landing

1. Cliquer **Publish** → copier le lien de partage, format : `https://tally.so/r/XXXXXX`
2. Le `FORM_ID` = la partie `XXXXXX` après `/r/`
3. Dans `index.html` (bloc CONFIG en haut du body) :
   ```js
   TALLY_FORM_ID: "XXXXXX",
   ```
4. Commit + push :
   ```bash
   cd 06_OnePager
   git add index.html && git commit -m "config: activation formulaire Tally" && git push
   ```
5. Le bouton « Devenir membre de la commission » ouvrira automatiquement le formulaire Tally
   (au lieu de l'email pré-rempli actuel).

---

## 7. Gestion des candidatures

- Tableau de bord Tally → onglet **Submissions** : toutes les réponses, export CSV possible
- Recommandation : trier chaque candidature sous 10 jours (engagement annoncé dans le formulaire)
- À l'acceptation : envoyer la charte d'engagement (`docs/charte-engagement-membre-v1.docx`) pour signature
- Reporter les membres confirmés dans `STATUS_C5.md` (tableau Membres) et sur la landing (section Équipe : passer la carte de `Poste ouvert` à `Confirmé`)
