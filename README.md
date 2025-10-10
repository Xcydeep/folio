## Portfolio Xcydeep — Développeur Backend

Un portfolio mono-fichier (HTML/CSS/JS) élégant et performant, mettant en avant les compétences backend, les projets, l'expérience, la formation et un formulaire de contact fonctionnel (Formspree). Aucune dépendance de build — tout est prêt à l'emploi dans `index.html`.

### Aperçu rapide
- **Technos**: HTML5, CSS3, JavaScript (ES6), Google Fonts, Font Awesome
- **CDN**: Font Awesome 6.4, Google Fonts (`Inter`, `JetBrains Mono`, `Playfair Display`)
- **Contact**: Formulaire intégré via Formspree (`POST https://formspree.io/f/mgvlowll`)
- **Fichiers principaux**: `index.html`, `favicon.ico`, images (portfolio, projets, profil), `CV_professionel.pdf`

### Structure fonctionnelle (Sections et interfaces)
- **Header / Navigation**
  - Logo avec image ronde et texte accentué
  - Menu liens: `Accueil`, `Compétences`, `Projets`, `Expérience`, `Formation`, `Contact`
  - Bouton hamburger (mobile) avec ouverture/fermeture du menu et changement d'icône
  - Lien de téléchargement du CV (`CV_professionel.pdf`)
- **Arrière-plans animés**
  - Lignes animées générées dynamiquement en JS (`createBackgroundLines`) avec opacité/largeur/délais aléatoires
  - Cercles décoratifs violets qui se dispersent/reviennent selon le scroll de la section `#home`
- **Hero (`#home`)**
  - Titre, sous-texte, boutons d'appel à l'action
  - Photo de profil avec cadres animés et lignes dorées ascendantes (`gold-rise`)
- **Compétences (`#skills`)**
  - Cartes de catégories (Langages & Frameworks, Bases de données, API & Services, Outils & Méthodologies)
  - Hover states, bordures, ombres et animations d'entrée
- **Projets (`#projects`)**
  - Cartes projet avec image, description, tags techno et **barre d’avancement animée** (JS augmente `width` et texte de 0→% cible)
- **Expérience (`#experience`)**
  - Timeline centrée avec items alternés, marqueurs animés au survol
- **Formation (`#education`)**
  - Liste d’éléments avec dates et descriptions
- **Contact (`#contact`)**
  - Coordonnées (email, téléphone/WhatsApp, localisation)
  - Formulaire de contact validé côté client et envoyé via **Formspree**
- **Footer**
  - Texte, liens sociaux (GitHub, LinkedIn, Twitter, WhatsApp, Facebook), copyright

### Comportements et logique (JavaScript)
- `createBackgroundLines()` — génère les lignes décoratives en arrière-plan
- `setupMobileNavigation()` — gère l’ouverture/fermeture du menu hamburger et la fermeture au clic sur un lien
- `setupHeaderScroll()` — rétrécit/ombre le header au scroll (`.scrolled`)
- `setupSectionAnimations()` — active l’animation d’apparition des sections via `IntersectionObserver`
- Cercles d’arrière-plan — dispersion/recentrage selon visibilité de `#home`
- Toasts et messages de bouton
  - `showToast(message, type, duration)` — toasts success/error/warning avec fermeture et auto-disparition
  - `showBtnMessage(text, color, duration)` — message contextuel à côté du bouton envoyer
- Formulaire de contact (`#contactForm`)
  - Validation stricte (longueurs, regex nom/email, min/max)
  - Envoi `fetch` vers Formspree avec `Accept: application/json`
  - Gestion des états: loader sur bouton, reset, toasts d’erreur/succès
- Barres de progression des projets
  - Démarrage après `DOMContentLoaded`: remplit la barre vers `data-percentage` et incrémente le texte
- Lignes dorées dynamiques autour de la photo — créées et animées après `DOMContentLoaded`

### Personnalisation
- **Couleurs/Thèmes**: variables CSS dans `:root` (`--primary-color`, `--secondary-color`, `--accent-color`, etc.)
- **Typographies**: modifiables via les import Google Fonts en `<head>`
- **Images**: remplacez `img.png`, `screen.jpg`, `icon.png`, etc. par vos visuels (mêmes noms ou ajustez les `src`)
- **Liens sociaux**: éditer les URLs dans le footer
- **CV**: remplacer `CV_professionel.pdf` et/ou le texte du lien de téléchargement
- **Formulaire**: changer l’endpoint Formspree par le vôtre (`action` du `<form>`) et valider le schéma côté Formspree si nécessaire

### Déploiement
- Projet statique — hébergeable sur n’importe quel service static hosting (GitHub Pages, Netlify, Vercel, etc.)
  1. Pousser le dossier sur un repo
  2. Activer l’hébergement statique (racine = ce dossier)
  3. Vérifier que les chemins d’images et `favicon.ico` sont accessibles

### Accessibilité & responsive
- Navigation clavier et focus visibles sur inputs
- Breakpoints principaux: 1200px, 992px, 768px, 576px
- Menu mobile coulissant, boutons full-width sur mobile, grilles adaptatives

### Sécurité & bonnes pratiques
- Validation client robuste avant envoi du formulaire
- Pas de clés API ni secrets côté client
- Utilisation d’un service tiers (Formspree) pour éviter un backend exposé

### Arborescence minimale
```
folio/
├─ index.html
├─ README.md
├─ favicon.ico
├─ CV_professionel.pdf
├─ img.png
├─ icon.png
├─ screen.jpg
├─ 20250126_213548.jpg
├─ 73c1cdf1-e726-4af5-b6f6-842ffd7c0e5d.jpg
├─ 8cfe4772-acdd-40ae-8f38-c06411c10e69.jpg
└─ 9112b807bc9ced3b5bd2dc8ca5ae8312.jpg
```

### Utilisation locale
- Ouvrir `index.html` dans un navigateur moderne
- Pour tester le formulaire, utiliser votre endpoint Formspree (le courant est `mgvlowll`)

### Licence
Projet personnel de portfolio. Sauf mention contraire, tout le contenu (texte, images, CV) est la propriété de l’auteur.

