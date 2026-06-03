# CHANGELOG — Vigie V1.1

## Statut

Version : **V1.1 — FINAL**  
Date de validation : juin 2025  
Fichier de production : `index.html`  
Archive figée : `archives/VIGIE_V1.1_FINAL.html`

---

## Nouvelles fonctionnalités

### 1. Logique de session

- Remplacement de la logique "ronde unique" par une logique de **session de travail**.
- **Démarrage** : passage obligatoire par EPI et consigne de déplacement.
- **Reprise** : accès direct au menu des contrôles sans rejouer les étapes de sécurité.
- **Fin de session** : réinitialisation complète et retour à l'accueil.
- Persistance en `localStorage` : la session survit au rechargement de page.

### 2. Menu "Choix des contrôles" — tableau de bord

- Remplace l'ancien écran de choix statique.
- Chaque contrôle affiche sa **progression individuelle** (barre + pourcentage + statut).
- Statuts possibles : *Non commencé* / *[équipement] en cours* / *Terminé ✓*.
- Reprise intelligente : clic sur une carte = reprise exactement là où l'utilisateur s'est arrêté.
- Bouton **Fin de session** en bas du menu.

### 3. Ronde du Général (nouveau module)

- 3 zones : A (Goulotte T4), B (Goulotte T8), C (Goulotte T3 + T6).
- Bannière **Vigilance accrue** avec points critiques par zone.
- 3 états au clic : 🟢 RAS / 🟡 À surveiller / 🔴 Intervention nécessaire.
- Chips de motifs contextuels selon l'état sélectionné.
- Commentaire facultatif par zone.
- Résumé final par zone avec motifs et commentaires.

### 4. Graisseurs automatiques — évolutions

- Ajout du convoyeur **TC** entre T5 et T6 (série T complète : T1–T5, TC, T6–T8).
- Total : **52 graisseurs** (36 série T + 16 série OVB).
- Nouveau visuel OVB : **deux chevrons /\\ superposés** au centre du rectangle pour distinguer visuellement l'overband du convoyeur classique.

### 5. Contrôle lames goulottes (nouveau module)

- 3 goulottes : T3 (5 lames), T4 (10 lames), T7 (5 lames).
- Représentation **ligne unique** fidèle à la disposition terrain.
- Clic direct sur la lame observée, cycle ⚪ → 🟢 → 🟡 → 🔴 → ⚪.
- Résumé avec compteurs et visualisation icônes par goulotte.

### 6. Contrôle usure tapis (nouveau module)

- **13 équipements** : T1–T8, TC (9 convoyeurs) + OVB1–4 (4 overbands).
- Critères convoyeurs : Usure de la bande / Déchirure / Centrage.
- Critères overbands : idem + Lattes.
- Résumé détaillé par équipement avec valeur par critère.

### 7. Bouton Home 🏠

- Visible sur tous les écrans opérationnels (Général, Graisseurs, Lames, Usure, Résumés).
- **Absent** sur EPI et Consigne : les étapes de sécurité ne peuvent pas être contournées.
- Ramène directement au menu "Choix des contrôles" sans perte de données.

---

## Évolutions depuis la V1.0

| Point | V1.0 | V1.1 |
|-------|------|------|
| Modules disponibles | Graisseurs uniquement | 4 modules |
| Graisseurs série T | T1–T8 (8 convoyeurs, 32 graisseurs) | T1–T8 + TC (9 convoyeurs, 36 graisseurs) |
| Graisseurs total | 48 | 52 |
| Visuel OVB | Rectangle + flèche (identique convoyeur) | Rectangle + chevrons /\\ distinctifs |
| Écran d'accueil | Reprise d'une ronde unique | Gestion de session complète |
| Navigation | Linéaire (Précédent / Suivant) | Hub central + bouton Home |
| Persistance | Données d'une seule ronde | Données de 4 modules simultanés |
| Progression visible | En-tête du contrôle actif uniquement | Tableau de bord global |

---

## Choix ergonomiques

