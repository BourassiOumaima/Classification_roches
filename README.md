# Classificateur de Roches

Application web permettant d'identifier le type d'une roche à partir d'une photo, grâce à un modèle de deep learning exécuté directement dans le navigateur (TensorFlow.js).

## Fonctionnalités

- Chargement d'une image de roche depuis l'appareil
- Classification en temps réel dans le navigateur (pas de serveur backend nécessaire)
- Affichage des 3 prédictions les plus probables avec leur pourcentage de confiance

## Classes reconnues

- Basalt
- Coal
- Granite
- Limestone
- Marble
- Quartzite
- Sandstone

## Technologies

- HTML / JavaScript
- TensorFlow.js (TFJS) pour l'inférence côté client
- Tailwind CSS pour le style

## Architecture

Le modèle (entraîné au préalable, probablement avec Keras/TensorFlow puis converti au format TFJS) est chargé directement dans le navigateur via `tf.loadGraphModel`. Chaque image est redimensionnée en 224x224, normalisée, puis passée au modèle pour prédiction.

## Structure du projet

```
classification_roches/
├── index.html                      # Interface + logique de prédiction
└── rock_classifier_float32_tfjs/   # Modèle TFJS (model.json + poids)
```

## Installation et utilisation

1. Cloner le dépôt
2. S'assurer que le dossier `rock_classifier_float32_tfjs/` (contenant `model.json` et les fichiers de poids) est présent à la racine
3. Servir le projet via un serveur local (nécessaire pour le chargement du modèle), par exemple :
```bash
python -m http.server 8000
```
4. Ouvrir `http://localhost:8000` dans le navigateur
5. Charger une image de roche et cliquer sur "Prédire"
