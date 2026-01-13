# Validation du Système Customer Retention Ownership

**Test réalisé sur données e-commerce réelles**

---

## Dataset de validation

| Attribut | Valeur |
|----------|--------|
| **Source** | UCI Online Retail Dataset |
| **Période** | Décembre 2010 — Décembre 2011 |
| **Transactions analysées** | 397 884 |
| **Clients uniques** | 4 338 |
| **Chiffre d'affaires total** | £8 911 407 |
| **Date de référence** | 9 décembre 2011 |

---

## Résultats par couche

### Couche 1 — Faits clients (base_customers)

Agrégation des données transactionnelles en une vue stable par client.

| Contrôle qualité | Résultat |
|------------------|----------|
| Doublons | 0 |
| Valeurs NULL | 0 |
| Valeurs négatives | 0 |
| Incohérences de dates | 0 |

---

### Couche 2 — Statut de rétention (retention_snapshot)

Classification des clients selon leur récence d'achat.

| Statut | Clients | Pourcentage |
|--------|---------|-------------|
| **ACTIF** (≤30 jours) | 1 667 | 38,4% |
| **À RISQUE** (31-90 jours) | 1 222 | 28,2% |
| **INACTIF** (>90 jours) | 1 449 | 33,4% |

Distribution conforme aux benchmarks e-commerce (ACTIF 20-40%, À RISQUE 15-30%, INACTIF 30-60%).

---

### Couche 3 — Détection de risque (churn_detection)

Identification des signaux comportementaux de désengagement.

| Niveau de risque | Clients | Pourcentage |
|------------------|---------|-------------|
| **ÉLEVÉ** (≥50 pts) | 599 | 13,8% |
| **MOYEN** (20-49 pts) | 678 | 15,6% |
| **FAIBLE** (0-19 pts) | 3 061 | 70,6% |

**Valeur ajoutée du système (early warning) :**

| Situation | Clients |
|-----------|---------|
| Clients ACTIFS mais à risque ÉLEVÉ | 30 |
| Clients ACTIFS mais à risque MOYEN | 678 |

Ces 708 clients apparaissent "sains" dans un dashboard classique (dernière commande < 30 jours) mais présentent des signaux comportementaux de désengagement. **C'est précisément la valeur du système : détecter ces clients avant qu'ils ne basculent.**

---

### Couche 4 — Évolution des cohortes (cohort_retention_evolution)

Suivi de la rétention par cohorte d'acquisition sur 12 mois.

| Contrôle qualité | Résultat |
|------------------|----------|
| Cohortes suivies | 13 |
| Rétention M+0 | 100% (conforme) |
| Rétention > 100% | 0 (aucune anomalie) |

**Exemple — Cohorte décembre 2010 (885 clients) :**

| Maturité | Rétention |
|----------|-----------|
| M+0 | 100% |
| M+1 | 36,6% |
| M+3 | 38,4% |
| M+6 | 36,3% |
| M+12 | 28,5% |

Courbe de rétention réaliste et exploitable pour le pilotage stratégique.

---

### Couche 5 — Logique d'alerte (alert_logic)

Évaluation des conditions de déclenchement d'alerte.

| Métrique | Valeur |
|----------|--------|
| % À RISQUE actuel | 28,17% |
| % À RISQUE baseline (7 jours) | 26,11% |
| Variation relative | +7,89% |
| Seuil WARNING | +15% |
| Seuil CRITICAL | +25% |
| **Alerte déclenchée** | Non |

Résultat attendu : la variation de +7,89% est inférieure au seuil d'alerte. Le système filtre correctement le bruit.

---

## Synthèse

| Couche | Contrôles | Résultat |
|--------|-----------|----------|
| 1 — Faits | 4/4 | ✓ |
| 2 — Statut | 5/5 | ✓ |
| 3 — Risque | 4/4 | ✓ |
| 4 — Cohortes | 5/5 | ✓ |
| 5 — Alertes | 4/4 | ✓ |
| **Total** | **22/22** | **✓ Validé** |

---

## Conclusion

Le système a été exécuté avec succès sur un dataset de **397 884 transactions** représentant **4 338 clients** sur une période de 12 mois.

Les résultats démontrent :
- Une **architecture fonctionnelle** de bout en bout
- Des **distributions conformes** aux benchmarks sectoriels
- Une **valeur ajoutée mesurable** : 708 clients à risque identifiés parmi les clients apparemment actifs
- Des **mécanismes anti-bruit opérationnels** : pas de fausse alerte déclenchée

**Le système est prêt pour un déploiement en environnement de production.**

---

## Accès aux fichiers détaillés

Les fichiers CSV de sortie (5 tables) et la documentation technique complète sont disponibles sur demande.

**Contact :** tilkinanalytics@gmail.com

---

*Validation réalisée en janvier 2026*
