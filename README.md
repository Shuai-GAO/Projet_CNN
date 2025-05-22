# Reconnaissance des langues sous-annotées avec réseaux de neurones

## Introduction
Ce projet vise à appliquer les **réseaux de neurones** à la reconnaissance automatique des langues sous-annotées (**mongol, tatar, estonien et chinois**) en utilisant des **spectrogrammes audio** comme entrée.

## Méthodologie

### 1. Prétraitement des données
- **Téléchargement** des corpus depuis *Common Voice*.
- **Filtrage** des fichiers audios pour supprimer les silences (*Praat*).
- **Segmentation** en tranches de **2 secondes**.
- **Suppression** des fichiers trop courts (< 0.8s).
- **Transformation** des fichiers audio en images spectrogrammes (*.png*).

### 2. Architecture du modèle
- Modèle CNN développé avec **Keras/TensorFlow** :
  - **Deux couches de convolution** (`Conv2D`).
  - **Couches de pooling** (`MaxPooling2D`) pour la réduction de dimension.
  - **Couches entièrement connectées** (`Dense`) pour la classification finale.

### 3. Entraînement et optimisation
- **Hyperparamètres** :
  - `batch_size = 50`
  - `epochs = 100`
  - `learning_rate = 0.01`
- **Plateforme** : Google Colaboratory.
- **Optimisation** : SGD avec Nesterov momentum.

## Résultats
- **Précision maximale atteinte** : **79,3 %**.
- **Défis identifiés** :
  - Similarité linguistique entre le **mongol et le tatar**, rendant la classification plus difficile.
  - **Impact de la taille du corpus** : un corpus plus petit (344 fichiers train, 40 fichiers test) a donné une précision plus élevée (**85,5 %**), tandis qu’un corpus plus grand a réduit la performance.
  - **Prétraitement** : suppression des silences et segmentation en 2 secondes, mais sans distinction entre voyelles et consonnes, ce qui pourrait influencer les résultats.

## Conclusion
Ce projet propose une approche **automatique et scalable** pour la reconnaissance des langues sous-annotées. Des améliorations peuvent être envisagées via :
- **L’augmentation des données** pour améliorer la robustesse du modèle.
- **L’exploration de nouvelles architectures** comme les Transformers ou l’apprentissage auto-supervisé.
- **Une meilleure prise en compte des caractéristiques phonétiques** (voyelles/consonnes) pour affiner la classification.
