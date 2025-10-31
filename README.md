# TP3 — Outils & Techniques d’apprentissage automatique

Notebook ciblé: `TP3Outils&Technique.ipynb`

Ce README documente UNIQUEMENT le notebook ci‑dessus. Il explique l’objectif, les dépendances, comment l’exécuter, ce que l’on obtient et comment personnaliser/diagnostiquer.

## 🎯 Objectif

Construire et évaluer un pipeline de classification supervisée basé sur un réseau de neurones convolutionnel (CNN), avec:
- Exploration des données et visualisations
- Prétraitements (normalisation, reshape, encodage one‑hot)
- Définition de l’architecture (Conv/Pool/Dense/Dropout)
- Entraînement avec callbacks (ex. early stopping)
- Analyse des courbes d’apprentissage
- Évaluation: accuracy, rapport de classification, matrice de confusion
- Inspection d’exemples mal classés et top‑3 probabilités

Remarque: le notebook reste agnostique du dataset exact (Keras datasets ou données locales) et met l’accent sur la démarche.

## ⚙️ Prérequis

- Python ≥ 3.9 (recommandé: 3.10/3.11)
- Jupyter Notebook/Lab
- Bibliothèques Python courantes:
  - numpy, pandas, matplotlib, seaborn
  - scikit‑learn
  - tensorflow (keras)

Optionnel: GPU/CUDA pour accélérer TensorFlow (non nécessaire pour un petit dataset).

## 🚀 Installation rapide (Windows PowerShell)

Vous pouvez réutiliser l’environnement virtuel existant `.venv` s’il est présent à la racine. Sinon, créez‑en un et installez les dépendances:

```powershell
# Créer et activer un venv (si besoin)
python -m venv .venv
.\.venv\Scripts\Activate.ps1

# Mettre pip à jour et installer les paquets
python -m pip install --upgrade pip
pip install jupyterlab numpy pandas matplotlib seaborn scikit-learn tensorflow
```

Si l’activation est bloquée par la stratégie PowerShell, lancez temporairement:

```powershell
Set-ExecutionPolicy -Scope Process -ExecutionPolicy Bypass
```

## 📦 Données

- Le notebook peut utiliser un dataset intégré à Keras (ex: MNIST/Fashion‑MNIST/CIFAR10) ou un jeu local si précisé dans les premières cellules.
- Les étapes de chargement/partitionnement (train/val/test) sont exécutées dans les premières cellules de code.

## 🧭 Contenu du notebook (par grandes étapes)

1. Exploration des données
   - Dimensions, classes, échantillons illustratifs
2. Prétraitements
   - Normalisation des pixels, reshape des tenseurs, encodage des labels
3. Modèle CNN
   - Convolutions + Pooling, Dense finale, régularisation (Dropout)
   - `model.summary()` pour inspecter les paramètres
4. Entraînement
   - Optimiseur, fonction de perte, métriques, batch size, validation split
   - Callbacks (ex. EarlyStopping / ModelCheckpoint si utilisés)
5. Courbes d’apprentissage
   - Analyse accuracy/loss: sous‑apprentissage vs surapprentissage
6. Évaluation
   - Accuracy test, baseline de comparaison
   - Rapport de classification (precision/recall/F1), matrice de confusion normalisée
7. Interprétation des prédictions
   - Top‑3 probabilités
   - Grille d’exemples mal classés et analyse des confusions récurrentes
8. Conclusion
   - Synthèse des résultats et pistes d’amélioration (data augmentation, tuning)

## ▶️ Exécution

- Ouvrez le dossier du TP, activez votre venv puis lancez Jupyter Lab ou Notebook:

```powershell
.\.venv\Scripts\Activate.ps1
jupyter lab
# ou
jupyter notebook
```

- Ouvrez `TP3Outils&Technique.ipynb` et exécutez les cellules dans l’ordre (Kernel > Restart & Run All recommandé pour une exécution propre).

## ✅ Résultats attendus

- Courbes d’entraînement/validation (accuracy et loss)
- `model.summary()` affiché
- Scores sur l’ensemble de test
- Rapport de classification et matrice de confusion
- Visualisation de quelques erreurs typiques et top‑3 des classes prédites

## 🔧 Personnalisation

- Hyperparamètres: nombre de filtres, taille des kernels, Dropout, batch size, epochs
- Optimiseur et learning rate
- Split validation et early stopping (patience)
- Data augmentation (ex. `ImageDataGenerator`/`tf.image`)

## 🩺 Dépannage

- TensorFlow CPU suffit pour des tests. Pour le GPU, installez les versions CUDA/cuDNN compatibles.
- Erreur d’activation PowerShell: utilisez la commande d’exception temporaire ci‑dessus.
- Mémoire limitée: réduisez batch size/complexité du modèle ou échantillonnez le dataset.

## 🔁 Reproductibilité

- Fixez un seed (numpy/tensorflow) si vous avez une cellule dédiée pour la reproductibilité.
- Note: les entraînements sur GPU peuvent rester légèrement non déterministes.

## 👤 Auteure

Adjaho Sara — TP3 du module « Outils et techniques d’apprentissage automatique ».

---

Ce document concerne exclusivement `TP3Outils&Technique.ipynb`. Pour d’autres TP (Titanic/Heart), voir leurs notebooks/rapports respectifs.
