# Détection automatique des intrusions réseau par Machine Learning

## Travail de Fin de Cycle — Université de Kinshasa

**Auteur :** MAKENENE LUKAU Epaphras  
**Directeur :** KYAMAKYA KYANDOGHERE, ing., Ph.D  
**Institution :** Université de Kinshasa (UNIKIN)  
**Faculté :** Polytechnique  
**Année académique :** 2025–2026

---

## 1. Présentation du projet

Ce dépôt rassemble les notebooks Python, les résultats expérimentaux et les ressources associés au Travail de Fin de Cycle (TFC) intitulé :

**« Évaluation comparative des modèles de Machine Learning pour la détection automatique des intrusions réseau à partir de données de trafic public »**

L'objectif est d'évaluer et de comparer plusieurs algorithmes classiques d'apprentissage automatique pour la classification binaire du trafic réseau, en distinguant les communications normales des communications associées à des attaques.

L'étude repose sur le jeu de données public **UNSW-NB15** et s'intéresse à la fois aux performances prédictives des modèles et à l'influence du traitement du déséquilibre des classes.

## 2. Objectifs de l'étude

Le travail vise à :

1. Comparer les performances de quatre modèles de Machine Learning pour la détection des intrusions réseau.
2. Étudier l'influence du prétraitement et du rééquilibrage des classes par SMOTENC.
3. Examiner les compromis entre précision de détection, faux positifs, faux négatifs et coût de calcul.

## 3. Modèles étudiés

Quatre algorithmes de classification supervisée sont évalués :

| Modèle | Abréviation | Description |
|---|---|---|
| Régression logistique | LR | Modèle linéaire de classification |
| Arbre de décision | DT | Classification fondée sur des règles de décision |
| Forêt aléatoire | RF | Ensemble d'arbres de décision |
| Machine à vecteurs de support | SVM | Classification par séparation optimale, avec noyau RBF |

Chaque algorithme est étudié selon deux configurations :

- **Sans SMOTENC :** apprentissage sans suréchantillonnage synthétique.
- **Avec SMOTENC :** apprentissage intégrant un rééquilibrage adapté aux variables numériques et catégorielles.

L'étude porte ainsi sur **huit configurations expérimentales**.

## 4. Jeu de données UNSW-NB15

Le jeu de données **UNSW-NB15**, développé à l'UNSW Canberra et présenté par Moustafa et Slay en 2015, contient des observations de trafic réseau normal et malveillant.

Les expériences utilisent les partitions officielles suivantes :

| Fichier | Utilisation | Observations |
|---|---|---:|
| `UNSW_NB15_training-set.csv` | Entraînement et validation croisée | 175 341 |
| `UNSW_NB15_testing-set.csv` | Évaluation finale | 82 332 |

Chaque fichier comporte 45 colonnes dans sa version officielle, incluant les variables descriptives et les informations de classification.

La variable `label` sert à la classification binaire :

- `0` : trafic normal ;
- `1` : trafic associé à une attaque.

**Source officielle :** https://research.unsw.edu.au/projects/unsw-nb15-dataset

La séparation officielle entre entraînement et test est conservée afin de disposer d'un ensemble de test indépendant.

## 5. Méthodologie expérimentale

La démarche expérimentale comprend les étapes suivantes :

**Étape 1 — Chargement des données**

Importation des partitions officielles UNSW-NB15 et identification des variables explicatives ainsi que de la variable cible.

**Étape 2 — Prétraitement**

Préparation des variables numériques et catégorielles conformément aux besoins des modèles étudiés.

**Étape 3 — Gestion du déséquilibre des classes**

Comparaison des configurations sans rééquilibrage et avec SMOTENC. Le suréchantillonnage est réservé aux données d'apprentissage et ne doit pas être appliqué à l'ensemble de test.

**Étape 4 — Optimisation des hyperparamètres**

Recherche des configurations d'hyperparamètres au moyen d'une procédure de validation croisée sur les données d'entraînement.

**Étape 5 — Évaluation finale**

Évaluation des modèles retenus sur la partition officielle de test, sans utilisation de cette partition pour l'ajustement des hyperparamètres.

## 6. Métriques d'évaluation

Les modèles sont comparés à partir de plusieurs indicateurs complémentaires :

| Métrique | Rôle |
|---|---|
| Accuracy | Proportion globale des prédictions correctes |
| Precision | Proportion d'attaques correctement identifiées parmi les alertes d'attaque |
| Recall | Proportion des attaques effectivement détectées |
| F1-score | Moyenne harmonique de la précision et du rappel |
| ROC-AUC | Capacité de discrimination entre les classes |
| Matrice de confusion | Analyse des vrais positifs, vrais négatifs, faux positifs et faux négatifs |
| Temps de calcul | Analyse du coût computationnel, lorsque mesuré |

