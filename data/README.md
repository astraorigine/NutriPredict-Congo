# Données NutriPredict Congo

## Données brutes (data/raw/)

Les fichiers de données brutes DHS ne sont pas inclus dans ce dépôt.  
Ils sont exclus par le .gitignore conformément aux conditions d'utilisation 
du DHS Program (interdiction de redistribution des microdonnées).

### Comment obtenir les données

1. Créer un compte sur [dhsprogram.com](https://dhsprogram.com)
2. Soumettre une demande d'accès motivée 
3. Télécharger les fichiers suivants en format Stata (.dta) :

| Pays | Enquête | Fichier KR | Fichier HR |
|---|---|---|---|
| Congo (Brazzaville) | Standard DHS 2011-12 | CGKR61FL.DTA | CGHR61FL.DTA |
| RDC | Standard DHS 2023-24 | CDKR81FL.dta | CDHR81FL.dta |
| Cameroun | Standard DHS 2018 | CMKR71FL.DTA | CMHR71FL.DTA |

4. Placer les fichiers dans `data/raw/` en respectant la structure :

data/raw/
├── congo2011_12/
│   ├── CGKR61DT/CGKR61FL.DTA
│   └── CGHR61DT/CGHR61FL.DTA
├── rdc2023_24/
└── cameroun2018/

## Données traitées (data/processed/)

Les fichiers dans `data/processed/` sont des datasets nettoyés  
et agrégés, sans données individuelles brutes.  
Ils peuvent être partagés librement.

### Citation obligatoire DHS
The DHS Program, Congo Standard DHS 2011-12.
ICF International, Rockville, Maryland, USA.