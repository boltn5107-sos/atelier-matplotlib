# atelier-matplotlib

Atelier d'analyse graphique avec **Matplotlib** et **Pandas** de données de capteurs IoT
installés dans plusieurs bâtiments d'une entreprise. Le dataset contient des mesures de
température, d'humidité, de pression et de consommation énergétique.

## Structure du projet

```
atelier_matplotlib_iot/
│
├── data/
│   └── mesures_capteurs.csv      # Données brutes des capteurs (605 mesures)
│
├── notebooks/
│   └── atelier_matplotlib_iot.ipynb  # Notebook complet (Parties 1 à 9)
│
└── exports/
    ├── temperature.png           # Graphique évolution de la température (Partie 8)
    └── temperature.pdf           # Version PDF du même graphique
```

## Données

Le fichier `mesures_capteurs.csv` contient 9 colonnes :

| Colonne | Description |
|---|---|
| `id_mesure` | Identifiant unique de la mesure |
| `date_heure` | Date et heure de la mesure (2026-01-05 → 2026-01-29) |
| `id_capteur` | Identifiant du capteur |
| `batiment` | Bâtiment concerné (B001, B002, B003, B004) |
| `temperature` | Température en °C |
| `humidite` | Humidité en % |
| `pression` | Pression en hPa |
| `consommation` | Consommation énergétique en kWh |
| `etat` | État du capteur (OK, ALERTE, ERREUR) |

## Installation

```bash
pip install pandas matplotlib jupyter
```

## Exécution

```bash
jupyter notebook notebooks/atelier_matplotlib_iot.ipynb
```

## Contenu du notebook

| Partie | Sujet | Type de graphique |
|---|---|---|
| 1 | Évolution de la température dans le temps | Line plot |
| 2 | Consommation moyenne par bâtiment | Bar chart (vertical + horizontal) |
| 3 | Distribution de la température et de la consommation | Histogramme (10 / 20 / 30 classes) |
| 4 | Relation température ↔ consommation | Scatter plot |
| 5 | Distribution et dispersion | Box plots |
| 6 | Répartition des états (OK, ALERTE, ERREUR) | Pie chart |
| 7 | Évolution de la température par bâtiment | Multi-courbes |
| 8 | Sauvegarde des graphiques | Exports PNG et PDF |
| 9 | Bonus | Détection IQR, heatmap, sous-graphiques, profils horaires, corrélation |

## Résultats clés

- **Anomalies de température** : -18,5 °C et 58,7 °C (capteur défaillant, bâtiment B004),
  confirmées par la détection automatique par IQR.
- **Consommation** : B004 est le bâtiment le plus consommateur (≈ 283 kWh en moyenne), B003 le
  moins (≈ 153 kWh). Un pic isolé à 875 kWh constitue une anomalie.
- **Corrélation** : humidité fortement liée à la température (**-0,92**) ; la consommation
  dépend peu de la température (**+0,32**).
- **États des capteurs** : 94,3 % OK, 4,8 % ALERTE, 0,8 % ERREUR.
