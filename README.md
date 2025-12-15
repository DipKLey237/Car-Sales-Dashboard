# 🚗 Car Sales Dashboard - Power BI

![Power BI]
![Excel]
![DAX]

## 📋 Vue d'ensemble

Dashboard interactif Power BI analysant les performances de vente d'automobiles sur la période 2022-2023. Ce projet démontre ma maîtrise des outils de Business Intelligence et de la visualisation de données dans un contexte métier réaliste.

---

## 🎯 Objectifs du projet

Créer un tableau de bord permettant de :
- **Suivre les KPIs** essentiels (ventes, prix moyen, volume)
- **Analyser les tendances** temporelles et géographiques
- **Identifier les segments** les plus performants (modèles, couleurs, concessions)
- **Faciliter la prise de décision** stratégique pour la direction commerciale

---

## 📊 Métriques clés implémentées

### 1️⃣ Sales Overview (Vue d'ensemble)
| Métrique            | Valeur  | Variation   |
|---------------------|---------|-------------|
| **YTD Total Sales** | $371,2M | +23,59% YOY |
| **MTD Total Sales** | $54,28M |      -      |
| **YTD vs PYTD**     | +$70,8M |      -      |

**Justification** : Mesure la santé financière globale et permet de comparer la performance actuelle aux objectifs annuels et à l'année précédente.

---

### 2️⃣ Average Price Analysis
| Métrique              | Valeur  | Variation |
|-----------------------|---------|-----------|
| **YTD Average Price** | $28,0K  |  -0,79%   |
| **MTD Average Price** | $28,26K |     -     |

**Justification** : Indicateur de positionnement stratégique. La baisse du prix moyen (-0,79%) malgré la hausse des ventes (+23,59%) révèle une stratégie orientée volume ou un shift vers des modèles plus accessibles.

---

### 3️⃣ Cars Sold Metrics (Volume)
| Métrique          | Valeur | Variation   |
|-------------------|--------|-------------|
| **YTD Cars Sold** |  13,3K | +24,57% YOY |
| **MTD Cars Sold** |  1,92K |     -       |

**Justification** : Le volume est supérieur à la croissance du CA, confirmant l'analyse du prix moyen. Essentiel pour la gestion des stocks et la planification de production.

---

## 📈 Visualisations implémentées

### 📉 YTD Weekly Trend
- **Type** : Line chart
- **Objectif** : Identifier la saisonnalité et les pics d'activité
- **Insight** : Pic à 14,9M en semaine 40, permettant d'anticiper les périodes de forte demande

### 🥧 YTD Sales by Body Style
- **Type** : Donut chart
- **Segments** : SUV (dominant ~35%), Hatchback (~25%), Sedan (~20%), Passenger, Hardtop
- **Objectif** : Optimiser le mix produit et adapter les stocks

### 🎨 YTD Sales by Color
- **Type** : Donut chart  
- **Top 3** : Pale White (~40%), Black (~30%), Red (~20%)
- **Objectif** : Gestion des stocks de peinture et compréhension des préférences consommateurs

### 🗺️ YTD Sales by Dealer Region
- **Type** : Map visualization (Bing Maps)
- **Régions** : Pasco, Aurora, Scottsdale, Austin, Janesville, Middletown, Greenville
- **Objectif** : Allocation territoriale des ressources et identification des zones à potentiel

### 📊 Company-Wise Sales Trend
- **Type** : Table avec bar charts intégrés
- **Top performers** : Dodge (6,74%), Chevrolet (7,30%), Chrysler (4,31%)
- **Objectif** : Comparer les marques et optimiser les partenariats constructeurs

### 🔍 Detailed Sales Grid
- **Type** : Table détaillée
- **Colonnes** : Car_id, Date, Customer Name, Dealer, Company, Color, Model, Total Sales
- **Objectif** : Drill-down pour analyses approfondies et vérification transactionnelle

---

## 🛠️ Compétences techniques développées

### Power Query
- ✅ Connexion et import de données Excel
- ✅ Nettoyage et transformation des données
- ✅ Création d'une **Calendar Table** personnalisée
- ✅ Gestion des relations (clés primaires et étrangères)

