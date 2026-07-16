# 🏔️ Road trip Massif central — Nancy → Nancy

Mini-application web pour visualiser, de façon interactive, l'itinéraire d'un road trip
de 6 jours entre **Nancy et le Massif central** (8 → 13 août 2026, en boucle complète).

Carte topographique, tracé de la boucle, 10 étapes numérotées et détail jour par jour
(horaires indicatifs, altitudes, conseils, lieux de nuitée).

**🔗 Démo en ligne : https://matthieucrny.github.io/voyage-itineraire/**

![Statut](https://img.shields.io/badge/statut-V1-2f6d4f) ![Sans build](https://img.shields.io/badge/build-aucun-b5541f) ![Sans clé API](https://img.shields.io/badge/API-aucune%20cl%C3%A9-2f6d4f)

---

## ✨ Fonctionnalités

- 🗺️ **Carte interactive** (Leaflet + fond OpenTopoMap) avec le tracé de la boucle complète.
- 📍 **10 étapes numérotées** dans l'ordre chronologique ; Nancy porte un marqueur de départ/arrivée distinct.
- 🗓️ **Panneau jour par jour** : cliquer une journée déplie son détail et zoome la carte sur ses étapes (les autres s'estompent) ; recliquer referme et rétablit la vue globale.
- ℹ️ **Infobulles** par site : jour, date, horaire, altitude et note pratique.
- ⭐ **Étapes optionnelles** clairement identifiées (ex. château de Murol).
- 🛏️ **Lieu de nuitée** affiché pour chaque journée.
- 📱 **Responsive** (carte au-dessus, panneau en dessous sur mobile) et **navigable au clavier**.

---

## 🚀 Utilisation

### En local

Ouvrez simplement `index.html` dans un navigateur récent (double-clic).
Une **connexion Internet est nécessaire** pour charger la bibliothèque de carte et les
tuiles topographiques (aucune installation, aucune étape de build).

> 💡 Si Leaflet ou les tuiles ne se chargent pas (hors ligne, CDN bloqué), la page
> reste utilisable : le détail des journées s'affiche et un message remplace la carte.

### Déploiement sur GitHub Pages

1. Créez un dépôt GitHub et poussez le contenu de ce dossier à la **racine** de la branche `main` :
   ```bash
   git init
   git add .
   git commit -m "Road trip Massif central — V1"
   git branch -M main
   git remote add origin git@github.com:<utilisateur>/<depot>.git
   git push -u origin main
   ```
2. Dans le dépôt : **Settings → Pages**.
3. **Source** : `Deploy from a branch` → branche `main`, dossier `/ (root)`.
4. Enregistrez. L'URL publique (`https://<utilisateur>.github.io/<depot>/`) est disponible en une à deux minutes.

Aucune configuration supplémentaire n'est requise : le site est entièrement statique.

---

## 🧱 Structure du projet

```
.
├── index.html              # Application complète et autonome (HTML + CSS + JS)
├── CAHIER_DES_CHARGES.md   # Spécifications de référence (V1.0)
└── README.md               # Ce fichier
```

Les données de l'itinéraire sont embarquées dans `index.html` (constante `DAYS`) :
pour modifier une étape, un horaire ou une nuitée, éditez directement cet objet.

---

## 🛠️ Choix techniques

| Domaine | Choix |
|---------|-------|
| Langage | HTML / CSS / JavaScript vanilla — aucune chaîne de build |
| Cartographie | [Leaflet](https://leafletjs.com) 1.9.4 (CDN cdnjs) |
| Fond de carte | Tuiles [OpenTopoMap](https://opentopomap.org) © OpenStreetMap (CC-BY-SA) |
| Typographies | Google Fonts (Bricolage Grotesque, Public Sans), repli `sans-serif` |
| Hébergement | GitHub Pages (statique, gratuit) |

---

## 🗺️ Itinéraire

| Jour | Date | Étapes | Nuitée |
|------|------|--------|--------|
| 1 | Sam. 8 août | Départ Nancy · Roche de Solutré | Orcines / Clermont-Ferrand |
| 2 | Dim. 9 août | Puy de Dôme · Puy de Pariou | Besse-et-Saint-Anastaïse |
| 3 | Lun. 10 août | Lac Pavin · Puy de Sancy · Château de Murol *(optionnel)* | Murat / Le Claux |
| 4 | Mar. 11 août | Puy Mary · Plateau de l'Aubrac | Sainte-Énimie |
| 5 | Mer. 12 août | Gorges du Tarn · Viaduc de Millau | Le Puy-en-Velay |
| 6 | Jeu. 13 août | Rocher Saint-Michel d'Aiguilhe · Retour Nancy | — |

Kilométrage total estimé : **≈ 1 640 km** (tracé à vol d'oiseau ; horaires et distances indicatifs).

---

## 📄 Attribution & licence

- Fonds de carte © [OpenStreetMap](https://www.openstreetmap.org/copyright), rendu
  [OpenTopoMap](https://opentopomap.org) (CC-BY-SA) — mentions conservées sur la carte et en pied de panneau.
- Projet personnel. Contenu de l'itinéraire librement réutilisable.
