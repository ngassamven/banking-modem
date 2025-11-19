# 🏦 Pile de données moderne – Domaine Bancaire
**Snowflake • DBT • Apache Airflow • Apache Kafka • Debezium • Python • Docker • Git • CI/CD**

## 📌 Aperçu du projet
Ce projet présente un pipeline complet de **pile de données moderne** appliqué au domaine bancaire.  
Il simule des données clients, comptes et transactions, capture les changements en temps réel, applique des transformations analytiques et fournit des insights dans un environnement entièrement orchestré et automatisé.

👉 **Pensez-y comme à un véritable écosystème de données bancaires moderne**, construit avec les meilleures pratiques utilisées en production.

---

## 🏗️ Architecture
Le pipeline fonctionne selon le flux suivant :

1. **Data Generator** → Simulation de clients, comptes et transactions (Faker).  
2. **Kafka + Debezium** → Capture de données de changement (CDC) depuis PostgreSQL et stockage dans MinIO.  
3. **Airflow** → Orchestration, ingestion, planification de snapshots et chargements Snowflake.  
4. **Snowflake** → Data Warehouse structuré en *Bronze → Silver → Gold*.  
5. **DBT** → Transformations, modèles analytiques, tests, snapshots SCD Type 2.  
6. **CI/CD GitHub Actions** → Tests automatiques, compilation et déploiement.

---

## ⚡ Pile technologique
- **Snowflake** – Cloud Data Warehouse  
- **DBT** – Transformations, tests, snapshots SCD2  
- **Apache Airflow** – Orchestration & planification  
- **Apache Kafka + Debezium** – Streaming & CDC  
- **MinIO** – Stockage objet compatible S3  
- **PostgreSQL** – Système OLTP source  
- **Python (Faker)** – Génération de données synthétiques  
- **Docker / Docker Compose** – Environnement conteneurisé  
- **GitHub Actions** – CI/CD automatisé  

---

## ✅ Fonctionnalités principales
- Base OLTP PostgreSQL entièrement fonctionnelle (ACID)  
- Génération de données bancaires réalistes :  
  - Clients  
  - Comptes  
  - Transactions  
- CDC en temps réel via Kafka + Debezium  
- Modélisation analytique avec DBT (staging, dimensions, faits)  
- Snapshots SCD2 pour l’historisation  
- Pipelines Airflow automatisés  
- CI/CD pour validation et déploiement des modèles  

---

## 📂 Structure du dépôt
banking-modern-datastack/
├── .github/workflows/ # Pipelines CI/CD (ci.yml, cd.yml)
├── banking_dbt/ # Projet DBT
│ ├── models/
│ │ ├── staging/ # Modèles de staging
│ │ ├── marts/ # Dimensions & faits
│ │ └── sources.yml
│ ├── snapshots/ # Snapshots SCD2
│ └── dbt_project.yml
├── consumer/
│ └── kafka_to_minio.py
├── data-generator/ # Génération de données Faker
│ └── faker_generator.py
├── docker/
│ ├── dags/ # DAGs Airflow
├── kafka-debezium/ # Connecteurs Kafka + CDC
│ └── generate_and_post_connector.py
├── postgres/ # Schémas OLTP
│ └── schema.sql
├── docker-compose.yml
├── dockerfile-airflow.dockerfile
└── README.md


---

## ⚙️ Implémentation – Étapes détaillées  

### 1. Simulation des données
- Génération de clients, comptes et transactions à l’aide de Faker.  
- Insertion dans PostgreSQL pour simuler un véritable système bancaire OLTP.  
- Configuration contrôlée via fichier `.config.yaml`.

### 2. Kafka + Debezium (CDC)
- Configuration de Kafka Connect et Debezium pour capturer les changements PostgreSQL (WAL).  
- Streaming des événements CDC vers MinIO.

### 3. Orchestration Airflow
- Développement de DAGs pour :  
  - Ingestion MinIO → Snowflake (Bronze)  
  - Chargements incrémentaux  
  - Snapshots planifiés SCD2  

### 4. Snowflake Data Warehouse
- Architecture multi-couches : Bronze, Silver, Gold.  
- Schémas et tables de staging.

### 5. Transformations DBT
- Modèles de staging normalisés  
- Modèles analytiques : faits et dimensions  
- Snapshots SCD2 pour historisation  
- Tests intégrés (unique, not null, relations)

### 6. CI/CD (GitHub Actions)
- **ci.yml** : linting, compilation DBT, exécution des tests  
- **cd.yml** : déploiement des DAGs & modèles DBT après merge  

---

## 📊 Résultats livrables
- Pipeline complet CDC : **Postgres → Kafka → MinIO → Snowflake**  
- Modèles DBT (staging, marts, snapshots)  
- DAGs Airflow orchestrés et planifiés  
- Données bancaires synthétiques réalistes  
- Pipeline CI/CD garantissant qualité et fiabilité  

---

## 👤 Auteur
**Venceslas NGASSAM**  
📧 Contact : *venceslasngassam@gmail.com*  
🔗 LinkedIn : *www.linkedin.com/in/venceslas-osee-ngassam-kate-data-engineer*

