# Partir un jour - Write-up

Nous analysons une photographie montrant un avion en phase d'atterrissage.

1. **Analyse de la photo et des métadonnées** :
   - Nous identifions la compagnie aérienne comme étant *Aer Lingus*.
   - L'examen des métadonnées géographiques et temporelles nous indique que la photo a été prise en Irlande à une date précise.
   - La position des volets de l'avion suggère que ce dernier est en phase finale d'atterrissage.
2. **Recherche du vol** :
   - Nous utilisons la base de données historique d'un service de suivi de vols (comme *ADSB-Exchange*) en filtrant par la date et l'heure estimées de la prise de vue.
   - Nous isolons le vol correspondant aux critères d'atterrissage : `EIN605P` (provenance Amsterdam, destination Dublin).
3. **Géolocalisation au sol** :
   - Sur Google Maps, nous recherchons la zone d'approche de l'aéroport pour repérer le bâtiment rouge visible sur l'image et identifions la route `R108`.

**FLAG** : `HTS{amsterdam:dublin:EIN605P:R108}`
