# Prise en charge des métadonnées INSPIRE par data.gouv.fr

Le présent document reprend le plan de la partie B du *Règlement (CE) n°1205/2008 du 3 décembre 2008 de la Commission portant modalités d'application de la directive 2007/2/CE du Parlement européen et du Conseil en ce qui concerne les métadonnées* ([version consolidée](https://eur-lex.europa.eu/legal-content/FR/TXT/?uri=CELEX%3A02008R1205-20081224)). Ce plan est également celui du [*Guide de saisie des éléments de métadonnées INSPIRE appliqué aux données*](https://cnig.gouv.fr/IMG/pdf/guide-de-saisie-des-elements-de-metadonnees-inspire-v2.0-1.pdf) du Conseil national de l'information géolocalisée, dans sa version 2.0 de décembre 2019, qui fait référence quant à l'interprétation des spécifications de la réglementation INSPIRE pour les administrations françaises. Pour chaque élément de métadonnées listé, il discute de l'existence dans le schéma de métadonnées de data.gouv.fr d'une catégorie permettant de représenter l'information considérée. 

Le schéma de métadonnées de data.gouv.fr est déduit du [modèle de données](https://doc.data.gouv.fr/api/reference/#/datasets/get_dataset) fourni dans la description de l'API, dans sa version du 7 juillet 2023, ainsi que des explications sur l'usage des champs présentées dans la [page de la documentation](https://doc.data.gouv.fr/moissonnage/dcat/#jeu-de-donn%C3%A9es) dédiée à la correspondance avec les métadonnées DCAT.

Quelques éléments de métadonnées ISO 19115/19139 supplémentaires sont ajoutés en fin de document. Ceux-ci ne sont pas prévus ou sont considérés comme optionnels du point de vue d'INSPIRE, mais ils sont fortement utilisés par les catalogues INSPIRE.

Légende :

| Importance | Prise en charge | Icône |
| --- | --- | --- |
| Majeur | Oui | ![](./img/checkbox-circle-fill.svg) |
| Majeur | Non | ![](./img/close-circle-fill.svg) |
| Majeur | Partielle | ![](./img/question-fill.svg) |
| Mineur | Oui | ![](./img/checkbox-line.svg) |
| Mineur | Non | ![](./img/close-circle-line.svg) |
| Mineur | Partielle | ![](./img/question-line.svg) |

## Identification des données

Un jeu de données (*dataset*) dans le contexte de data.gouv.fr est une "ressource" de [type](#type-de-la-ressource) "série de données" au sens d'INSPIRE. Les ressources (*resource*) au sens de data.gouv.fr sont à rapprocher de la notion de "[localisateur de la ressource](#localisateur-de-la-ressource)" d'INSPIRE.

### Intitulé de la ressource

*Nom caractéristique et souvent unique sous lequel la ressource est connue. Le domaine de valeur de cet élément de métadonnées est du texte libre. Cardinalité : 1.*

![](./img/checkbox-circle-fill.svg) `title` (chaîne de caractères)

### Résumé de la ressource

*Bref résumé narratif du contenu de la ressource. Le domaine de valeur de cet élément de métadonnées est du texte libre. Cardinalité : 1.*

![](./img/checkbox-circle-fill.svg) `description` (chaîne de caractères)

### Type de la ressource

*Type de ressource décrit par les métadonnées. Cardinalité : 1.*

Le registre INSPIRE met à disposition un vocabulaire ["Type de ressource"](https://inspire.ec.europa.eu/metadata-codelist/ResourceType) pour cette information.

Le type de ressource permet de distinguer :
- les séries de données (*dataset*), également appelés "jeux de données" ;
- les ensembles de séries de données (*series*), également appelés "lots" ;
- les services de données (*service*).

Les exigences d'INSPIRE en matière de métadonnées diffèrent pour les services et ensembles de séries. Les services ont des propriétés spécifiques (non considérées par le présent document), telles que le type de service de données géographiques ou les ressources couplées. Cf. *Règlement (UE) n°1089/2010 de la Commission du 23 novembre 2010 portant modalités d'application de la directive 2007/2/CE du Parlement européen et du Conseil en ce qui concerne l'interopérabilité des séries et des services de données géographiques* ([version consolidée](https://eur-lex.europa.eu/legal-content/FR/TXT/?uri=CELEX%3A02010R1089-20141231)) et *Règlement (CE) n o 976/2009 de la Commission du 19 octobre 2009 portant modalités d’application de la directive 2007/2/CE du Parlement européen et du Conseil en ce qui concerne les services en réseau* ([version consolidée](https://eur-lex.europa.eu/legal-content/FR/TXT/?uri=CELEX%3A02009R0976-20141231)).

Ces objets ont aussi des fonctions différentes. Un ensemble de séries est défini comme "une compilation de séries de données géographiques partageant la même spécification de produit". En pratique, les gestionnaires de données les utilisent pour regrouper des jeux de données formant un ensemble cohérent et pertinent pour les réutilisateurs. Un service de données est défini par la [directive INSPIRE](https://eur-lex.europa.eu/legal-content/FR/TXT/?uri=CELEX%3A02007L0002-20190626) comme "les opérations qui peuvent être exécutées à l'aide d'une application informatique sur les données géographiques contenues dans des séries de données géographiques ou sur les métadonnées qui s'y rattachent", incluant la recherche de jeux de données, la consultation des métadonnées et des données, le téléchargement des données, etc.

![](./img/close-circle-fill.svg) À l'heure actuelle, data.gouv.fr ne prend en charge que les *datasets*. Si un lot ou un service devaient faire l'objet d'une fiche de métadonnées, celle-ci serait traitée comme si elle décrivait un jeu de données.

### Localisateur de la ressource

*Le localisateur de la ressource définit le ou les liens avec la ressource et/ou le lien avec les informations supplémentaires concernant la ressource. Le domaine de valeur de cet élément de métadonnées est une chaîne de caractères couramment exprimée sous forme de localisateur de ressource uniforme (Uniform Resource Locator, URL). Cardinalité : 0..\*, obligatoire s’il existe un URL permettant d’obtenir davantage d’informations sur la ressource et/ou un accès à des services connexes.*

### Identificateur de ressource unique

*Une valeur identifiant la ressource de manière unique. Le domaine de valeur de cet élément de métadonnées est un code obligatoire sous forme de chaîne de caractères, généralement attribué par le propriétaire des données, et un espace de noms sous forme de chaîne de caractères qui identifie de manière unique le contexte du code d’identification (par exemple le propriétaire des données). Cardinalité : 1..\*.*

### Langue de la ressource

*La langue ou les langues utilisées dans le cadre de la ressource. Le domaine de valeur de cet élément de métadonnées se limite aux langues définies dans la norme ISO 639-2. Cardinalité : 0..\*, obligatoire si la ressource inclut des informations textuelles.*

### Encodage

### Encodage des caractères

### Type de représentation géographique


## Classification des données et services géographiques

### Catégorie thématique

*La catégorie thématique est un système de classification de haut niveau qui permet de regrouper et de chercher par thème les ressources de données géographiques disponibles. Cardinalité : 1..\*.*

Le registre INSPIRE met à disposition un vocabulaire ["Catégories thématiques conformément à la norme EN ISO 19115"](https://inspire.ec.europa.eu/metadata-codelist/TopicCategory) pour cette information.

Exemple d'implémentation XML ([datARA](https://catalogue.datara.gouv.fr/geonetwork/srv/api/records/6e5e2df3-8579-429f-837a-0dd9fef28a6f/formatters/xml)) :

```xml
        <gmd:topicCategory>
          <gmd:MD_TopicCategoryCode>climatologyMeteorologyAtmosphere</gmd:MD_TopicCategoryCode>
        </gmd:topicCategory>
```

data.gouv.fr ne propose pas de champ spécifique pour les catégorisations normalisées, seulement un champ de mots clés libres.

![](./img/question-line.svg) `tags` (liste de chaînes de caractères)

## Mots clés

*Si la ressource est une série de données géographiques ou un ensemble de séries de données géographiques, il convient de fournir au moins un mot clé du thésaurus multilingue de l’environnement (GEMET, General Environmental Multi-lingual Thesaurus) décrivant le thème dont relèvent les données géographiques, conformément aux définitions des annexes I, II ou III de la directive 2007/2/CE. Pour chaque mot clé, les éléments de métadonnées suivants doivent être fournis :*
- *Valeur du mot clé. La valeur du mot clé est un mot, un mot formalisé ou une expression couramment utilisés pour décrire le sujet. La catégorie thématique étant trop imprécise pour des recherches détaillées, les mots clés permettent d’affiner la recherche en texte intégral et permettent une recherche structurée par mot clé. Le domaine de valeur de cet élément de métadonnées est du texte libre.*
- *vocabulaire contrôlé d'origine. Si la valeur du mot clé provient d’un vocabulaire contrôlé (thésaurus, ontologie), par exemple GEMET, l’origine du vocabulaire contrôlé sera indiquée. Cette indication d’origine inclut au moins le titre et une date de référence (date de publication, date de dernière révision ou de création) du vocabulaire contrôlé en question.*
*Cardinalité : 1..\*.*

Le mot-clé obligatoire susmenionné correspond à ce que le guide de saisie du CNIG nomme "thème INSPIRE". Le registre INSPIRE met à disposition un vocabulaire ["Registre de thème INSPIRE"](https://inspire.ec.europa.eu/theme) pour cette information.

Le guide de saisie du CNIG identifie deux autres informations obligatoires à représenter sous forme de mots clés :
- pour un [jeu de données dit "prioritaire"](https://cnig.gouv.fr/IMG/pdf/guide-de-saisie-des-elements-de-metadonnees-inspire-v2.0-1.pdf#%5B%7B%22num%22%3A82%2C%22gen%22%3A0%7D%2C%7B%22name%22%3A%22XYZ%22%7D%2C68%2C289%2C0%5D), un mot clé qui fait référence à la réglementation européenne concernée. Le registre INSPIRE met à disposition un vocabulaire ["INSPIRE priority data set"](https://inspire.ec.europa.eu/metadata-codelist/PriorityDataset) pour cette information.
- pour un [jeu de données de couverture régionale ou nationale](https://cnig.gouv.fr/IMG/pdf/guide-de-saisie-des-elements-de-metadonnees-inspire-v2.0-1.pdf#%5B%7B%22num%22%3A85%2C%22gen%22%3A0%7D%2C%7B%22name%22%3A%22XYZ%22%7D%2C68%2C785%2C0%5D), un mot clé spécifiant la portée en question. Le registre INSPIRE met à disposition un vocabulaire ["Champ géographique"](https://inspire.ec.europa.eu/metadata-codelist/SpatialScope) pour cette information.

![](./img/question-line.svg) `tags` (liste de chaînes de caractères)

Le champ `tags` de data.gouv.fr est adapté pour les mots clés libres. Pour les autres, toutes les informations permettant de retrouver le vocabulaire dans lequel ils ont été sélectionnés sont perdues.

## Situation géographique

*Étendue de la ressource dans l’espace géographique, exprimée sous la forme d’un rectangle de délimitation. Ce rectangle de délimitation est défini par les longitudes est et ouest et les latitudes sud et nord en degrés décimaux, avec une précision d’au moins deux chiffres après la virgule. Cardinalité : 1..\*.*

### Rectangle de délimitation géographique

### Référentiel de coordonnées

#### Cas général : système de référence spatial

#### Cas particulier : système de référence par identifiant géographique


## Référence temporelle

*Cardinalité : 1..\* (au moins un des éléments ci-après doit être fourni).*

### Etendue temporelle

*L’étendue temporelle définit la période de temps couverte par le contenu de la ressource. Cette période peut être exprimée de l’une des manières suivantes :*
- *une date déterminée,*
- *un intervalle de dates exprimé par la date de début et la date de fin de l’intervalle,*
- *un mélange de dates et d’intervalles.*

![](./img/question-line.svg) `temporal_coverage / start` et `temporal_coverage / end` (date et heure)

```json
  "temporal_coverage": {
    "end": "2023-07-07T08:10:08.146Z",
    "start": "2023-07-07T08:10:08.146Z"
  }
```

L'approche de data.gouv.fr est plus restrictive que celle d'INSPIRE, qui autorise plusieurs la saisie de plusieurs intervalles et/ou dates indépendantes.

Sans que cela ne soit prévu par INSPIRE, certains catalogues dont GéoIDE permettent à leurs utilisateurs de préciser la nature de la période de référence par un commentaire textuel.

```xml
            <gmd:temporalElement>
              <gmd:EX_TemporalExtent>
                <gmd:extent>
                  <gml:TimePeriod gml:id="extent1">
                    <gml:description>période de mesure</gml:description>
                    <gml:beginPosition>2007-01-01</gml:beginPosition>
                    <gml:endPosition>2014-12-31</gml:endPosition>
                  </gml:TimePeriod>
                </gmd:extent>
              </gmd:EX_TemporalExtent>
            </gmd:temporalElement>
```

Cette métadonnée reste relativement peu utilisée aujourd'hui. D'autres moyens sont possibles pour exprimer cette information, que l'on retrouve notamment dans les libellés et descriptions des jeux de données.

### Date de publication

*Date de publication de la ressource lorsqu’elle est disponible ou date d’entrée en vigueur. Il peut y avoir plus d’une date de publication.*

![](./img/close-circle-fill.svg) `harvest / created_at`

La [documentation du moissonnage DCAT](https://doc.data.gouv.fr/moissonnage/dcat/#jeu-de-donn%C3%A9es) prévoit la retranscription de `dct:issued` - la propriété DCAT correspondant à la date de publication - dans le champ `created_at` du dictionnaire objet de la propriété `harvest` du jeu de données. D'un point de vue sémantique, ce n'est pas un choix cohérent. La conséquence pratique de l'usage de ce champ est que l'information apparaît dans l'interface utilisateur dans les "extras de moissonnage" avec pour libellé *created_at*, ce qui la rend inintelligible pour les utilisateurs.

Aucune des propriétés de date des jeux de données (`created_at`, `deleted`, `frequency_date`, `last_modified`, `last_update`) ne semble en effet correspondre à cette notion.

En pratique, cette information ne semble aujourd'hui pas récupérée du tout par les moissonnages INSPIRE.

Exemple d'une fiche de métadonnées de datARA :
- La [fiche d'origine](https://catalogue.datara.gouv.fr/geonetwork/srv/fre/catalog.search#/metadata/9136f19c-f8ab-414e-9a93-d1ee29967504) sur catalogue.datara.gouv.fr indique comme date de publication le 1er août 2017.
- Cette information est représentée ainsi dans l'exposition [XML](https://catalogue.datara.gouv.fr/geonetwork/srv/api/records/9136f19c-f8ab-414e-9a93-d1ee29967504/formatters/xml) :
    ```xml
                <gmd:date>
                  <gmd:CI_Date>
                     <gmd:date>
                        <gco:DateTime>2017-08-01T00:00:00</gco:DateTime>
                     </gmd:date>
                     <gmd:dateType>
                        <gmd:CI_DateTypeCode codeList="http://standards.iso.org/iso/19139/resources/gmxCodelists.xml#CI_DateTypeCode"
                                             codeListValue="publication"/>
                     </gmd:dateType>
                  </gmd:CI_Date>
               </gmd:date>
    ```
- Dans les propriétés du [dataset correspondant](https://www.data.gouv.fr/api/1/datasets/63d1c53284e435b2fc40440f/) de data.gouv.fr, on ne retrouve cette date nulle part. `harvest / created_at` n'existe pas.
- Dans l'[interface de data.gouv.fr](https://www.data.gouv.fr/fr/datasets/apres-mine-desordres-surfaciques-en-auvergne-rhone-alpes/#/information), elle n'apparaît sans surprise pas davantage. Le champ `created_at` des "extras du moissonnage" est présenté comme vide.

### Date de dernière révision

*Date de la dernière révision de la ressource, si la ressource a été révisée. Il ne doit pas y avoir plus d’une date de dernière révision.*

![](./img/checkbox-circle-fill.svg) `last_update` (date)

Outre `created_at`, data.gouv.fr propose deux champs pour de dates pour décrire le cycle de vie du jeu de données : `last_modified` et `last_update`. La différence entre les deux n'est pas expliquée dans les documents analysés, mais il est possible que l'un corresponde à la date de dernière mise à jour de la fiche de métadonnées lorsqu'elle est saisie directement dans data.gouv.fr. [Cet exemple](https://www.data.gouv.fr/api/1/datasets/56ba2ce488ee382c284b6d5b/), où `last_modified` est le 14 mars 2016 et `last_update` le 9 février 2016, avec le 9 février 2016 présenté [dans l'interface](https://www.data.gouv.fr/fr/datasets/contours-geographiques-des-academies/#/information) comme date de *Dernière mise à jour* (des données, semble-t-il) suggère qu'il s'agirait plutôt de `last_modified`. `last_update` correspondrait donc à la métadonnée de date de dernière révision prévue par INSPIRE.

Etrangement, la [documentation du moissonnage DCAT](https://doc.data.gouv.fr/moissonnage/dcat/#jeu-de-donn%C3%A9es) indique `dct:modified` est retranscrite dans le champ `modified_at` du dictionnaire objet de la propriété `harvest` du jeu de données, et non directement dans un des champs de date du jeu de données.

Dans le cas des moissonnages INSPIRE, il semblerait que cette information soit pour l'heure perdue. 

Exemple d'une fiche de métadonnées de datARA :
- La [fiche d'origine](https://catalogue.datara.gouv.fr/geonetwork/srv/fre/catalog.search#/metadata/9136f19c-f8ab-414e-9a93-d1ee29967504) sur catalogue.datara.gouv.fr indique comme date de révision le 23 janvier 2023.
- Cette information est représentée ainsi dans l'exposition [XML](https://catalogue.datara.gouv.fr/geonetwork/srv/api/records/9136f19c-f8ab-414e-9a93-d1ee29967504/formatters/xml) :
    ```xml
                <gmd:date>
                  <gmd:CI_Date>
                     <gmd:date>
                        <gco:DateTime>2023-01-23T08:46:21</gco:DateTime>
                     </gmd:date>
                     <gmd:dateType>
                        <gmd:CI_DateTypeCode codeList="http://standards.iso.org/iso/19139/resources/gmxCodelists.xml#CI_DateTypeCode"
                                             codeListValue="revision"/>
                     </gmd:dateType>
                  </gmd:CI_Date>
               </gmd:date>
    ```
- Dans les propriétés du [dataset correspondant](https://www.data.gouv.fr/api/1/datasets/63d1c53284e435b2fc40440f/) de data.gouv.fr, on ne retrouve cette date nulle part. `harvest / last_modified` (et non `harvest / modified_at` comme susmentionné) et `last_modified` contiennent une date qui pourrait correspondre à la [date des métadonnées](#date-des-métadonnées), si ce n'est que l'heure diffère : `2023-01-26T01:11:30.469000+00:00` dans data.gouv.fr, `2023-01-26T08:12:28` dans le XML. `harvest / last_update` et `last_update` contiennent la date du 4 mai 2023, qui n'apparaît nulle part dans la fiche de métadonnées initiale et représente probablement une information technique liée au processus de moissonnage.
- Dans l'[interface de data.gouv.fr](https://www.data.gouv.fr/fr/datasets/apres-mine-desordres-surfaciques-en-auvergne-rhone-alpes/#/information), la *Dernière mise à jour* est le 4 mai 2023.

### Date de création

*Date de création de la ressource. Il ne doit pas y avoir plus d’une date de création.*

![](./img/checkbox-circle-fill.svg) `created_at` (date)

Dans l'interface de data.gouv.fr, la valeur de ce champ apparaît dans la rubrique *Temporalité*, avec le libellé *Création*.

À noter que ce champ n'est aujourd'hui pas utilisé de cette manière dans le cas des moissonnages INSPIRE.

Exemple d'une fiche de métadonnées de la datARA :
- La [fiche d'origine](https://catalogue.datara.gouv.fr/geonetwork/srv/fre/catalog.search#/metadata/9136f19c-f8ab-414e-9a93-d1ee29967504) sur catalogue.datara.gouv.fr ne présente pas de date de création.
- Dans les propriétés du [dataset correspondant](https://www.data.gouv.fr/api/1/datasets/63d1c53284e435b2fc40440f/) de data.gouv.fr, `created_at` contient la date du 26 janvier 2023, qui - au vu de la [représentation XML](https://catalogue.datara.gouv.fr/geonetwork/srv/api/records/9136f19c-f8ab-414e-9a93-d1ee29967504/formatters/xml) - pourrait correspondre à la [date des métadonnées](#date-des-métadonnées), si ce n'est que l'heure diffère : `2023-01-26T01:11:30.469000+00:00` dans data.gouv.fr, `2023-01-26T08:12:28` dans le XML.
  ```xml
    <gmd:dateStamp>
      <gco:DateTime>2023-01-26T08:12:28</gco:DateTime>
    </gmd:dateStamp>
  ```
- Dans l'[interface de data.gouv.fr](https://www.data.gouv.fr/fr/datasets/apres-mine-desordres-surfaciques-en-auvergne-rhone-alpes/#/information), la valeur de *Création* est cette même date du 26 janvier 2023.

### Système de référence temporel


## Qualité et validité

### Généalogie

*La généalogie fait état de l’historique du traitement et/ou de la qualité générale de la série de données géographiques. Le cas échéant, elle peut inclure une information indiquant si la série de données a été validée ou soumise à un contrôle de qualité, s’il s’agit de la version officielle (dans le cas où il existe plusieurs versions) et si elle a une valeur légale. Le domaine de valeur de cet élément de métadonnées est du texte libre. Cardinalité : 1.*

![](./img/close-circle-fill.svg) data.gouv.fr ne propose aujourd'hui aucun champ qui pourrait recevoir cette information.

Exemple : fiche de métadonnées de datARA ([API](https://catalogue.datara.gouv.fr/geonetwork/srv/api/records/d06b6410-9df9-11de-ace6-0030485c9eb6/formatters/xml) / [interface](https://catalogue.datara.gouv.fr/geonetwork/srv/fre/catalog.search#/metadata/d06b6410-9df9-11de-ace6-0030485c9eb6)) contenant des informations de généalogie qui ne sont pas reprises sur data.gouv.fr ([API](https://www.data.gouv.fr/api/1/datasets/6372171e01009c6d82f64c90/) / [interface](https://www.data.gouv.fr/fr/datasets/zone-de-montagne-sur-auvergne-rhone-alpes/#/information)).

### Résolution spatiale

*La résolution spatiale se rapporte au niveau de détail de la série de données. Elle est exprimée comme un ensemble de valeurs de distance de résolution allant de zéro à plusieurs valeurs (normalement utilisé pour des données maillées et des produits dérivés d’imagerie) ou exprimée en échelles équivalentes (habituellement utilisées pour les cartes ou les produits dérivés de cartes). Une échelle équivalente est généralement exprimée sous la forme d’une valeur entière correspondant au dénominateur de l’échelle. Une distance de résolution est exprimée sous forme de valeur numérique associée à une unité de longueur. Cardinalité : 0..\*, obligatoire pour les séries de données et les ensembles de séries de données pour lesquels une échelle équivalente ou une distance de résolution peuvent être indiquées.*

### Cohérence topologique


## Conformité

*Cardinalité : 1..\*.*

### Spécification

*Indication de la référence des règles de mise en œuvre adoptées en vertu de l’article 7, paragraphe 1, de la directive 2007/2/CE ou des autres spécifications auxquelles une ressource particulière est conforme. Une ressource peut être conforme à plusieurs règles de mise en œuvre adoptées au titre de l’article 7, paragraphe 1, de la directive 2007/2/CE, ou à d’autres spécifications. Cette indication inclut au moins le titre et une date de référence (date de publication, date de dernière révision ou de création) des règles de mise en œuvre adoptées en vertu de l’article 7, paragraphe 1, de la directive 2007/2/CE ou des autres spécifications auxquelles la ressource est conforme.*

### Degré

*Degré de conformité de la ressource par rapport aux règles de mise en œuvre adoptées au titre de l’article 7, paragraphe 1, de la directive 2007/2/CE ou à d’autres spécifications.*

Le registre INSPIRE met à disposition un vocabulaire ["Niveau de conformité"](https://inspire.ec.europa.eu/metadata-codelist/DegreeOfConformity) pour cette information.

## Contraintes en matière d'accès et d'utilisation

*Une contrainte en matière d’accès et d’utilisation peut être l’un des deux éléments suivants ou les deux : un ensemble de conditions applicables à l’accès et à l’utilisation ; un ensemble de restrictions concernant l’accès public.*

### Conditions applicables à l'accès et à l'utilisation

*Cet élément de métadonnées définit les conditions applicables à l’accès et à l’utilisation des séries et des services de données géographiques, et, le cas échéant, les frais correspondants, conformément à l’article 5, paragraphe 2, point b), et à l’article 11, paragraphe 2, point f), de la directive 2007/2/CE. Le domaine de valeur de cet élément de métadonnées est du texte libre. Cet élément doit avoir des valeurs. Si aucune condition ne s’applique à l’accès à la ressource et à son utilisation, on utilisera la mention « aucune condition ne s’applique ». Si les conditions sont inconnues, on utilisera la mention « conditions inconnues ». Cet élément fournira aussi des informations sur tout frais éventuel à acquitter pour avoir accès à la ressource et l’utiliser, le cas échéant, ou fera référence à un localisateur de ressource uniforme (Uniform Resource Locator, URL) où il sera possible de trouver des informations sur les frais. Cardinalité : 1..\*.*

Le registre INSPIRE met à disposition un vocabulaire ["Conditions Applying To Access and Use"](https://inspire.ec.europa.eu/metadata-codelist/ConditionsApplyingToAccessAndUse) pour les deux seuls termes maîtrisés évoqués dans la définition : "conditions inconnues" et "aucune condition ne s'applique".

### Restrictions concernant l'accès public

*Lorsque les États membres restreignent l’accès public aux séries et aux services de données géographiques au titre de l’article 13 de la directive 2007/2/CE, cet élément de métadonnées fournit des informations sur les restrictions et les raisons de celles-ci. S’il n’y a pas de restrictions concernant l’accès public, cet élément de métadonnées l’indiquera. Le domaine de valeur de cet élément de métadonnées est du texte libre. Cardinalité : 1..\*.*

## Organisations responsables de l'établissement, de la gestion, de la maintenance et de la diffusion des séries et services de données géographiques

*Cardinalité : 1..\*. Pour chaque organisation, les deux éléments ci-après doivent être fournis.*

### Partie responsable

*Description de l’organisation responsable de l’établissement, de la gestion, de la maintenance et de la diffusion de la ressource. Cette description inclut : le nom de l’organisation sous forme de texte libre ; une adresse e-mail de contact sous la forme d’une chaîne de caractères.*

### Rôle de la partie responsable

*Fonction de l’organisation responsable.*

Le registre INSPIRE met à disposition un vocabulaire ["Rôle de la partie responsable"](https://inspire.ec.europa.eu/metadata-codelist/ResponsiblePartyRole) pour cette information.


## Métadonnées concernant les métadonnées

### Point de contact des métadonnées

*Description de l’organisation responsable de la création et de la maintenance des métadonnées. Cette description inclut : le nom de l’organisation sous forme de texte libre ; une adresse e-mail de contact sous la forme d’une chaîne de caractères. Cardinalité : 1..\*.*

### Date des métadonnées

*Date à laquelle l’enregistrement de métadonnées a été créé ou actualisé. Cette date est exprimée conformément à la norme ISO 8601. Cardinalité : 1.*

### Langue des métadonnées

*C’est la langue dans laquelle les éléments de métadonnées sont exprimés. Le domaine de valeur de cet élément de métadonnées se limite aux langues officielles communautaires représentées conformément à la norme ISO 639-2. Cardinalité : 1.*

### Identifiant de la métadonnée


## Métadonnées non requises par INSPIRE

Les métadonnées qui suivent ne sont pas requises par INSPIRE, et ne sont par conséquent pas évoquées par le guide de saisie du CNIG. Les catalogues qui les prennent en charge sont donc d'autant plus susceptibles d'avoir fait des choix d'implémentation différents.

### Fréquence d'actualisation

![](./img/question-line.svg) `frequency`. 

Le type de valeur indiqué dans la documentation de l'API de data.gouv.fr est `'unknown'`. La documentation de l'import DCAT recommande l'usage du [vocabulaire de fréquences du Dublin Core](https://www.dublincore.org/specifications/dublin-core/collection-description/frequency/) ou [celui de la Commission européenne](https://op.europa.eu/en/web/eu-vocabularies/concept-scheme/-/resource?uri=http://publications.europa.eu/resource/authority/frequency). En pratique, ce ne sont a priori pas les URI complets qui sont stockés, mais les labels anglophones ou la partie identifiante de l'URI, qui sont identiques pour les termes les plus courants ([ex 1](https://www.data.gouv.fr/api/1/datasets/5809e241c751df2646c562c5/), [ex 2](https://www.data.gouv.fr/api/1/datasets/60799532757dbdef335c00c5/)). Il arrive de trouver des termes qui n'appartiennent pas à ces vocabulaires - [par exemple](https://www.data.gouv.fr/api/1/datasets/56ba2ce488ee382c284b6d5b/) `'ponctual'`, qui est cependant reconnu et traduit par `'Ponctuelle'` [dans l'interface](https://www.data.gouv.fr/fr/datasets/contours-geographiques-des-academies/#/information).

Le registre INSPIRE met à disposition un vocabulaire ["Fréquence de maintenance"](https://inspire.ec.europa.eu/metadata-codelist/MaintenanceFrequency) pour cette information.

GéoIDE, qui est l'un des catalogues à la prendre en charge, permet de saisir non seulement une fréquence issue du vocabulaire INSPIRE susmentionné, mais aussi de l'expliciter par une note.

```xml
        <gmd:resourceMaintenance>
          <gmd:MD_MaintenanceInformation>
            <gmd:maintenanceAndUpdateFrequency>
              <gmd:MD_MaintenanceFrequencyCode codeListValue="asNeeded" codeList="http://standards.iso.org/ittf/PubliclyAvailableStandards/ISO_19139_Schemas/resources/codelist/gmxCodelists.xml#MD_MaintenanceFrequencyCode">asNeeded</gmd:MD_MaintenanceFrequencyCode>
            </gmd:maintenanceAndUpdateFrequency>
            <gmd:maintenanceNote>
              <gco:CharacterString>En particulier, mise à jour après chaque Conseil de Paris ayant donné lieu à délibération sur une ou des ZAC.</gco:CharacterString>
            </gmd:maintenanceNote>
          </gmd:MD_MaintenanceInformation>
        </gmd:resourceMaintenance>
```

ISO 19139 associe d'autres éléments que `gmd:maintenanceAndUpdateFrequency` et `gmd:maintenanceNote` aux objets `gmd:MD_MaintenanceInformation`, par exemple `gmd:dateOfNextUpdate` pour spécifier exactement la date de prochaine mise à jour, ou `userDefinedMaintenanceFrequency` pour définir la fréquence par une durée plutôt que par un terme de vocabulaire.

### Statut du jeu de données
