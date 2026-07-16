# Cahier des charges — Mini-application « Road trip Massif central »

| | |
|---|---|
| **Projet** | Application web de visualisation interactive d'un itinéraire de road trip |
| **Commanditaire** | Matt (projet personnel) |
| **Version** | 1.0 |
| **Date** | 16 juillet 2026 |
| **Statut** | Validé pour développement |

---

## 1. Contexte et objectifs

Dans le cadre de la préparation d'un road trip de 6 jours entre Nancy et le Massif central (du **samedi 8 au jeudi 13 août 2026**, en boucle complète), le commanditaire souhaite disposer d'une application web légère permettant de visualiser l'itinéraire de manière interactive.

L'application doit être **consultable en ligne via GitHub Pages** et servir à la fois d'outil de préparation avant le départ et de référence pendant le voyage (consultation sur mobile).

### Objectifs

- **O1** — Visualiser l'intégralité du parcours (boucle Nancy → Nancy) sur une carte interactive.
- **O2** — Consulter le détail de chaque journée : étapes, horaires indicatifs, altitudes, conseils pratiques, lieu de nuitée.
- **O3** — Publier l'application sans coût d'hébergement ni dépendance à un service payant.

---

## 2. Périmètre

### Inclus

- Affichage cartographique de l'itinéraire complet et des 10 étapes.
- Panneau descriptif jour par jour (6 jours), interactif et synchronisé avec la carte.
- Compatibilité ordinateur et mobile (consultation en voiture / en randonnée avec réseau).

### Exclus (V1)

- Calcul d'itinéraire routier en temps réel (le tracé relie les étapes à vol d'oiseau).
- Réservation d'hébergements ou intégration à des services tiers (météo, trafic).
- Compte utilisateur, sauvegarde serveur, mode collaboratif.
- Fonctionnement hors ligne complet (PWA).

---

## 3. Exigences fonctionnelles

| ID | Exigence | Priorité |
|----|----------|----------|
| EF-01 | La carte affiche les 10 étapes du parcours sous forme de marqueurs numérotés dans l'ordre chronologique. Nancy (départ/arrivée) porte un marqueur distinct. | Obligatoire |
| EF-02 | Le tracé de la boucle complète relie toutes les étapes, du départ de Nancy au retour à Nancy. | Obligatoire |
| EF-03 | Un clic sur un marqueur ouvre une infobulle : nom du site, jour et date, horaire indicatif, altitude, note pratique. | Obligatoire |
| EF-04 | Un panneau latéral liste les 6 journées (sam. 8 → jeu. 13 août 2026) avec date, titre, kilométrage indicatif. | Obligatoire |
| EF-05 | Un clic sur une journée déplie son détail (étapes, nuitée) et recentre/zoome la carte sur les étapes du jour ; les marqueurs des autres jours sont estompés. | Obligatoire |
| EF-06 | Un second clic sur la journée ouverte referme le détail et rétablit la vue globale de la boucle. | Obligatoire |
| EF-07 | Les étapes facultatives (ex. château de Murol) sont visuellement identifiées comme « optionnelles ». | Souhaitable |
| EF-08 | Le lieu de nuitée de chaque journée est affiché avec une note de contexte. | Obligatoire |
| EF-09 | L'en-tête affiche le titre du voyage, les dates et le kilométrage total estimé. | Souhaitable |

### Contenu de l'itinéraire (données de référence)

| Jour | Date | Étapes | Nuitée |
|------|------|--------|--------|
| 1 | Sam. 8 août | Départ Nancy · Roche de Solutré | Orcines / Clermont-Ferrand |
| 2 | Dim. 9 août | Puy de Dôme · Puy de Pariou | Besse-et-Saint-Anastaïse |
| 3 | Lun. 10 août | Lac Pavin · **Puy de Sancy (téléphérique)** · Château de Murol *(optionnel)* | Murat / Le Claux |
| 4 | Mar. 11 août | Puy Mary · Plateau de l'Aubrac | Sainte-Énimie |
| 5 | Mer. 12 août | Gorges du Tarn · Viaduc de Millau | Le Puy-en-Velay |
| 6 | Jeu. 13 août | Rocher Saint-Michel d'Aiguilhe · Retour Nancy | — |

---

## 4. Exigences non fonctionnelles