### DAX (Data Analysis Expressions)
```dax
// Exemples de mesures créées

YTD Total Sales = TOTALYTD(SUM(Sales[Total_Sales]), 'Calendar'[Date])

MTD Total Sales = TOTALMTD(SUM(Sales[Total_Sales]), 'Calendar'[Date])

PYTD Total Sales = CALCULATE(
    [YTD Total Sales],
    SAMEPERIODLASTYEAR('Calendar'[Date])
)

YOY Growth = DIVIDE(
    [YTD Total Sales] - [PYTD Total Sales],
    [PYTD Total Sales],
    0
)

YTD Average Price = AVERAGEX(
    FILTER(Sales, Sales[Date] <= MAX('Calendar'[Date])),
    Sales[Total_Sales]
)
```

### Formules DAX utilisées
- **CALENDAR** : Génération de la table calendrier
- **IF** : Logique conditionnelle
- **SUM / SUMX** : Agrégations simples et itératives
- **COUNT** : Comptage de véhicules
- **CALCULATE** : Modification du contexte de filtre
- **SAMEPERIODLASTYEAR** : Comparaisons temporelles
- **CONCATENATE** : Création de clés composites

### Visualisation & Design
- 🎨 Création d'un arrière-plan personnalisé
- 📊 Configuration avancée des visuels
- 🎯 Mise en forme conditionnelle dynamique
- 🧭 Navigation entre pages (Overview / Details)
- 🗺️ Intégration de cartes Bing Maps

---

## 🗂️ Structure du projet

```
Car-Sales-Dashboard/
│
├── Data/
│   └── car_data.xlsx              # Dataset source (2022-2023)
│
├── Dashboard/
│   └── Car_Sales_Dashboard.pbix   # Fichier Power BI
│
├── Images/
│   ├── dashboard_overview.png     # Screenshot page Overview
│   └── dashboard_details.png      # Screenshot page Details
│
└── README.md                       # Documentation
```

---

## 🚀 Comment utiliser ce projet

### Prérequis
- Power BI Desktop (version gratuite suffisante)
- Microsoft Excel (pour consulter les données sources)

### Installation
1. Cloner le repository
```bash
git clone https://github.com/[votre-username]/car-sales-dashboard.git
```

2. Ouvrir le fichier `.pbix` avec Power BI Desktop

3. Rafraîchir les données si nécessaire (Accueil > Actualiser)

4. Explorer les pages **Overview** et **Details**

---

## 🎓 Difficultés surmontées

### 1. Compréhension du dataset
- Analyse approfondie de 13 000+ lignes de transactions
- Identification des colonnes clés et leurs relations

### 2. Création de la Calendar Table
- Construction d'une table de dates continue pour les calculs temporels DAX
- Établissement des relations avec la table principale

### 3. Modélisation des données
- Définition de la clé primaire (Car_id)
- Création des relations avec les tables de dimension
- Optimisation du modèle en étoile (star schema)

### 4. Formules DAX avancées
- Compréhension des contextes de ligne et de filtre
- Implémentation des comparaisons YOY et YTD
- Gestion des erreurs de division par zéro

### 5. Mise en forme conditionnelle
- Création de règles dynamiques basées sur les performances
- Application de gradients de couleurs pour les bar charts

### 6. Design personnalisé
- Création d'un arrière-plan cohérent sur Canva/PowerPoint
- Harmonisation de la charte graphique

---

## 📚 Sources d'apprentissage

- **Tutoriel YouTube** : [Tutorial]
- **Documentation Microsoft** : Power BI & DAX
- **Communauté** : Power BI Community Forum

---

## 🎯 Perspectives d'amélioration

- [ ] Ajout de filtres dynamiques par année/trimestre
- [ ] Intégration de prévisions avec fonctions DAX (FORECAST)
- [ ] Analyse de cohorte client (récurrence d'achat)
- [ ] Export automatique vers Excel avec Power Automate
- [ ] Ajout d'une page "Dealer Performance" détaillée
- [ ] Implémentation de seuils d'alerte (KPI en dessous des objectifs)

---

## 👤 Auteur

**NGANGUE Dippah Olivier**  
🎯 En reconversion vers Data Analyst  
📧 [ndmandfred3@gmail.com]  
💼 [LinkedIn](https://www.linkedin.com/in/ngangue-olivier)  
🐙 [GitHub](https://github.com/DipKLey237/portfolio)

---

## 🙏 Remerciements

Merci à la communauté Power BI pour les ressources et tutoriels, ainsi qu'au créateur du tutoriel YouTube qui m'a guidé dans ce projet d'apprentissage.

---

⭐ **Si ce projet vous a été utile, n'hésitez pas à le star !**
