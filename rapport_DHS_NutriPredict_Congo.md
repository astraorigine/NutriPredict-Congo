# Rapport d'utilisation des données DHS
**Projet :** Déterminants socio-démographiques de la malnutrition 
infantile en République du Congo  
**Auteur :** MPOY Schekina Lutte-de-vie  
**Institution :** Université Denis Sassou N'Guesso (UDSN), Kintélé  
**Email :** mpoyschekinaluttedevie@gmail.com  
**Date de début :** 19 juin 2026  
**Statut :** En cours,document mis à jour progressivement  

---

## 1. Description des données utilisées

### 1.1 Source

Les données utilisées dans ce projet sont issues du Programme 
des Enquêtes Démographiques et de Santé (DHS Program), financé 
par l'USAID. L'accès aux microdonnées a été obtenu dans le cadre 
d'une demande académique approuvée le 22 juin 2026.

### 1.2 Fichiers utilisés

| Pays | Enquête | Fichier | Lignes | Colonnes |
|---|---|---|---|---|
| Congo (Brazzaville) | Standard DHS 2011-12 | CGKR61FL.DTA (Children's Recode) | 9 329 | 1 110 |
| Congo (Brazzaville) | Standard DHS 2011-12 | CGHR61FL.DTA (Household Recode) | 11 632 | 3 194 |

*Les fichiers RDC 2023-24 et Cameroun 2018 seront intégrés 
dans la phase de comparaison régionale.*

### 1.3 Préparation des données

Après chargement des fichiers bruts, les étapes suivantes 
ont été appliquées :

1. **Sélection des variables pertinentes** : 8 variables 
retenues dans KR (Z-scores anthropométriques, identifiants 
démographiques, clés de jointure) et 8 dans HR (caractéristiques 
socio-économiques du ménage).

2. **Traitement des codes aberrants DHS** : 146 valeurs 
>= 9000 sur la variable hw70 (codes 9996, 9998, 9999 
signalant des mesures manquantes ou hors limites) ont été 
remplacées par NaN avant la conversion en Z-scores réels 
(division par 100).

3. **Exclusion des observations sans mesures anthropométriques** : 
4 854 lignes sans Z-score taille/âge (hw70) ont été exclues, 
correspondant à des enfants non présents lors de la mesure. 
Le dataset effectif est de **4 475 enfants mesurés**.

4. **Fusion KR + HR** : Les deux fichiers ont été joints 
sur la clé composite cluster/ménage. La fusion 
est complète, aucun enfant sans correspondance ménage, 
0 valeur manquante introduite.

5. **Construction de la variable cible** : La variable 
binaire `stunting` a été créée selon le seuil OMS standard 
(Z-score taille/âge < -2.0).

### 1.4 Distribution de la variable cible

| Statut | Effectif | Proportion |
|---|---|---|
| Stunting (retard de croissance) | 1 197 | 26.7% |
| Normal | 3 278 | 73.3% |
| **Total** | **4 475** | **100%** |

Un déséquilibre modéré est observé (26.7% de cas positifs). 
La stratégie retenue pour la modélisation est l'utilisation 
de `class_weight='balanced'` dans les modèles scikit-learn.

---

*Les sections suivantes seront complétées au fur et à mesure 
de l'avancement du projet :*
- *Section 2 : Résultats de l'analyse exploratoire*
- *Section 3 : Résultats de la modélisation*
- *Section 4 : Conclusions et limites*