| ID | Exigence | Priorité |
|----|----------|----------|
| ENF-01 | **Fichier unique** : l'application tient dans un seul `index.html` autonome (HTML + CSS + JS inclus). | Obligatoire |
| ENF-02 | **Aucune clé API** ni service payant : bibliothèques et fonds de carte libres uniquement. | Obligatoire |
| ENF-03 | **Hébergement statique** : déployable tel quel sur GitHub Pages, sans étape de build. | Obligatoire |
| ENF-04 | **Responsive** : mise en page adaptée du poste de travail au smartphone (≤ 820 px : carte au-dessus, panneau en dessous). | Obligatoire |
| ENF-05 | **Accessibilité** : navigation clavier sur les journées (focus visible, Entrée/Espace), respect de `prefers-reduced-motion`. | Souhaitable |
| ENF-06 | **Langue** : interface intégralement en français. | Obligatoire |
| ENF-07 | **Performance** : page utilisable en moins de 3 s sur connexion mobile standard (hors chargement des tuiles). | Souhaitable |

---

## 5. Contraintes et choix techniques

| Domaine | Choix | Justification |
|---------|-------|---------------|
| Langage | HTML / CSS / JavaScript vanilla | Aucune chaîne de build, maintenance minimale |
| Cartographie | [Leaflet](https://leafletjs.com) 1.9.x via CDN (cdnjs) | Standard open source, léger, sans clé API |
| Fond de carte | Tuiles OpenTopoMap (© OpenStreetMap, CC-BY-SA) | Rendu topographique adapté à un itinéraire de montagne |
| Typographies | Google Fonts (Bricolage Grotesque, Public Sans) avec repli `sans-serif` | Identité visuelle ; dégradation acceptable si CDN indisponible |
| Données | Structure JavaScript embarquée dans la page (`DAYS`) | Volume faible et stable ; évite un fichier JSON externe et les problèmes CORS en ouverture locale |
| Hébergement | GitHub Pages (branche `main`, racine) | Gratuit, versionné, URL publique |

**Attribution** : les mentions légales OpenStreetMap / OpenTopoMap doivent rester visibles sur la carte et en pied de panneau.

---

## 6. Livrables

1. `index.html` — application complète et autonome.
2. `CAHIER_DES_CHARGES.md` — le présent document, versionné dans le dépôt.
3. `README.md` *(souhaitable)* — présentation du projet et procédure de déploiement GitHub Pages.

---

## 7. Critères de recette

| ID | Scénario de test | Résultat attendu |
|----|------------------|------------------|
| CR-01 | Ouvrir `index.html` en double-cliquant sur le fichier (protocole `file://`), navigateur récent, connexion Internet active | La carte, le tracé et les 10 marqueurs s'affichent |
| CR-02 | Ouvrir l'URL GitHub Pages sur ordinateur | Identique à CR-01, panneau latéral à gauche |
| CR-03 | Ouvrir l'URL GitHub Pages sur smartphone | Carte en haut, panneau en bas, aucune barre de défilement horizontale |
| CR-04 | Cliquer sur « Lun. 10 août » | Le détail se déplie, la carte zoome sur le Sancy, les autres marqueurs s'estompent |
| CR-05 | Recliquer sur la même journée | Le détail se referme, la vue globale de la boucle est rétablie |
| CR-06 | Cliquer sur le marqueur « Puy de Sancy » | Infobulle avec jour, horaire, altitude 1 885 m et note pratique |
| CR-07 | Naviguer au clavier (Tab puis Entrée sur une journée) | Comportement identique au clic, focus visible |
| CR-08 | Couper le réseau puis recharger | Dégradation contrôlée : la page se charge, un message ou une zone vide remplace les tuiles (pas d'erreur bloquante) |

**Environnements de référence** : Chrome, Firefox et Safari dans leurs versions courantes ; Android et iOS récents.

> ⚠️ **Limite connue** : la prévisualisation du fichier dans certaines interfaces en bac à sable (aperçu de chat, visionneuse intégrée) peut bloquer les CDN et les tuiles cartographiques. La recette fait foi sur navigateur (fichier local ou GitHub Pages), pas en aperçu intégré.

---

## 8. Évolutions envisagées (hors périmètre V1)

- **V1.1** — Cases à cocher « étape faite » avec persistance locale (`localStorage`).
- **V1.2** — Lien « Ouvrir dans Google Maps » par étape pour la navigation routière.
- **V1.3** — Affichage de la météo du jour par site (API météo gratuite).
- **V2** — Tracé routier réel (OSRM / GraphHopper) en remplacement du tracé à vol d'oiseau.

---

*Document rédigé le 16 juillet 2026 — version 1.0.*