Dans un système de détection d'intrusions, l'analyse des **faux négatifs** et des **faux positifs** est particulièrement importante.

## 7. Organisation du dépôt

```text
TFC-MAKENENE-LUKAU-Epaphras/
│
├── Regression_logistique_OPTIMISE.ipynb
├── Arbre_decision_OPTIMISE.ipynb
├── Foret_aleatoire_OPTIMISE.ipynb
├── SVM_OPTIMISE.ipynb
│
├── UNSW_NB15_training-set.csv
├── UNSW_NB15_testing-set.csv
│
├── resultats_officiels/
├── Photos/
│
├── requirements.txt
├── .gitignore
└── README.md
```

### Description des éléments

| Fichier ou dossier | Description |
|---|---|
| `Regression_logistique_OPTIMISE.ipynb` | Expériences de régression logistique |
| `Arbre_decision_OPTIMISE.ipynb` | Expériences d'arbre de décision |
| `Foret_aleatoire_OPTIMISE.ipynb` | Expériences de forêt aléatoire |
| `SVM_OPTIMISE.ipynb` | Expériences de machine à vecteurs de support |
| `UNSW_NB15_training-set.csv` | Partition officielle d'entraînement |
| `UNSW_NB15_testing-set.csv` | Partition officielle de test |
| `resultats_officiels/` | Résultats expérimentaux exportés |
| `Photos/` | Figures et illustrations associées aux expériences |
| `requirements.txt` | Dépendances Python du projet |
| `.gitignore` | Exclusion des fichiers temporaires |
| `README.md` | Documentation du dépôt |

## 8. Installation

### Prérequis

- Python et un environnement Jupyter compatibles avec les dépendances du projet ;
- Git ;
- Visual Studio Code ou Jupyter Notebook ;
- Les bibliothèques Python répertoriées dans `requirements.txt`.

### Cloner le dépôt

```bash
git clone https://github.com/Epa-ML/TFC-MAKENENE-LUKAU-Epaphras.git
cd TFC-MAKENENE-LUKAU-Epaphras
```

### Créer un environnement virtuel

Sous Windows PowerShell :

```powershell
python -m venv .venv
.\.venv\Scripts\python.exe -m pip install -r requirements.txt
```

Sous Linux ou macOS :

```bash
python3 -m venv .venv
source .venv/bin/activate
python -m pip install -r requirements.txt
```

Les versions exactes des bibliothèques doivent être vérifiées dans l'environnement ayant servi à réaliser les expériences.

## 9. Exécution des expériences

1. Cloner le dépôt et installer les dépendances.
2. Vérifier que les deux fichiers CSV officiels sont présents à la racine du projet.
3. Ouvrir le notebook correspondant au modèle souhaité.
4. Sélectionner l'environnement Python approprié.
5. Exécuter les cellules dans leur ordre d'apparition.
6. Consulter les métriques, figures et résultats générés.

Les chemins relatifs des fichiers CSV supposent que le dossier de travail courant correspond à la racine du dépôt.

**Remarque :** les procédures de validation croisée et d'optimisation des hyperparamètres peuvent nécessiter des ressources de calcul et un temps d'exécution importants.

## 10. Résultats expérimentaux

Les résultats de l'étude sont destinés à permettre une comparaison des huit configurations selon :

- la qualité globale de classification ;
- la capacité de détection des attaques ;
- le nombre de fausses alertes ;
- le nombre d'attaques non détectées ;
- l'influence du rééquilibrage des classes ;
- le coût computationnel, lorsque disponible.

Les résultats détaillés sont regroupés dans le dossier `resultats_officiels/`.

Les valeurs numériques définitives doivent être interprétées à partir des fichiers de résultats et des exécutions des notebooks correspondants.

## 11. Reproductibilité et limites

La reproductibilité des expériences repose notamment sur :

- l'utilisation des partitions officielles UNSW-NB15 ;
- la séparation des données d'entraînement et de test ;
- l'application des transformations apprises uniquement à partir des données d'entraînement ;
- la réalisation du suréchantillonnage à l'intérieur des étapes d'apprentissage ;
- la conservation des paramètres d'optimisation et des résultats expérimentaux ;
- l'identification des versions logicielles utilisées.

Les résultats obtenus sur UNSW-NB15 ne garantissent pas automatiquement des performances équivalentes sur d'autres réseaux ou dans des conditions opérationnelles réelles.

## 12. Utilisation académique

Ce dépôt accompagne un Travail de Fin de Cycle réalisé à la Faculté Polytechnique de l'Université de Kinshasa pendant l'année académique 2025–2026.

Il est destiné à la consultation, à la vérification méthodologique et à la reproduction des expériences dans un cadre scientifique et pédagogique.

**Auteur : MAKENENE LUKAU Epaphras**  
**Université de Kinshasa — Faculté Polytechnique**  
**Année académique 2025–2026**