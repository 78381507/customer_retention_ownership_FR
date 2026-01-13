# Système Customer Retention Ownership

**Résumé exécutif en français du système d'ownership de la rétention client**

---

## Documentation

**[Résumé Exécutif](https://github.com/78381507/customer_retention_ownership_FR/blob/main/File_02_Resume_Executif/resume_executif.md)**

Ce document de 2 pages présente :
- Le problème business résolu
- L'architecture de la solution
- La valeur apportée à chaque équipe (Marketing, Produit, Finance, Data)
- Le périmètre de responsabilité assumé
- Les limites explicites du système

**[Documents annexes](https://github.com/78381507/customer_retention_ownership_FR/tree/main/File_03_Docs)**
- Diagramme pipeline (retention_pipeline_FR.png)
- Note annexe définition Customer Retention (PDF)

---

## Objectif

Ce repository présente la **vision métier** et l'**impact business** du système Customer Retention Ownership.

Le système permet de :
- Détecter les clients à risque **30 à 45 jours avant** leur désengagement, selon le cycle d'achat
- Déclencher des **alertes automatisées** sans fatigue décisionnelle
- Assurer l'**ownership complet** de la métrique de rétention (données → décisions)

---

## Documentation technique complète

L'implémentation technique complète (architecture SQL, règles de calcul, contrôles qualité, procédures de déploiement) est documentée en anglais.

**Accès disponible sur demande :**
- Email : tilkinanalytics@gmail.com
- LinkedIn : [François Tilkin](https://www.linkedin.com/in/françois-tilkin-1667b138a/)

---

## Validation

Le système a été validé sur un dataset e-commerce réel (UK Online Retail).

**[Voir les résultats de validation](https://github.com/78381507/customer_retention_ownership_FR/blob/main/File_04_Test_Resultats/validation_systeme.md)**

- 397 884 transactions analysées
- 4 338 clients segmentés
- 5 couches SQL exécutées avec succès
- 708 clients ACTIFS identifiés à risque (early warning)

---

## Visualisation

![Architecture du système](https://github.com/78381507/customer_retention_ownership_FR/blob/main/File_03_Docs/retention_pipeline_FR.png)

*Architecture décisionnelle en 5 couches : Faits → Statut → Risque → Tendances → Actions*

---

## Auteur

**François Tilkin**  
Data Analyst | Customer Retention Ownership  

**Portfolio :**
- UK Retail Europe Analytics System (dashboards Looker Studio + automatisation Make.com)
- Customer Retention Ownership (architecture décisionnelle 5-layer)

**Certifications :**
- Google Data Analytics Professional Certificate (93%)
- IBM Data Analyst Professional Certificate (90%)

**Contact :**
- Email : tilkinanalytics@gmail.com
- LinkedIn : [François Tilkin](https://www.linkedin.com/in/françois-tilkin-1667b138a/)

---

**Note sur la langue :**  
*Le système est documenté en anglais car il s'agit d'un référentiel technique. La logique métier, les décisions et les responsabilités associées sont expliquées en français pour garantir une compréhension immédiate des équipes.*
