# Dashboard Nomadia - Guide d'Utilisation

## Table des Matières
1. [Vue d'ensemble](#vue-densemble)
2. [Démarrage](#démarrage)
3. [Interface Principale](#interface-principale)
4. [Filtres et Navigation](#filtres-et-navigation)
5. [Sections du Dashboard](#sections-du-dashboard)
6. [Export de Données](#export-de-données)
7. [Résolution des Problèmes](#résolution-des-problèmes)

---

## Vue d'ensemble

Le **Dashboard Nomadia** est une application web interactive conçue pour la gestion et le suivi des situations de stationnement des voyageurs. Il offre une vision complète et en temps réel des signalements à travers des indicateurs de performance, des analyses territoriales et des outils de suivi opérationnels.

### Fonctionnalités Principales
- Suivi en temps réel des signalements actifs
- Analyses statistiques et indicateurs de performance (KPIs)
- Visualisations interactives (graphiques, cartes de chaleur)
- Filtres avancés par territoire, statut et période
- Export de données au format CSV
- Synchronisation automatique avec Airtable

---

## Démarrage

### Prérequis
- Python 3.8 ou supérieur
- Token API Airtable valide
- Connexion internet

### Installation

1. **Installer les dépendances**
```bash
pip install -r requirements.txt
```

2. **Configuration de l'API Airtable**

   Créez un fichier `.env` à la racine du projet :
   ```env
   AIRTABLE_TOKEN=votre_token_airtable_ici
   ```

3. **Lancer le dashboard**
```bash
streamlit run app.py
```

4. **Accéder au dashboard**

   Ouvrez votre navigateur à l'adresse : `http://localhost:8501`

---

## Interface Principale

### En-tête
- **Titre** : "Dashboard Nomadia - Gestion des Signalements"
- **Logo** : Affiché dans la barre latérale
- **Bouton d'actualisation** : Recharge les données depuis Airtable

### Barre Latérale (Sidebar)

La barre latérale contient tous les contrôles de filtrage :

#### 1. Bouton d'Actualisation
- Cliquez sur "🔄 Actualiser les données" pour recharger les données depuis Airtable
- Les données sont mises en cache pendant 5 minutes pour optimiser les performances

#### 2. Filtres Disponibles
- **Intercommunalité** : Filtrez par zone intercommunale
- **État de gestion** : Filtrez par statut du dossier (en cours, terminé, etc.)
- **Arrondissement** : Filtrez par zone géographique
- **Période** : Sélectionnez une plage de dates pour l'analyse

---

## Filtres et Navigation

### Comment Utiliser les Filtres

1. **Filtre par Intercommunalité**
   - Sélectionnez "Toutes" pour voir l'ensemble des données
   - Choisissez une intercommunalité spécifique pour une vue ciblée

2. **Filtre par État de Gestion**
   - Options : Diagnostic en cours, A traiter, Fin du stationnement, etc.
   - Permet d'identifier rapidement les dossiers nécessitant une action

3. **Filtre par Arrondissement**
   - Affine l'analyse par zone administrative

4. **Filtre par Période**
   - Utilisez le sélecteur de dates pour analyser une période spécifique
   - Par défaut, affiche toutes les données disponibles

### Combinaison de Filtres
Les filtres peuvent être combinés pour des analyses très précises. Par exemple :
- Intercommunalité X + État "A traiter" + Dernier trimestre
- Arrondissement Y + Période spécifique

---

## Sections du Dashboard

### 1. Activité Globale & Évolution

**Signalements Totaux**
- Grande carte affichant le nombre total de signalements
- Mise à jour selon les filtres appliqués

**Évolution Mensuelle**
- Graphique en courbe montrant la tendance des signalements
- Permet d'identifier les périodes de forte activité

### 2. Vue d'Ensemble - KPIs Principaux

#### État Actuel du Territoire
- **Signalements actifs** : Nombre de situations en cours
- **Ménages présents** : Total des ménages actuellement sur le territoire
- **Caravanes présentes** : Total des caravanes en stationnement
- **Ratio Caravanes/Ménage** : Moyenne de caravanes par ménage

#### Performance de Gestion
- **Délai moyen 1ère intervention** : Temps de réaction moyen
  - ✅ Objectif : < 7 jours
  - ⚠️ Alerte si > 7 jours
- **Durée moyenne de stationnement** : Temps moyen de présence
- **Dossiers urgents** : Signalements nécessitant une attention immédiate
  - Critères : >30 jours sans intervention OU aucune intervention

### 3. Performance Opérationnelle

**Indicateurs**
- **Taux de réactivité** : Pourcentage de dossiers traités en moins de 7 jours
- **Interventions moyennes/dossier** : Nombre moyen d'actions par signalement
- **Durée moyenne de présence** : Statistique globale

**Graphiques**
- **Distribution des délais** : Histogramme montrant la répartition des délais d'intervention
  - Ligne verte : Objectif 7 jours
  - Ligne orange : Seuil critique 20 jours
- **Corrélation interventions/durée** : Scatter plot montrant la relation entre nombre d'interventions et durée de présence

### 4. Analyse Territoriale

**Top 5 Communes (Hot Spots)**
- Identification des zones avec le plus de signalements
- Graphique en barres horizontales

**Activité par Intercommunalité**
- Vue d'ensemble de la répartition géographique
- Carte de chaleur colorée par intensité

**Taille Moyenne des Groupes**
- Comparaison ménages vs caravanes par territoire
- Graphique en barres groupées

### 5. Analyse Juridique

**Répartition par Statut Juridique**
- Camembert montrant les différents types de situations
- Exemples : Stationnement régulier, irrégulier, procédure en cours

**Durée Moyenne par Type de Procédure**
- Analyse de l'efficacité des différentes procédures
- Aide à identifier les processus les plus longs

**Situation : Subie vs Choisie**
- Compréhension du contexte social
- Indicateur clé pour l'accompagnement

### 6. Services & Conditions de Vie

**Index de Précarité**
- Nombre de situations sans aucun service (eau, électricité, assainissement)
- Indicateur d'urgence sociale

**Taux d'Équipement**
- Graphique en barres empilées montrant l'accès aux services
  - Eau
  - Électricité
  - Assainissement

**Impact des Services**
- Corrélation entre nombre de services disponibles et durée de présence
- Aide à comprendre les facteurs d'installation durable

### 7. Mobilisation des Acteurs

**Acteurs les Plus Mobilisés**
- Top 10 des partenaires impliqués dans la gestion
- Graphique horizontal

**Performance par Gestionnaire**
- Tableau détaillé avec :
  - Nombre de dossiers gérés
  - Délai moyen d'intervention
  - Nombre de dossiers terminés
  - Taux de résolution (%)

### 8. Analyse du Journal des Interventions

**KPIs Interventions**
- Total d'interventions
- Dossiers avec interventions
- Moyenne par dossier
- Dossiers actifs

**Types d'Interventions**
- Top 10 des interventions les plus fréquentes
- Catégorisation :
  - 📞 Contact & Communication
  - 🤝 Rencontre & Médiation
  - ⚖️ Juridique & Administratif
  - 🚔 Forces de l'Ordre
  - 📋 Autre

**Performance des Gestionnaires**
- Nombre d'interventions par gestionnaire
- Moyenne interventions/dossier

**Analyse Territoriale**
- Communes nécessitant le plus d'interventions
- Intensité des interventions (ratio interventions/dossiers)

**Détail des Interventions**
- Tableau complet avec filtres
- Possibilité d'export CSV

**Efficacité des Types d'Interventions**
- Taux de résolution par type d'intervention
- Aide à identifier les actions les plus efficaces

### 9. Évolution de la Présence des Voyageurs

**KPIs de Flux**
- Nouvelles arrivées (ménages)
- Départs (ménages)
- Ménages actuellement présents
- Taux de rotation

**Graphiques d'Évolution**
- **Ménages** : Courbe de présence + barres d'arrivées/départs
- **Caravanes** : Même visualisation pour les caravanes
- Vue hebdomadaire des flux

**Tableau Détaillé**
- Export CSV disponible
- Détail semaine par semaine

### 10. Analyse de Saisonnalité

**Évolution Mensuelle**
- Graphique combiné : barres (signalements) + courbe (ménages)
- Identification des pics saisonniers

**Activité par Trimestre**
- Vue agrégée pour tendances à long terme
- Graphique en barres colorées

### 11. Liste Détaillée des Signalements

**Fonctionnalités**
- **Recherche** : Champ de recherche libre (commune, adresse, gestionnaire, etc.)
- **Tri** : Plusieurs options
  - Score de priorité (décroissant)
  - ID
  - Date de début
  - Délai d'intervention
  - Nombre de ménages

**Tableau avec Coloration Conditionnelle**
- **Délai d'intervention** :
  - Vert : ≤ 7 jours (objectif atteint)
  - Jaune : 8-20 jours (attention)
  - Rouge : > 20 jours (critique)
- **Score de priorité** :
  - Rouge foncé : > 100 (urgence élevée)
  - Jaune : 50-100 (attention)
  - Vert : < 50 (normal)

**Colonnes Affichées**
- ID
- Commune
- Intercommunalité
- Date de début
- Ménages
- Caravanes
- État de gestion
- Délai 1ère intervention
- Terrain
- Score de priorité

---

## Export de Données

### Export Principal (Liste Détaillée)
1. Appliquez vos filtres
2. Utilisez la barre de recherche si nécessaire
3. Cliquez sur "📥 Télécharger les données (CSV)"
4. Le fichier est nommé automatiquement : `nomadia_export_YYYYMMDD_HHMMSS.csv`

### Export des Interventions
1. Accédez à la section "Analyse du Journal des Interventions"
2. Développez "📋 Voir le détail de toutes les interventions"
3. Appliquez les filtres (gestionnaire, catégorie)
4. Cliquez sur "📥 Télécharger les interventions (CSV)"

### Export de l'Analyse de Présence
1. Accédez à la section "Évolution de la Présence des Voyageurs"
2. Développez "📋 Voir le détail hebdomadaire"
3. Cliquez sur "📥 Télécharger l'analyse de présence (CSV)"

---

## Résolution des Problèmes

### Problème : "Aucune donnée disponible"

**Causes possibles :**
1. Token Airtable invalide ou expiré
2. Problème de connexion internet
3. Base Airtable inaccessible

**Solutions :**
1. Vérifiez votre fichier `.env` et assurez-vous que le token est correct
2. Testez votre connexion internet
3. Vérifiez que vous avez accès à la base Airtable
4. Consultez les logs Streamlit pour plus de détails

### Problème : Données non actualisées

**Solution :**
1. Cliquez sur le bouton "🔄 Actualiser les données" dans la barre latérale
2. Les données sont mises en cache pendant 5 minutes
3. Un rafraîchissement manuel efface le cache et recharge depuis Airtable

### Problème : Graphiques vides

**Causes possibles :**
1. Filtres trop restrictifs
2. Données manquantes dans Airtable
3. Champs de date non remplis

**Solutions :**
1. Réinitialisez les filtres (sélectionnez "Toutes" / "Tous")
2. Vérifiez que les données existent dans Airtable
3. Assurez-vous que les champs obligatoires sont remplis

### Problème : Export CSV ne fonctionne pas

**Solution :**
1. Vérifiez que vous avez au moins un enregistrement dans la vue filtrée
2. Essayez un autre navigateur
3. Videz le cache de votre navigateur

### Problème : Le dashboard est lent

**Causes possibles :**
1. Volume important de données
2. Cache désactivé
3. Trop de filtres simultanés

**Solutions :**
1. Utilisez les filtres pour réduire le volume de données affichées
2. Le cache est automatique (TTL 5 minutes)
3. Rafraîchissez la page si nécessaire

---

## Comprendre les Indicateurs Clés

### Score de Priorité

**Formule :**
```
Score = (Ménages × Délai 1ère intervention) / Nb interventions

Bonus si statut = "Diagnostic en cours" | "A traiter" | "Interlocuteur consulté"
→ Score × 1.5
```

**Interprétation :**
- **Score > 100** : Priorité très élevée
  - Situation nécessitant une intervention urgente
  - Exemple : Nombreux ménages, délai long, peu d'interventions
- **Score 50-100** : Priorité moyenne
  - Surveillance nécessaire
- **Score < 50** : Priorité normale
  - Situation en cours de gestion normale
- **Score = 999** : Aucune intervention effectuée
  - Dossier non traité (priorité maximale absolue)

### Dossiers Urgents

**Critères d'urgence :**
- Délai de 1ère intervention > 30 jours **OU**
- Aucune intervention ET statut ≠ "Fin du stationnement"

### Taux de Rotation

**Formule :**
```
Taux de rotation = (Nombre de départs / Nombre d'arrivées) × 100
```

**Interprétation :**
- **100%** : Équilibre parfait (autant d'arrivées que de départs)
- **< 100%** : Augmentation de la présence
- **> 100%** : Diminution de la présence

---

## Conseils d'Utilisation

### Pour un Suivi Quotidien
1. Consultez la section "Dossiers urgents"
2. Vérifiez le "Délai moyen 1ère intervention"
3. Regardez les "Signalements actifs"

### Pour une Analyse Mensuelle
1. Utilisez le filtre de période (dernier mois)
2. Consultez "Évolution Mensuelle"
3. Analysez la "Performance par Gestionnaire"
4. Exportez les données pour archivage

### Pour un Rapport Trimestriel
1. Activez le filtre de période (trimestre)
2. Consultez toutes les sections d'analyse
3. Exportez les visualisations (screenshot)
4. Téléchargez les CSV pour annexes

### Pour une Intervention d'Urgence
1. Triez par "Score de priorité (décroissant)"
2. Filtrez par "Dossiers urgents"
3. Identifiez les situations critiques (rouge)
4. Vérifiez le journal des interventions

---

## Foire aux Questions (FAQ)

### Q1 : À quelle fréquence les données sont-elles actualisées ?
**R :** Les données sont mises en cache pendant 5 minutes. Pour une actualisation immédiate, utilisez le bouton "🔄 Actualiser les données".

### Q2 : Puis-je modifier les données depuis le dashboard ?
**R :** Non, le dashboard est en lecture seule. Toutes les modifications doivent être effectuées directement dans Airtable.

### Q3 : Les exports CSV contiennent-ils toutes les colonnes ?
**R :** Oui, l'export principal contient toutes les colonnes de la base de données, même celles non affichées dans le tableau.

### Q4 : Comment interpréter un score de priorité de 999 ?
**R :** Un score de 999 indique qu'aucune intervention n'a été effectuée. C'est le niveau de priorité le plus élevé.

### Q5 : Que signifie "Situation : Subie vs Choisie" ?
**R :** Cet indicateur différencie si le stationnement est :
- **Subi** : Contrainte économique ou sociale
- **Choisi** : Mode de vie volontaire

### Q6 : Comment sont catégorisées les interventions ?
**R :**
- **Contact & Communication** : Appels, contacts communes
- **Rencontre & Médiation** : Visites, rencontres, médiation
- **Juridique & Administratif** : PV, courriers, demandes d'évacuation
- **Forces de l'Ordre** : Interventions police
- **Autre** : Autres types d'actions

### Q7 : Quelle est la différence entre "Signalements actifs" et "Signalements totaux" ?
**R :**
- **Signalements actifs** : Stationnements en cours (pas de date de fin OU date de fin future)
- **Signalements totaux** : Tous les signalements selon les filtres appliqués

---

## Support et Contact

### Problèmes Techniques
- Vérifiez d'abord la section "Résolution des Problèmes"
- Consultez les logs Streamlit dans le terminal
- Contactez l'administrateur système

### Modifications de Fonctionnalités
Pour toute demande d'évolution ou nouvelle fonctionnalité, contactez l'équipe de développement.

### Données et Configuration Airtable
Pour les questions liées aux données, la structure des tables ou les permissions Airtable, contactez l'administrateur Airtable.

---

## Informations Légales

**Dashboard Nomadia** - Gestion et suivi des situations de stationnement

Données synchronisées avec Airtable via API

Ce dashboard est la propriété de la société immatriculée au SIRET : 99158319600019

---

**Version du guide** : 1.0
**Dernière mise à jour** : 2025-10-22
