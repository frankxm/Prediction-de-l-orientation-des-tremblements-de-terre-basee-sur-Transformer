# Prediction de l'orientation des tremblements de terre basée sur Transformer

## Description des fichiers

### `Earthquake.py`
Ce fichier permet d'analyser et de visualiser des séries temporelles de données de contrainte. Il effectue les opérations suivantes :
- Lecture et fusion de fichiers CSV.
- Détection et correction des valeurs aberrantes.
- Lissage des données à l'aide de moyennes mobiles.
- Analyse des variations pendant les événements sismiques.
Des graphiques détaillés sont générés pour observer les tendances et anomalies dans les données de contrainte.

### `Kmeans.py`
Ce fichier analyse et visualise la répartition des zones sismiques à partir des données de latitude et longitude. Il utilise l'algorithme **KMeans** pour effectuer le clustering et évaluer différentes valeurs de `k` à l'aide des critères suivants :
- SSE (Somme des erreurs au carré)
- Silhouette score
- Indice de Davies-Bouldin

Le fichier génère des visualisations, telles que des courbes SSE, des diagrammes de clusters, et des cartes de dispersion avec les centres des clusters. De plus, il permet de vérifier les étiquettes des points spécifiques et de tracer l'enveloppe convexe des points pour délimiter les zones analysées.

### `Machine_learning.py`
Ce fichier permet de comparer un modèle d'apprentissage profond (Transformer) avec des méthodes d'apprentissage automatique. Les principales étapes incluent :
- Lecture et prétraitement des données.
- Sélection des échantillons et construction des étiquettes.
- Normalisation des données.
- Formation et évaluation du modèle.
- Vérification des performances du modèle, avec des courbes de validation et de test.

### `Earthquake_gui.py`
#### Utilisation :
1. **Étape 1** : Importez les fichiers de données de contrainte de la station, le catalogue des tremblements de terre et le fichier modèle. Si les données de contrainte sont sous format texte brut, elles sont prétraitées pour afficher des informations pertinentes telles que l'heure d'importation, le nom de la station, sa longitude, sa latitude, et le volume des données. De même, après l'importation du catalogue des tremblements de terre, les informations suivantes sont affichées : heure d'importation, zone de données, plages de longitude et de latitude, profondeur et détails du réseau sismique.
2. **Étape 2** : Une fois les trois fichiers importés, vous pouvez cliquer sur le bouton de prédiction pour prédire les tremblements de terre. Les résultats seront affichés sur une carte interactive via Amap, avec la possibilité de visualiser les résultats à votre convenance.

### `Zone_map.py`
Ce fichier utilise la bibliothèque **Folium** pour créer une carte interactive. Il applique l'algorithme **KMeans** pour effectuer une analyse de clustering sur des données géographiques, créant ainsi une carte interactive qui visualise dynamiquement les différentes zones géographiques par clusters. Cette fonctionnalité est essentielle pour l'interface graphique (GUI).

---

## Expérience du modèle Transformer

### `Dataset_process/earthdataset_process.py`
Ce fichier définit la classe `MyDataset` pour créer un ensemble de données personnalisé à l'aide de **PyTorch** pour l'entraînement et le test d'un modèle de machine learning. Il applique des techniques d'augmentation de données sur des séries temporelles.

### `Module/`
Le répertoire définit un modèle **Transformer** comprenant plusieurs composants essentiels :
- **Encoders et Decoders** : Le *Encoder* transforme une séquence d'entrée en un espace latent, et le *Decoder* génère la sortie basée sur cette représentation.
- **Mécanisme d'attention** : Le mécanisme de **Self-Attention** aide à comprendre les relations entre différentes parties d'une séquence. Il inclut aussi une attention multi-tête (*multi-head attention*).
- **Couches Feedforward** : Après l'attention, des couches de réseaux de neurones feedforward sont utilisées.
- **Encodage positionnel** : Le modèle Transformer n'ayant pas de notion de position des éléments dans une séquence, des encodages positionnels sont ajoutés pour indiquer la position des tokens.
- **Fonction de perte** : La fonction de perte est la **cross-entropy**, adaptée pour cette tâche.

### `Run_earthquake.py`
Ce fichier sert à **entraîner et valider le modèle Transformer** en réalisant plusieurs expériences. Il explore la performance du modèle en fonction de divers paramètres, tels que :
- Taux d'apprentissage
- Taille du lot
- Optimiseur
- Nombre d'époques
- Stratégie de décroissance du taux d'apprentissage
- Structure de l'ensemble de données

L'objectif est d'obtenir le modèle optimal avec les meilleures performances.

### `Run_with_saved_model.py`
Ce fichier permet d'évaluer les performances d'un modèle Transformer pré-entraîné sur un jeu de données de test. Il génère des résultats sous forme de métriques et de graphiques visuels pour analyser la performance du modèle dans une tâche de classification multi-classes.

---

## Détails supplémentaires
Si vous souhaitez en savoir plus sur les détails techniques et théoriques derrière ce projet, vous pouvez consulter l'article suivant : [Lire l'article ici](https://drive.google.com/file/d/1Ev51Qw1txSkjH7OhbzFTypYUKFZ4OkxN/view?usp=drive_link)

