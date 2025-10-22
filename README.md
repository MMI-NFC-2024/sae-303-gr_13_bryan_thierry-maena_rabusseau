[![Review Assignment Due Date](https://classroom.github.com/assets/deadline-readme-button-22041afd0340ce965d47ae6ef1cefeee28c7c493a6346c4f15d667ab976d596c.svg)](https://classroom.github.com/a/tzO_JqWG)
- URL site WEB : sae-303-bryan-thierry-maena-rabusseau.netlify.app  https://sae-303-bryan-thierry-maena-rabusseau.netlify.app/ 
- URL Notebook Observable : https://observablehq.com/d/7056e0df4a835b48 
- Nom : Rabusseau
- Prénom : Maéna 
- Nom binome : Thierry 
- Prénom binome : Bryan 


 Remarques : Éléments Techniques Remarquables


### Framework CSS & Composants
- **[DaisyUI](https://daisyui.com/)** + **Tailwind CSS** pour un design moderne et cohérent
- Système de thèmes personnalisables avec variables CSS
- Composants réutilisables : cards, badges, alerts, stats
- [Navigation fixe](src/pages/index.astro#L6-L52) avec menu responsive

### Interface Responsive
- **Mobile-first design** avec breakpoints adaptatifs
- Grilles flexibles utilisant `lg:grid-cols-2` pour layout desktop/mobile
- Navigation hamburger menu pour mobile (< 1024px)
- [Exemple de grille responsive](src/pages/index.astro#L316) : graphique à gauche, texte à droite sur desktop, empilés sur mobile


### Composants de Visualisation
- **[Composant Donuts](src/components/Donuts.astro)** : Graphique en anneau pour les régions
- **[Composant CartePatrimoine](src/components/CartePatrimoine.astro)** : Carte interactive avec sélecteur départements/régions
  - Filtre dynamique avec dropdown
  - Agrégation de données par code postal
  - Exclusion automatique des DOM-TOM
  - Mapping département → région
  - Échelle de couleur séquentielle (YlGnBu)
  - Tooltips interactifs avec nombre de lieux
- **Observable Plot.js** : Bibliothèque de visualisation déclarative
- **D3.js** : Manipulation et chargement de données GeoJSON
- **Leaflet** : Cartes interactives pour la représentation géographique
- Sources de données avec badges cliquables vers [Data.gouv.fr](src/pages/index.astro#L331-L340)

### Modes de Navigation des Visualisations
1. **[Mode Iframe](src/pages/visualisations/diagnostic-iframe.astro)** : Navigation avec menu latéral fixe
   - Menu latéral avec 3 sections de visualisations
   - IntersectionObserver pour activer automatiquement le menu selon la position de scroll
   - Smooth scroll vers les sections
   - Badge "Mode Iframe" dans le header
   - Bouton retour vers la page principale
   
2. **[Mode Slider](src/pages/visualisations/diagnostic-slider.astro)** : Défilement horizontal avec cartes géographiques
   - 2 slides : Départements et Régions
   - Navigation au clavier avec flèches ← →
   - Boutons de navigation circulaires entre slides
   - Indicateurs actifs en bas de page
   - Cartes générées avec Observable Plot et D3.js
   - Tooltip d'aide pour la navigation
   
3. **Pages individuelles** : Chaque visualisation accessible directement depuis la page d'accueil

### Layout des Graphiques
- [**Layout 2 colonnes**](src/pages/index.astro#L316-L371) : Graphique (50%) + Analyse (50%)
- **Inversion flexible** : Texte à gauche/droite selon la visualisation
- Hauteur fixe de 500px pour cohérence visuelle
- Bordures en pointillés pour zones de graphiques à compléter



### Navigation Principale
- **[Menu fixe en haut](src/pages/index.astro#L6-L52)** avec liens d'ancrage
- Navigation smooth scroll (`scroll-behavior: smooth`)
- Sections numérotées avec badges :
  - 01 - [Problématique](src/pages/index.astro#L88)
  - 02 - [Objectifs](src/pages/index.astro#L122)
  - 03 - [Données](src/pages/index.astro#L175)
  - 04 - [Analyse](src/pages/index.astro#L266)
  - 05 - [Solutions](src/pages/index.astro#L409)

### Hero Section
- [Section d'accueil](src/pages/index.astro#L54-L104) avec gradient background
- Statistiques clés affichées en cards
- Call-to-action avec scroll vers contenu



### Alerts & Messages Informatifs
- **[Alerts personnalisées](src/pages/index.astro#L104-L118)** avec couleur primaire (`bg-primary text-primary-content`)
- Icônes SVG intégrées pour meilleure accessibilité
- Structure sémantique avec titres et descriptions
- Utilisées pour : Constat, Observation clé, Impact attendu

### Cards Statistiques
- **[Stats verticales](src/pages/index.astro#L356-L376)** : Nombre d'EPCI, ratios, etc.
- Disposition flexible avec `stats-vertical`
- Valeurs colorées selon importance (primary, secondary, accent)
- Descriptions contextuelles pour chaque métrique

### Badges & Tags
- **[Badges de section](src/pages/index.astro#L123)** numérotés (01, 02, 03...)
- Tags de catégorie (`badge-outline`)
- [Badges de source](src/pages/index.astro#L335) avec hover effects



### Boutons & Liens
- **[Bouton Mode Iframe](src/pages/index.astro#L245)** : Accès au mode navigation avec menu latéral
- **[Bouton Mode Slider](src/pages/index.astro#L258)** : Accès au mode diaporama avec cartes
- Boutons avec style `btn-outline` et icônes SVG personnalisées
- [Lien vers Observable Notebook](src/pages/index.astro#L468) avec icône externe
- États hover avec transitions CSS
- Tailles adaptées (`btn-lg`) pour faciliter le clic
- Groupement de boutons avec `flex gap-2`

### Accessibilité
- Structure sémantique HTML5 (`<section>`, `<nav>`, `<main>`)
- Attributs ARIA implicites via DaisyUI
- Liens externes avec `target="_blank"` et `rel="noopener noreferrer"`
- SVG avec chemins descriptifs pour lecteurs d'écran
- Contraste de couleurs respectant WCAG (alerts primaires avec `bg-primary text-primary-content`)
- Navigation au clavier complète (mode slider avec flèches ← →)
- Tooltips informatifs (`data-tip`) pour guidance utilisateur
- Indicateurs visuels clairs pour position dans le slider



### Framework & Build
- **[Astro](astro.config.mjs)** : Framework statique ultra-rapide
- Génération de pages statiques (SSG)
- Composants `.astro` avec 0 JavaScript par défaut
- Hydratation partielle uniquement si nécessaire



### Données
- **[Sources de données](src/assets/)** : JSON locaux pour performance
  - `basilic_clean.json` : Équipements culturels (564 lieux)
  - `departements.json` : Données géographiques départementales (GeoJSON)
  - `regions.json` : Données géographiques régionales (GeoJSON)
  - `population.json` : Statistiques démographiques
- **Traitement des données** :
  - Agrégation par code postal puis département/région
  - Filtrage automatique des DOM-TOM
  - Mapping département → région avec table de correspondance
  - Calcul dynamique du nombre de lieux par territoire
  - Enrichissement des GeoJSON avec données quantitatives



### Breakpoints
- **Mobile** : < 1024px (navigation hamburger, grille empilée)
- **Desktop** : ≥ 1024px (navigation horizontale, grilles 2 colonnes)
- Utilisation de classes Tailwind `lg:` pour adaptations

### Grilles Adaptatives
- [Visualisations](src/pages/index.astro#L252-L253) : `grid lg:grid-cols-2`
- Gap ajustable selon l'écran
- Ordre des colonnes modifiable (`order-1`, `order-2`)




