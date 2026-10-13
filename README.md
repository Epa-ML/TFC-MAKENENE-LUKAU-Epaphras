# Détection automatique des vulnérabilités réseau à l'aide du Machine Learning

**Auteur** : MAKENENE LUKAU Epaphras  
**Directeur** : Kya KYAMAKYA ing., Ph.D  
**Faculté** : Polytechnique — Université de Kinshasa  
**Année académique** : 2025–2026

---

## Description

Ce dépôt contient l'ensemble des codes Python utilisés pour le Travail de Fin de Cycle (TFC) intitulé :

> **« Évaluation comparative des modèles de Machine Learning pour la détection automatique des intrusions réseau à partir de données de trafic public »**

Quatre modèles classiques de Machine Learning sont comparés sur le jeu de données public **UNSW-NB15** :
- Régression logistique (LR)
- Arbre de décision (DT)
- Forêt aléatoire (RF)
- Machine à vecteurs de support (SVM)

---

## Contenu du dépôt

| Fichier | Description |
|---------|-------------|
| `01_regression_logistique.ipynb` | Prétraitement + entraînement du modèle LR |
| `02_arbre_decision.ipynb` | Prétraitement + entraînement du modèle DT |
| `03_foret_aleatoire.ipynb` | Prétraitement + entraînement du modèle RF |
| `04_svm.ipynb` | Prétraitement + entraînement du modèle SVM |
| `requirements.txt` | Liste des dépendances Python |
| `figures/` | Figures générées (matrices de confusion, courbes ROC) |
| `data/` | Script de téléchargement du dataset UNSW-NB15 |

---

## Jeu de données

Le dataset utilisé est **UNSW-NB15**, généré en 2015 par Moustafa et Slay à l'UNSW Canberra.

- Fichier utilisé : `UNSW_NB15_1.csv` (82 332 échantillons, 45 colonnes)
- Répartition des classes : 44,94 % normal / 55,06 % attaque
- Site officiel : [https://research.unsw.edu.au/projects/unsw-nb15-dataset](https://research.unsw.edu.au/projects/unsw-nb15-dataset)

---

## Prérequis

- Python 3.13
- Jupyter Notebook ou VS Code
- Les bibliothèques listées dans `requirements.txt`

---

## Installation

```bash
# Cloner le dépôt
git clone https://github.com/Epa-ML/TFC-MAKENENE-LUKAU-Epaphras.git
cd TFC-MAKENENE-LUKAU-Epaphras

# Créer un environnement virtuel (optionnel mais recommandé)
python -m venv venv
source venv/bin/activate        # Linux / macOS
venv\Scripts\activate           # Windows

# Installer les dépendances
pip install -r requirements.txt
