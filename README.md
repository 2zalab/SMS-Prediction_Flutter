# SMS-Prediction_Flutter

## Description

Ce projet vise à développer un modèle de machine learning capable de prédire les messages à envoyer en fonction des messages reçus. Le modèle sera ensuite exporté et déployé dans une application Flutter.

## Contenu du projet

1. **Données**
   - Description des données utilisées pour entraîner le modèle.
   - Méthodes de prétraitement des données.

2. **Modèle de Machine Learning**
   - Algorithme utilisé pour la prédiction des messages.
   - Architecture du modèle.
   - Entraînement et validation du modèle.
   - Exportation du modèle.

3. **Application Flutter**
   - Intégration du modèle dans l'application Flutter.
   - Utilisation du modèle pour prédire les messages en temps réel.

## Prérequis

- Python 3.7 ou supérieur
- Flutter SDK
- Bibliothèques Python : TensorFlow, scikit-learn, pandas, numpy

## Installation

### Étape 1: Cloner le dépôt

```
git clone https://github.com/votre-utilisateur/message-prediction-model.git
cd message-prediction-model
```

### Étape 2: Configurer l'environnement Python

Il est recommandé d'utiliser un environnement virtuel pour installer les dépendances.

```
python3 -m venv env
source env/bin/activate  # Sur Windows: env\Scripts\activate
pip install -r requirements.txt
```

### Étape 3: Préparer les données

Placez vos données de formation dans le dossier `data`. Le fichier de données devrait être au format CSV avec deux colonnes : `message_recu` et `message_envoye`.

### Étape 4: Entraîner le modèle

Exécutez le script d'entraînement pour construire et entraîner le modèle.

```
python train_model.py
```

### Étape 5: Exporter le modèle

Le modèle entraîné sera exporté au format TensorFlow SavedModel. Le fichier sera sauvegardé dans le dossier `exported_model`.

```
python export_model.py
```

## Utilisation du modèle

### Chargement et Prédiction

Vous pouvez charger le modèle exporté et effectuer des prédictions en utilisant le script suivant :

```
import tensorflow as tf

model = tf.keras.models.load_model('exported_model')
prediction = model.predict([votre_message_recu])
```

## Déploiement dans l'application Flutter

### Étape 1: Configurer Flutter

Assurez-vous que Flutter est correctement installé. Suivez les instructions officielles sur [flutter.dev](https://flutter.dev).

### Étape 2: Ajouter le modèle à l'application Flutter

Copiez le dossier `exported_model` dans le répertoire de votre application Flutter.

### Étape 3: Utiliser le modèle dans Flutter

Utilisez le plugin `tflite_flutter` pour charger et utiliser le modèle dans votre application. Ajoutez le plugin dans votre fichier `pubspec.yaml` :

```
dependencies:
  tflite_flutter: ^0.9.0
```

Ensuite, dans votre code Dart, chargez le modèle et effectuez des prédictions :

```
import 'package:tflite_flutter/tflite_flutter.dart';

final interpreter = Interpreter.fromAsset('exported_model/model.tflite');

// Préparez vos données de prédiction ici
var input = [votreMessageRecu];

// Effectuez la prédiction
var output = List.filled(1, 0).reshape([1, 1]);
interpreter.run(input, output);

// Affichez le message prédit
print(output);
```

## Structure du projet

```
message-prediction-model/
├── data/
│   └── messages.csv
├── exported_model/
│   └── model
├── flutter_app/
│   ├── lib/
│   │   └── main.dart
├── models/
│   └── message_prediction_model.py
├── notebooks/
│   └── data_preprocessing.ipynb
├── requirements.txt
├── train_model.py
├── export_model.py
└── README.md
```

## Contribuer

Les contributions sont les bienvenues ! Veuillez ouvrir une issue ou une pull request pour discuter des changements proposés.

## Licence

Ce projet est sous licence MIT. Voir le fichier [LICENSE](LICENSE) pour plus de détails.

### Notes

1. **requirements.txt** : Assurez-vous de créer un fichier `requirements.txt` listant toutes les bibliothèques Python nécessaires.
2. **Fichiers Python** :
   - `train_model.py` : Script pour entraîner le modèle.
   - `export_model.py` : Script pour exporter le modèle entraîné.
   - `message_prediction_model.py` : Fichier contenant la définition et l'architecture du modèle.

### Exemple de fichier `requirements.txt`

```
tensorflow
scikit-learn
pandas
numpy
```
