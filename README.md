# Data-Warehouse-Projet
Création d'une base de données décisionnelles et son cube OLAP à partir d'une base de données commerciale.

# Base de données choisie
La base de données sur laquelle j’ai travaillé est **classicModelsBase** qui est un détaillant de modèles réduits de base de données de voitures classiques. Elle contient des données commerciales typiques telles que les clients, les produits, les commandes client, les lignes de commande client, etc. Et que j’ai trouvé dans un site qui fait des tutoriels sur MySQL.

[Download the Database](https://www.mysqltutorial.org/mysql-sample-database.aspx)

# Entrepôt de données
Le but de créer notre base de données décisionnelles est de répondre à ces principales questions :
+ Quels sont les produits les plus vendus par date et par location ?
+ Quels sont les quantités des produits achetés par clients, par date et par location ?
+ Quels sont les clients ayant effectué le plus nombres d'achats par date et par location ?
+ Quels sont les fournisseurs qui ont réalisé le plus grand nombre de ventes par date et par location ?
+ Quel est le gain total obtenu par date et par location ?

[Schéma de la base de données opérationnelles](Database-Diagram.pdf)

# Dimensions
+ **Dim 1 :** Locations
+ **Dim 2 :** Dates
+ **Dim 3 :** Products
+ **Dim 4 :** Sellers
+ **Dim 5 :** Customers

La table de faits contiendra en plus **des clés étrangères non significatives des tables de dimension** les colonnes suivantes :

+ **orderId** (Si on fait le count de cet élément on va savoir le nombre d’achat réalisé)
+ **quantityOrdered** (La quantité de chaque produit)
+ **priceEach** (Le prix de chaque produit)
+ **globalPrice** (c’est un attribut calculable depuis le produit de quantityOrdered et priceEach)

[Schéma en étoile de la base de données décisionnelles](https://github.com/LearnToCode180/Datawarehouse-Projet/blob/main/sch%C3%A9ma%20en%20%C3%A9toile.pptx)

# Technologies utilisées
+ MySQL Workbench
+ Talend Open Studio (TOS) : Data Integration
+ Power BI : Data Visualisation
+ Pentaho Schema Workbench : Création Cube OLAP
+ TIBCO Jaspersoft Server : Génération du rapport à partir du Cube OLAP crée

# Extraits du travail réalisé

## Alimentation des tables de dimensions et de la table de faits par TOS
+ Dimension **dates** :

![datesALMT](/Images/datesALMT.png)

+ Table de faits **FactSales** :

![fact_Sales](/Images/fact_sellers_ALMT.png)

## Diagrammes obtenus par Power BI
+ Gain total par ville et par année :

![Gain total par ville et par annee](Images/GainTotalParVille.png)

+ Quantité achetée par année :

![QuantiteParAnnee](/Images/QuantiteParAnnee.png)

+ Quantités achetées de chaque produit par mois et par année :

![QuantitésAchetéesDeChaqueProduit](/Images/QuantitésAchetéesDeChaqueProduit.png)

## Création du Cube OLAP par Pentaho Schema Workbench
+ Cube OLAP :

![CubeOLAP](/Images/CubeOLAP.png)

+ La mesure OrderNumber :

![MesureOrderNumber](/Images/MesureOrderNumber.png)

# Rapport à partir du Cube OLAP par Jaspersoft Server
+ Rapport OLAP :

![RapportOLAP](/Images/RapportOLAP.png)

+ Nombre d'ordres fait par le client **Online Diecast Creations Co**  du produit **1936 Mercedes Benz 500k Roadster** où le fournisseur est **Red Start Diecast**  dans **USA, NH, Nashua** à la date **06/01/2003** :

![OrderNumberRapport](/Images/OrderNumberRapport.png)

