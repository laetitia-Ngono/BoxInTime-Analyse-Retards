# 📦 BoxInTime - Analyse des Retards de Livraison

<div align="center">

![Python](https://img.shields.io/badge/Python-3776AB?style=for-the-badge&logo=python&logoColor=white)
![Pandas](https://img.shields.io/badge/Pandas-150458?style=for-the-badge&logo=pandas&logoColor=white)
![Power BI](https://img.shields.io/badge/Power_BI-F2C811?style=for-the-badge&logo=powerbi&logoColor=black)
![Scikit Learn](https://img.shields.io/badge/Scikit_Learn-F7931E?style=for-the-badge&logo=scikit-learn&logoColor=white)

**Optimisation logistique par l'analyse de données**  
*Du diagnostic data au pilotage stratégique*

[📊 Dashboard](#-dashboard-interactif) • [📈 Résultats](#-résultats-clés) • [🎯 Recommandations](#-recommandations-stratégiques)

</div>

---

## 📌 À propos du Projet

**BoxInTime**, entreprise e-commerce française spécialisée dans la vente de produits électroniques (smartphones, tablettes, accessoires), connaît une forte croissance (+40% du CA en 3 ans) mais fait face à une **augmentation alarmante des retards de livraison**.

### 🚨 Problématique

- 📍 **2023** : Plus de 25% des commandes livrées en retard
- 📍 **Réclamations clients** : +30%
- 📍 **Impact** : Satisfaction client et image de marque
- 📍 **Coûts** : SAV, compensations, pénalités

### 🎯 Objectifs

- ✅ Identifier les facteurs principaux des retards de livraison
- ✅ Mettre en place des KPI logistiques actionnables
- ✅ Élaborer un dashboard interactif de pilotage
- ✅ Proposer des recommandations stratégiques concrètes

---

## 📊 Dataset & Périmètre

| Caractéristique | Détail |
|----------------|--------|
| **Période d'analyse** | 2019 - 2023 (5 ans) |
| **Volume de données** | 1 825 livraisons |
| **Couverture géographique** | 5 régions françaises |
| **Transporteurs** | UPS, Colissimo, DHL, ChronoPost |
| **Types de produits** | Smartphone, Tablette, PC, Accessoire, Composant |
| **Variables analysées** | 21 variables (14 initiales + 7 créées) |

---

## 🛠️ Méthodologie & Stack Technique

### Méthodologie CRISP-DM

Ce projet suit la méthodologie **CRISP-DM** (Cross-Industry Standard Process for Data Mining) :

1. **Compréhension Business** → Analyse du contexte BoxInTime
2. **Compréhension Données** → Exploration du dataset (1 825 livraisons)
3. **Préparation Données** → Nettoyage, variables dérivées
4. **Modélisation ML** → Régression logistique (prédiction retards)
5. **Évaluation** → AUC, matrice de confusion, insights
6. **Déploiement** → Dashboard Power BI + Recommandations

### Stack Technique

| Outil | Usage |
|-------|-------|
| **Python** | Analyse exploratoire : `pandas`, `numpy`, `matplotlib`, `seaborn` |
| **Scikit-learn** | Modélisation prédictive (Régression Logistique) |
| **Power BI** | Dashboard interactif 3 pages + 9 mesures DAX |
| **Gestion de projet** | Trello, Teams, Google Drive |

---

## 🔍 Résultats Clés

### 📈 Performance Globale

| KPI | Valeur | Tendance |
|-----|--------|----------|
| **Taux de retard global** | **17,1%** | 🔴 +109% (2019→2023) |
| **Livraisons en retard** | **312 / 1 825** | 1 livraison sur 6 |
| **Retard moyen** | **2,59 jours** | ➡️ Stable |
| **Livraisons à haut risque (ML)** | **124** | ⚠️ Probabilité > 50% |

### 🎯 Top 3 Facteurs Identifiés

#### 1️⃣ Combinaisons Région × Transporteur (Impact : CRITIQUE)

| Rang | Combinaison | Taux de retard |
|------|-------------|----------------|
| 🥇 | **PACA × UPS** | **28,4%** |
| 🥈 | **IDF × ChronoPost** | **24,7%** |
| 🥉 | **AURA × UPS** | **23,9%** |

> 💡 **Insight** : La pire combinaison (PACA × UPS) affiche un taux de retard **11,3 points** au-dessus de la moyenne globale.

#### 2️⃣ Délais Promis Inadaptés (Impact : ÉLEVÉ)

```
Délai 2 jours → 18,6% de retards
Délai 3 jours → 17,9% de retards
Délai 5 jours → 16,8% de retards

⚠️ Paradoxe : Les délais courts génèrent PLUS de retards !
```

#### 3️⃣ Type de Produit (Impact : MOYEN)

| Produit | Taux retard | Risque ML |
|---------|-------------|-----------|
| **Tablette** | 20,6% | 56,2% |
| PC Portable | 18,4% | 51,3% |
| Smartphone | 17,0% | 48,7% |
| Composant | 15,8% | 45,2% |
| Accessoire | 13,2% | 42,1% |

---

## 🤖 Machine Learning - Prédiction des Retards

### Régression Logistique

**Objectif** : Anticiper les livraisons à risque **avant expédition**

**Résultats** :
- ✅ **124 livraisons à haut risque** identifiées (probabilité > 50%)
- ✅ **Produit le plus à risque** : Tablette (56,2%)
- ✅ **Transporteur le plus à risque** : UPS
- ✅ **Combinaison critique** : PACA × UPS × Tablette

**Performance du modèle** :
```python
# Métriques clés
AUC-ROC Score : ~0.75
Variables importantes : Région, Transporteur, Type_Produit, Délai_Prévu
Identification efficace des combinaisons à risque
```

---

## 📊 Dashboard Interactif

Le dashboard Power BI comprend **3 pages interactives** :

### 📄 Page 1 : Vue d'Ensemble
- 🔢 **KPI Cards** : Taux retard, Retard moyen, Nb livraisons
- 📊 **Graphiques barres** : Taux de retard par Région / Transporteur
- 🗺️ **Tableau** : Combinaisons à risque

### 📄 Page 2 : Analyse Temporelle
- 📈 **Courbe d'évolution** : 2019-2023
- 📅 **Saisonnalité** : Analyse mensuelle
- 📦 **Distribution** : Par Produit & Canal

### 📄 Page 3 : Gestion de Risque ML
- 🔥 **Heatmap** : Région × Transporteur
- ⚠️ **KPI Risque** : 124 livraisons, probabilité moyenne 49,4%
- 📋 **Tableau détaillé** : Livraisons à haut risque

**Filtres dynamiques** : Année, Région, Transporteur, Type de produit

---

## 🎯 Recommandations Stratégiques

### 🚀 Plan d'Action sur 12 Mois

| Phase | Timing | Actions | Impact estimé |
|-------|--------|---------|---------------|
| **Phase 1 : Quick Wins** | M1-M2 | Déploiement dashboard<br>Ajustement délais<br>Traitement prioritaire | -3 à -4% |
| **Phase 2 : Test A/B** | M2-M5 | Test sur 20% du trafic<br>Suivi hebdomadaire | -2 à -3% |
| **Phase 3 : Déploiement** | M3-M6 | Négociation SLA<br>Réaffectation combinaisons | -5 à -7% |
| **Phase 4 : Optimisation** | M7-M12 | Suivi mensuel<br>Ajustements<br>Bilan 12 mois | Stabilisation |

### 💰 ROI Estimé

```
💸 Investissement nécessaire : ~7 600 €
💰 Gains estimés (an 1) : ~60 000 €
📈 ROI : 1 250%

Détail des gains :
• Réduction coûts SAV/compensations : ~24 000 €
• Rétention clients : ~36 000 €
```

### ✅ 6 Recommandations Prioritaires

#### 1. Réaffecter les Combinaisons à Risque (CRITIQUE)
```
PACA × UPS (28,4%) → PACA × Colissimo (13,2%)
IDF × ChronoPost (24,7%) → IDF × DHL (17,1%)
AURA × UPS (23,9%) → AURA × Colissimo (14,8%)
```

#### 2. Ajuster les Délais Promis (ÉLEVÉE)
- Passer de 2j à 3j pour Tablettes et PC Portables
- Augmenter à 4j pour les régions éloignées (PACA, AURA)

#### 3. Renégocier les Contrats SLA (ÉLEVÉE)
- Inclure des pénalités si retard > 20% sur une région
- Bonus si performance > 90% sur 6 mois consécutifs

#### 4. Surveillance Produits Sensibles (MOYENNE)
- Traitement prioritaire pour les Tablettes
- Emballage renforcé + assurance tracking

#### 5. Diversifier les Transporteurs (MOYENNE)
- Réduire la dépendance à UPS et Colissimo
- Tester des acteurs régionaux performants

#### 6. Déployer le Dashboard Prédictif (ÉLEVÉE)
- Suivi mensuel des KPI par la Direction Logistique
- Alertes automatiques pour combinaisons critiques

---

## 👥 Équipe Projet

| Membre | Rôle | Contributions |
|--------|------|---------------|
| **Clara DJAFA** | Chef de projet & Analyste Python | Pilotage, Exploration Python |
| **Laetitia NGONO** | Expert Power BI & Data Viz | Dashboard 3 pages, 9 mesures DAX |
| **Magalie ANGONO** | Data Scientist & ML | Modélisation ML, Score risque |
| **Hélène ZHANG** | Rédacteur & Expert métier | KPI, Recommandations |

### 📅 Timeline

**15 déc 2024 → 10 fév 2025** (57 jours)

```
├── 15-17 déc : Note de cadrage
├── 18-23 déc : Compréhension données
├── 01-06 jan : Préparation données
├── 07-16 jan : Analyse & ML
├── 17-21 jan : Évaluation & Insights
├── 22 jan-03 fév : Dashboard Power BI
├── 30 jan-04 fév : Présentation
└── 10 fév 2025 : 🎓 SOUTENANCE
```

---

## 📚 Livrables

| Livrable | Description | Lien |
|----------|-------------|------|
| 📘 **Note de Cadrage** | Contexte, objectifs, méthodologie CRISP-DM | [PDF](documentation/Note_Cadrage_BoxInTime.pdf) |
| 📅 **Planning Projet** | Timeline détaillée, répartition des rôles | [PDF](documentation/Planning_Projet_BoxInTime.pdf) |
| 🐍 **Notebook Python** | Analyse exploratoire + Modélisation ML | [.py](notebooks/BoxInTime_Notebook_Python.py) |
| 📊 **Dashboard Power BI** | 3 pages interactives + 9 mesures DAX | [.pbix](dashboards/BoxIn_time_dashboard.pbix) |
| 📄 **Rapport d'Analyse** | Synthèse complète des résultats | [PDF](documentation/Rapport_Analyse_BoxInTime.pdf) |
| 🎨 **Présentation** | Support de soutenance (24 slides) | [PDF](documentation/Présentation_Projet_BoxInTime.pdf) |

---

## 💡 Insights Métier

### 🔑 Constats Clés

✅ **83% des livraisons restent à l'heure** → Pas de défaillance systématique  
⚠️ **Retards concentrés** sur certaines combinaisons Région × Transporteur  
📈 **Problème structurel** : Hausse continue depuis 2019 (+109%)  
🎯 **Causes organisationnelles** : Non liées au poids, volume ou prix  
🚚 **Densité logistique critique** : IDF et AURA concentrent les risques

### 💰 Impact Financier

```
CA généré (2019-2023) : 693 000 €
Perte due aux retards : 24 000 € (3,4% du CA)

Si réduction de 10% du taux de retard :
→ Gain estimé : 60 000 € / an
→ ROI projet : 1 250%
```

---

## 🔄 Améliorations Futures

- [ ] Intégrer des données météo (impact sur les retards ?)
- [ ] Analyser l'impact des jours fériés et vacances scolaires
- [ ] Modèle ML plus avancé (Random Forest, XGBoost)
- [ ] Analyse de sentiment des avis clients
- [ ] Optimisation des tournées de livraison
- [ ] Prédiction de la demande par région/produit

---

## 📞 Contact

**Laetitia NGONO**  
🎓 Master Data Marketing - INSEEC Paris  
🔗 LinkedIn : [Laetitia NGONO](https://www.linkedin.com/in/laetitia-n)  
📧 Email : ngonolaetitia2811@gmail.com  
💼 Portfolio : [Laetitia-Ngono](https://github.com/Laetitia-Ngono)

---

## 📜 Informations

Ce projet a été réalisé dans un cadre académique pour **INSEEC Paris**.  
Les données utilisées sont fictives ou anonymisées conformément au RGPD.

---

<div align="center">

**⭐ Si ce projet vous a plu, n'hésitez pas à lui donner une étoile !**

*Réalisé avec passion par l'équipe 4* 🚀

</div>
