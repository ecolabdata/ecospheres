# Ecosphères

Ecosphères est le portail des données de la transition écologique et de la cohésion des territoires.

Ce dépôt sert de guichet technique à la plateforme Ecosphères.

## Dépôts de code

### [ecolabdata/ckanext-dsfr](https://github.com/ecolabdata/ckanext-dsfr)
*Extension de CKAN.*

Thème graphique pour CKAN mettant en oeuvre le [système de design de l'Etat](https://www.systeme-de-design.gouv.fr/).

Le thème implémente également des fonctionnalités de découverte des données (filtres par thématique, territoire ou organisation sur la page d'accueil...) et une organisation visuelle de l'interface conçus dans le cadre d'ateliers de design utilisateur.

### [ecolabdata/ckanext-ecospheres](https://github.com/ecolabdata/ckanext-ecospheres)

*Extension de CKAN.*

Personnalisation des extensions standard pour permettre le moissonnage de métadonnées structurées selon différents formats - à date INSPIRE-ISO 19115/19139 et DCAT - en minimisant les pertes d'information :

- [ckanext-scheming](https://github.com/ckan/ckanext-scheming) pour la définition d'un schéma unique de fiche de métadonnées (*dataset*), capable d'assimiler les informations fournies par les différentes sources.
- [ckanext-spatial](https://github.com/ckan/ckanext-spatial) pour transformer les fiches de métadonnées issues des moissonnages de catalogues de données géographiques (INSPIRE-ISO 19115/19139) selon le schéma unique.
- [ckanext-dcat](https://github.com/ckan/ckanext-dcat) pour transformer les fiches de métadonnées issues des moissonnages de catalogues DCAT selon le schéma unique, et exposer en DCAT les fiches structurées selon le schéma unique.

Système de gestion de vocabulaires contrôlés, avec :

- L'import depuis des sources diverses.
- La normalisation et mise en base des vocabulaires.
- La mise à disposition d'utilitaires pour les exploiter lors des moissonnages (reconnaissance des termes de vocabulaire) et pour l'affichage.

### [ecolabdata/ckanext-spatial](https://github.com/ecolabdata/ckanext-spatial)

*Fourche de l'extension [ckanext-spatial](https://github.com/ckan/ckanext-spatial).*
 
Possibilité de relancer un moissonnage lorsqu'il échoue en raison d'une erreur côté serveur.

Prise en charge des filtres OGC dans la configuration des moissonnages.

### [ecolabdata/guichetdonnees-public](https://github.com/ecolabdata/guichetdonnees-public)

*Outillage d'administration.*

Maintenance d'un annuaire des organisations et moissonnages associés, incluant les filtres permettant de moissonner spécifiquement les données d'une organisation sur un catalogue commun à plusieurs organisations.

Utilitaires pour faciliter la création et la gestion via l'API d'Ecosphères des objets *organization* et *harvest* représentant les organisations et configurations de moissonnages sur la plateforme. 