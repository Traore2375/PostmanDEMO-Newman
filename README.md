# 🚀 API Automation Project - Postman & Newman

## 📌 Description

Ce projet permet d’automatiser des tests API en utilisant **Postman** et **Newman**, avec génération de rapports HTML et intégration dans Jenkins pour une exécution continue.

---

## 🛠️ Technologies utilisées

* Postman (création des requêtes API)
* Newman (exécution en ligne de commande)
* Node.js
* Jenkins (CI/CD)
* GitHub (versioning)

---

## 📁 Structure du projet

```
📦 POSTMAN
 ┣ 📜 SimpleDemo.postman_collection.json
 ┣ 📜 QA.postman_environment.json
 ┣ 📜 data.json
 ┗ 📜 README.md
```

---

## ⚙️ Prérequis

Installer :

```bash
node -v
npm -v
```

Puis :

```bash
npm install -g newman
npm install -g newman-reporter-htmlextra
```

---

## ▶️ Exécution des tests

### 🔹 Exécution simple

```bash
newman run SimpleDemo.postman_collection.json
```

---

### 🔹 Avec environnement

```bash
newman run SimpleDemo.postman_collection.json -e QA.postman_environment.json
```

---

### 🔹 Avec data file (tests multiples)

```bash
newman run SimpleDemo.postman_collection.json -e QA.postman_environment.json -d data.json
```

---

### 🔹 Avec rapport HTML coloré

```bash
newman run SimpleDemo.postman_collection.json ^
-e QA.postman_environment.json ^
-d data.json ^
-r htmlextra ^
--reporter-htmlextra-export report.html
```

---

## 📊 Rapport

Après exécution, un fichier `report.html` est généré :

* Résumé des tests
* Statistiques (succès / échec)
* Détails des requêtes
* Visualisation colorée

---

## 🔁 Intégration Jenkins

### Étapes :

1. Créer un job Jenkins
2. Lier le repository GitHub
3. Ajouter une étape "Execute Windows batch command"

```bash
newman run SimpleDemo.postman_collection.json ^
-e QA.postman_environment.json ^
-d data.json ^
-r htmlextra ^
--reporter-htmlextra-export report.html
```

4. Publier le rapport HTML avec le plugin **HTML Publisher**

---

## 📌 Fonctionnalités

* Tests API automatisés
* Data-driven testing (JSON)
* Génération de rapports HTML
* Intégration CI/CD avec Jenkins

---

## 💡 Bonnes pratiques

* Ne pas committer les tokens (sécurité)
* Utiliser des variables d’environnement
* Versionner les collections Postman
* Utiliser des data files pour les tests multiples

---

## 👨‍💻 Auteur

Projet réalisé dans le cadre d’un POC d’automatisation API.

---

## 🚀 Améliorations possibles

* Ajout de tests automatisés avancés
* Intégration avec Docker
* Notifications (Slack / Email)
* Pipeline Jenkins (Jenkinsfile)

---
