# 🎵 AI SoundBoard - MyInstants API Reverse

Une application Electron moderne qui permet de rechercher et jouer des sons depuis MyInstants avec une interface transparente sur le côté droit de votre écran.

## 🚀 Fonctionnalités

- **API Reverse en temps réel** : Recherche directement sur MyInstants.com
- **Interface transparente** : Fenêtre sans bordures qui s'affiche sur le côté droit de l'écran
- **Recherche intelligente** : Tapez votre recherche et obtenez les résultats instantanément
- **Cache automatique** : Les sons sont mis en cache temporairement pour une lecture plus fluide
- **Sons populaires** : Affichage des sons tendance au démarrage
- **Son aléatoire** : Fonction pour jouer un son au hasard
- **Interface moderne** : Design sombre avec effets visuels

## 📋 Prérequis

- Node.js (version 14 ou plus récente)
- npm
- Connexion Internet pour accéder à MyInstants

## 🛠️ Installation

1. **Cloner ou télécharger le projet**
   ```bash
   cd ai-soundboard
   ```

2. **Installer les dépendances**
   ```bash
   npm install
   ```

3. **Lancer l'application**
   ```bash
   npm start
   ```

## 🎮 Utilisation

### Interface principale

L'application s'affiche sous forme d'une barre verticale transparente sur le côté droit de votre écran avec :

- **Zone de recherche** : Tapez votre mot-clé pour rechercher des sons
- **Boutons de contrôle** :
  - 🔍 Lancer une recherche
  - 🎲 Son aléatoire
  - 🔄 Actualiser (retour aux tendances)
  - ❌ Fermer l'application

### Recherche de sons

1. **Recherche par mot-clé** : Tapez dans la zone de recherche (ex: "salut", "meme", "bruh")
2. **Recherche automatique** : La recherche se lance automatiquement après 300ms
3. **Validation** : Appuyez sur Entrée pour valider votre recherche

### Lecture de sons

- **Clic simple** : Cliquez sur un son pour le jouer
- **Animation** : Le son en cours de lecture est mis en surbrillance avec une animation
- **Cache automatique** : Les sons sont téléchargés et mis en cache pour une lecture plus rapide

### Raccourcis clavier

- **Echap** : Arrêter le son en cours
- **F5** : Actualiser et retourner aux tendances
- **/** : Focus sur la zone de recherche

## 🔧 Architecture technique

### API Reverse

L'application utilise une API Express qui fait du scraping en temps réel sur MyInstants :

- **Recherche** : `GET /api/search/:query`
- **Tendances** : `GET /api/trending`
- **Cache** : `GET /api/cached/:id`
- **Téléchargement** : `GET /api/sound/:id/download`

### Parsing HTML

L'API parse le HTML de MyInstants pour extraire :
- Nom des sons
- URLs des fichiers MP3
- Liens vers les pages d'instant
- Métadonnées des sons

### Cache temporaire

- Les sons sont mis en cache dans le dossier temporaire système
- Nettoyage automatique après 1 heure
- Améliore la performance de lecture

## 📁 Structure du projet

```
├── main.js              # Application Electron principale avec API
├── index.html           # Interface utilisateur
├── styles.css           # Styles CSS transparents
├── script.js            # Logique côté client
├── package.json         # Configuration npm
└── README.md           # Documentation
```

## 🎨 Personnalisation

### Apparence

Modifiez `styles.css` pour personnaliser :
- Couleurs et transparence
- Position de la fenêtre
- Animations et effets

### Position de la fenêtre

Dans `main.js`, modifiez les paramètres de `BrowserWindow` :
```javascript
width: 320,              // Largeur
height: height - 100,    // Hauteur
x: width - 340,          // Position X (droite par défaut)
y: 50,                   // Position Y
```

## 🐛 Dépannage

### L'application ne se lance pas
- Vérifiez que Node.js est installé : `node --version`
- Réinstallez les dépendances : `npm install`

### Pas de sons trouvés
- Vérifiez votre connexion Internet
- Testez l'API : http://localhost:3001/api/status
- MyInstants pourrait être temporairement indisponible

### Sons qui ne se lancent pas
- Vérifiez les permissions audio de votre navigateur
- Certains sons peuvent avoir des restrictions de CORS
- Le cache peut être plein (redémarrez l'application)

## 🔒 Conformité et limitations

- **Usage éducatif** : Cette application est créée à des fins d'apprentissage
- **Respect du site** : L'API fait des requêtes raisonnables pour ne pas surcharger MyInstants
- **Cache temporaire** : Les sons ne sont pas stockés de façon permanente
- **Pas de redistribution** : Les sons appartiennent à leurs créateurs respectifs

## 🆕 Améliorations futures

- [ ] Ai direct soundboard

## 📝 Licence

MIT License - Voir le fichier LICENSE pour plus de détails.
