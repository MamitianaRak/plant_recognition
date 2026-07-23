# 🌿 Plant Recognition

Application web de reconnaissance de plantes par deep learning : upload d'une photo, classification automatique via un CNN (TensorFlow/Keras), et historique des analyses.

## Fonctionnalités

- **Upload d'image** via une API Flask (`/predict`) : redimensionnement, normalisation et inférence en temps réel.
- **Classification CNN** entraîné sur 29 espèces de plantes (aloe vera, banane, manioc, gingembre, papaye, pastèque, tabac, etc.).
- **Historique des analyses** persisté en base SQLite via SQLAlchemy (nom d'utilisateur, plante détectée, score de confiance, image).
- **Pipeline d'entraînement** complet : extraction du dataset, chargement/visualisation des images, entraînement et sauvegarde du modèle.

## Stack technique

- **Backend** : Flask, Flask-SQLAlchemy
- **Machine Learning** : TensorFlow / Keras (CNN), NumPy, Pillow
- **Base de données** : SQLite
- **Visualisation** : Matplotlib

## Architecture du projet

```
plant_recognition/
├── app.py            # API Flask (upload, prédiction, historique)
├── extract_data.py   # Extraction du dataset (zip -> data/)
├── load_data.py       # Chargement et visualisation des images du dataset
├── train_model.py     # Entraînement du modèle CNN et sauvegarde (model/model.h5)
├── test_api.py        # Script de test de l'endpoint /predict
└── requirements.txt
```

## Installation

```bash
git clone https://github.com/MamitianaRak/plant_recognition.git
cd plant_recognition
python -m venv venv
source venv/bin/activate  # Windows : venv\Scripts\activate
pip install -r requirements.txt
```

## Dataset

Le modèle est entraîné sur le dataset [Plants Type Datasets](https://www.kaggle.com/) (Kaggle). Télécharger le dataset, placer l'archive à la racine sous le nom `dataplante.zip`, puis l'extraire :

```bash
python extract_data.py
```

## Entraînement du modèle

```bash
python train_model.py
```

Le modèle entraîné est sauvegardé dans `model/model.h5`, chargé ensuite par l'API Flask.

## Lancer l'application

```bash
python app.py
```

L'application est accessible sur `http://127.0.0.1:5000`.

- `/` — page d'upload d'image
- `/predict` — endpoint POST de prédiction
- `/history` — historique des analyses effectuées

## Tester l'API

```bash
python test_api.py
```

## Espèces reconnues

Aloe vera, banane, bilimbi, cantaloup, manioc, noix de coco, maïs, concombre, curcuma, aubergine, galanga, gingembre, goyave, chou kale, haricot long, mangue, melon, orange, riz, papaye, piment, ananas, pomelo, échalote, soja, épinard, patate douce, tabac, pomme d'eau, pastèque.
