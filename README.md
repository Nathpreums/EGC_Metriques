# Évaluation des classements en uplift multi-traitement

Ce dépôt contient le code des expériences sur données synthétiques présentées dans l'article *« Au-delà du premier choix : évaluation des classements en uplift multi-traitement »* (EGC 2027).

L'objectif est d'étudier une métrique qui prend en compte l'ensemble du classement des traitements, et pas seulement la première recommandation. Le notebook permet notamment de comparer cette métrique, notée **R**, à la réponse espérée du premier choix (**V1**).

## Contenu

Le fichier `NOTEBOOK_METRIQUES_EGC.ipynb` rassemble les expériences :

- **Profils par rang** : comparaison de quatre classements qui ont le même premier choix, mais des ordres différents pour les traitements suivants (figure 1 de l'article).
- **Différences entre les rangs** : visualisation des écarts de réponse espérée entre les positions du classement.
- **Variance et sélection de modèles** : comparaison des variances des estimateurs IPW de V1 et de R, puis sélection parmi dix modèles candidats selon le nombre de traitements et la taille de l'échantillon de validation (figure 2 de l'article).

Toutes les données sont générées par le code. Aucun jeu de données externe n'est nécessaire.

## Exécution

Le code utilise Python et les bibliothèques suivantes : `numpy`, `pandas`, `matplotlib`, `scipy` et `scikit-learn`.

Pour les installer avec Jupyter :

```bash
pip install numpy pandas matplotlib scipy scikit-learn notebook
```

Ouvrir ensuite le notebook et exécuter les cellules dans l'ordre :

```bash
jupyter notebook NOTEBOOK_METRIQUES_EGC.ipynb
```

Le paramètre `MODE = 'quick'` permet de lancer les expériences avec moins de répétitions. Pour utiliser le réglage plus complet, remplacer `quick` par `full`. La dernière expérience peut prendre du temps, surtout avec un grand nombre de traitements.

Les figures sont enregistrées au format PDF et les tableaux de résultats au format CSV. Les premiers graphiques sont créés à côté du notebook ; les résultats de l'expérience sur la variance et la sélection sont placés dans `Chapitres/metriques/`.

Une graine aléatoire est fixée pour rendre les résultats reproductibles.