- **Smartphone uniquement** — gros boutons, pas de texte à saisir, utilisation possible sans clavier.
- **Session plutôt que ronde** — l'opérateur fait plusieurs contrôles dans une même sortie terrain sans revenir à l'accueil.
- **Pas de rouge/vert dans la navigation** — les catégories ▶ En route / ⏸ À l'arrêt utilisent uniquement la couleur accent (cyan) pour éviter la confusion avec les états métier 🟢🟡🔴.
- **Progression individuelle par contrôle** — l'opérateur voit immédiatement quels contrôles sont terminés, en cours, ou non commencés.
- **Reprise intelligente** — pas besoin de se souvenir de l'équipement en cours ; l'application reprend au premier élément incomplet.
- **Lames en ligne unique** — la représentation à 10 lames sur une seule ligne (T4) est fidèle à la disposition physique plutôt qu'optimisée pour l'écran.
- **OVB visuellement distinct** — les chevrons évoquent les lattes magnétiques, différenciant l'overband du convoyeur dès le premier regard.
- **Étapes sécurité non contournables** — le bouton Home est absent sur EPI et Consigne ; l'opérateur ne peut pas les sauter lors d'une nouvelle session.

---

## Points à tester sur le terrain

### Flux de session
- [ ] Démarrage : EPI → Consigne → Choix des contrôles.
- [ ] Reprise après fermeture du navigateur : SESSION EN COURS affiché, données restaurées.
- [ ] Fin de session : réinitialisation complète, retour à l'accueil.

### Ronde du Général
- [ ] Bannieres de vigilance affichées pour chaque zone.
- [ ] Chips de motifs apparaissent uniquement sur état 🟡 ou 🔴.
- [ ] Commentaire facultatif sauvegardé entre zones.
- [ ] Résumé final complet (zones + motifs + commentaires).

### Graisseurs automatiques
- [ ] TC présent entre T5 et T6 dans la séquence.
- [ ] Total affiché : 52 / 52.
- [ ] OVB clairement distinguable visuellement des convoyeurs.
- [ ] Positions AVANT / ARRIÈRE (OVB) vs TÊTE / PIED (convoyeurs).

### Contrôle lames goulottes
- [ ] T3 : 5 lames sur une ligne.
- [ ] T4 : 10 lames sur une ligne.
- [ ] T7 : 5 lames sur une ligne.
- [ ] Cycle ⚪ → 🟢 → 🟡 → 🔴 → ⚪ au clic.
- [ ] Résumé avec compteurs corrects.

### Contrôle usure tapis
- [ ] Séquence : T1 → T2 → T3 → T4 → T5 → TC → T6 → T7 → T8 → OVB1 → OVB2 → OVB3 → OVB4.
- [ ] OVB affiche 4 critères (+ Lattes), convoyeurs affichent 3 critères.
- [ ] Pas de T9 dans la liste.

### Navigation générale
- [ ] Bouton 🏠 sur tous les écrans opérationnels → Choix des contrôles.
- [ ] Bouton 🏠 absent sur EPI et Consigne.
- [ ] Progression conservée après 🏠.
- [ ] "Menu des contrôles" depuis un résumé → Choix des contrôles sans effacement.
- [ ] Tableau de bord : progression de chaque contrôle mise à jour en temps réel.

---

## Structure du projet

```
Vigie/
├── index.html                    ← Application V1.1 (production)
├── CHANGELOG_V1.1.md             ← Ce fichier
├── archives/
│   ├── vigie-v1.0.html           ← Archive V1.0
│   └── VIGIE_V1.1_FINAL.html     ← Archive figée V1.1
└── .claude/
    └── launch.json               ← Config serveur de développement
```

---

## Publication GitHub Pages

L'application est une **Single Page Application** autonome en HTML/CSS/JS pur.

- Aucune dépendance externe.
- Aucun build requis.
- Compatible GitHub Pages sans configuration particulière.
- Le fichier `index.html` à la racine est directement servi.

Pour publier : pousser le dépôt sur GitHub et activer GitHub Pages sur la branche `main`.
