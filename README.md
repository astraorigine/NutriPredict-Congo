# NutriPredict Congo

Analyse des facteurs socio-démographiques associés à la malnutrition 
infantile au Congo, à partir des microdonnées réelles de l'Enquête 
Démographique et de Santé (DHS).

![Statut](https://img.shields.io/badge/statut-en%20cours-orange)
![Python](https://img.shields.io/badge/Python-3.14-blue)
![Licence données](https://img.shields.io/badge/données-DHS%20non%20redistribuées-red)

---

## 📋 Contexte

Ce projet est né d'une question simple : pourquoi certains enfants 
sont-ils davantage touchés par la malnutrition que d'autres ?

À partir des microdonnées individuelles de l'Enquête Démographique 
et de Santé (DHS) du Congo, ce projet analyse 4 475 enfants pour 
identifier les facteurs socio-démographiques les plus associés au 
retard de croissance (stunting) — un indicateur clé de la 
malnutrition chronique infantile.

L'analyse combine une étude exploratoire de 7 facteurs 
socio-démographiques avec un modèle de classification supervisée 
visant à estimer le risque de stunting à partir du profil d'un 
ménage — une approche inspirée des méthodes de ciblage utilisées 
par les programmes de santé publique et les ONG nutritionnelles.

## 📊 Résultats clés

| Indicateur | Valeur |
|---|---|
| Enfants analysés | 4 475 |
| Taux de stunting global | 26.7% |
| Écart rural / urbain | 29.7% vs 18.2% |
| Facteur le plus déterminant (multivarié) | Âge de l'enfant (23.4%) |
| Meilleur modèle | Random Forest (F1 = 0.479, ROC-AUC = 0.655) |

## 🗂️ Structure du projet
NutriPredict-Congo/
├── data/
│ ├── raw/ # Données DHS brutes (non incluses, voir data/README.md)
│ └── processed/ # Dataset nettoyé (congo_clean.csv)
├── notebooks/
│ ├── 01_verification_donnees.ipynb
│ ├── 02_nettoyage_fusion.ipynb
│ ├── 03_analyse_exploratoire.ipynb
│ └── 04_modelisation.ipynb
├── outputs/ # Graphiques générés
├── rapport_DHS_NutriPredict_Congo.md
└── requirements.txt


## 🔧 Reproduire l'analyse

### 1. Cloner le dépôt

```bash
git clone https://github.com/astraorigine/NutriPredict-Congo.git
cd NutriPredict-Congo
```

### 2. Créer l'environnement virtuel

```bash
python -m venv venv
venv\Scripts\activate        # Windows
source venv/bin/activate     # macOS / Linux
pip install -r requirements.txt
```

### 3. Obtenir les données DHS

Les microdonnées DHS ne sont pas incluses dans ce dépôt, 
conformément aux conditions d'utilisation du DHS Program. 
Voir [`data/README.md`](data/README.md) pour la procédure d'accès.

### 4. Exécuter les notebooks

Exécuter les notebooks dans l'ordre (01 → 04), chacun étant 
autonome et rechargeant ses propres données.

## 🧪 Méthodologie

| Étape | Description |
|---|---|
| Nettoyage | Traitement des codes aberrants DHS, fusion ménage/enfant |
| Analyse exploratoire | 7 facteurs socio-démographiques analysés |
| Modélisation | Régression Logistique (référence) vs Random Forest |
| Évaluation | F1-score, Recall, ROC-AUC — adaptées au déséquilibre de classes |

## ⚠️ Limites

- Données déclaratives, collectées à un instant donné (2011-12) — 
  pas un système de suivi en temps réel
- Performances du modèle modestes (ROC-AUC = 0.655) — d'autres 
  facteurs non mesurés (alimentation, santé maternelle) jouent 
  probablement un rôle
- Analyse limitée au Congo (Brazzaville) — généralisation à 
  d'autres contextes non testée

## 🔭 Perspectives d'extension

L'accès aux données DHS a également été obtenu pour la RDC 
(Standard DHS 2023-24) et le Cameroun (Standard DHS 2018), en 
vue d'une possible comparaison régionale. Cette extension n'a 
pas été réalisée dans le cadre de cette première itération du 
projet, mais pourrait faire l'objet d'une analyse complémentaire.

## 📄 Conditions d'utilisation des données

Ce projet utilise des microdonnées DHS dans le cadre d'un accès 
académique approuvé. Conformément aux conditions d'utilisation :

- Aucune microdonnée individuelle brute n'est incluse dans ce dépôt
- Seuls le code, les résultats agrégés et les visualisations 
  sont partagés
- Citation officielle requise : *The DHS Program, Congo Standard 
  DHS 2011-12. ICF International, Rockville, Maryland, USA.*

## 👤 Auteur

**MPOY Schekina Lutte-De-Vie**  
Licence 2 Big Data & analyse de données
Université Denis Sassou Nguesso (UDSN), Kintélé, Congo-Brazzaville

## 📚 Source des données

The DHS Program — Demographic and Health Surveys  
[dhsprogram.com](https://dhsprogram.com)