We are showcasing Ocean Virtual Laboratory (**#OVL**) Visualisation tools at the 6th International Ocean Color Science (IOCS) meeting in Darmstadt.

Thanks to the co-host [EUMETSAT](https://www.linkedin.com/feed/#) and [European Space Agency - ESA](https://www.linkedin.com/feed/#) for organizing our venue, we will have demos during all lunch / coffee breaks until Wednesday afternoon.

  

Come to the colorful TV screen near the 1B pillar to know more about the https://ovl.oceandatalab.com visualisation portal and https://seascope.oceandatalab.com stand alone visualisation and analyses tool.

  

Below is a glance of beautiful meanders in Chlorophyll-a derived from **#Sentinel**-3 **#OLCI** sensor

https://odl.bzh/t3yhXIXK

# **Sujet de stage : Détection de fronts de chlorophylle et utilisation pour la validation de produits de courant océaniques**  
  
## Contexte  
Les fronts océaniques, visibles dans les observations satellitaires de chlorophylle, Temperature et Salinité, reflètent des structures dynamiques de surface telles que les zones de convergence, les fronts, les tourbillons ou les méandres de jets. Leur position et leur géométrie sont fortement influencées par la circulation de surface.  
  
Ainsi, la détection robuste de fronts sur ces traceurs peut servir d’indicateur indépendant pour valider des champs de courants issus de différentes sources (altimétrie, modèles numériques, produits multi-capteurs). La méthode a déjà été développé et testé sur des produits de température de Surface, l'objectif du stage est de l'étendre à d'autres observations comme la concentration en chlorophylle.  
  
  
## Objectifs du stage  
  
1. Développer une méthode robuste de détection de fronts dans les observations satellitaires de chlorophylle. La méthode pourra s'inspirer de l'algorithme existant pour la température   
2. Tester avec différents produits et résolution  
          
3. Quantifier la cohérence entre les fronts détectés et les courants de surface:  
    - Alignement front–courant (orientation et intensité).  
    - Comparaison avec jets et filaments simulés dans les produits de courant.    
    - Mesures de distance spatiale entre fronts et structures dynamiques.  
  
  Les développements se feront en Python  
    
## Compétences recherchées  
  
- Python  
- Traitement d’image et télédétection marine.   
- Notions de dynamique océanique.  
  
  
# **Sujet de stage : Implémentation d’un algorithme “Firework” pour la propagation des système de vague observés par satellite**  
  
    
  
## Contexte  
Plusieurs satellites permettent de mesurer les paramètres de houle (hauteur significative, période, direction) sur de vastes zones océaniques. Cependant, ces observations ponctuelles ou localisées ne permettent pas directement de reconstruire les champs de houle à l'échelle d'un bassin océanique.  
L’algorithme “firework”, utilisé en modélisation et dans plusieurs centres météo (ex. ECMWF), consiste à propager les observations de houle en suivant les lois de dispersion et de géométrie des rayons pour “éclairer” le domaine, comme un feu d’artifice qui se propage depuis des tempêtes sources.  
Les sources sont généralement détectées via la densité de rayons rétro-propagés, mais cette technique a ses limites pour les tempêtes à moins de 1000km des cotes. Ce stage vise à apporter, une information extérieure sur la position des tempetes pour reconstruire des champs de houle cohérents à partir d’observations satellite proches des cotes, et à évaluer les performances vis-à-vis de modèles de référence.  
  
## Objectifs du stage  
  
1. Analyser et comprendre le principe du firework algorithm:  
      
2. Implémenter en Python l’algorithme modifié d'identification des sources de houles.  
  
3. Tester sur differentes observations satellites  
          
4. Valider avec des observations indépendantes (in-situ, satellite) et des modèles  
  
## Compétences recherchées  
  
- Programmation Python   
- Notions de dynamique des vagues et dispersion.  
- Connaissances en océanographie physique / télédétection



# Old version

# **Sujet de stage : Détection de fronts de chlorophylle et utilisation pour la validation de produits de courant océaniques**

## Contexte
Les fronts océaniques, visibles dans les observations satellitaires de chlorophylle, Temperature et Salinité, reflètent des structures dynamiques de surface telles que les zones de convergence, les tourbillons ou les méandres de jets. Leur position et leur géométrie sont fortement influencées par la circulation de surface.

Ainsi, la détection robuste de fronts sur ces traceurs peut servir d’indicateur indépendant pour valider des champs de courants issus de différentes sources (altimétrie, modèles numériques, produits multi-capteurs). La méthode a déjà été développé et testé sur des produits de température de Surface, l'objectif du stage est de l'étendre à d'autres observations comme la chlrophylle.


## Objectifs du stage

1. Développer une méthode robuste de détection de fronts dans les observations satellitaires de chlorophylle. La méthode reposera sur l'algorithme existant pour la température 
2. Tester avec différents produits et résolution
        
3. Quantifier la cohérence entre les fronts détectés et les courants de surface:
    - Alignement front–courant (orientation et intensité).
    - Comparaison avec jets et filaments simulés dans les produits de courant.  
    - Mesures de distance spatiale entre fronts et structures dynamiques.

  Les développements se feront en Python
  
## Compétences recherchées

- Python
- Traitement d’image et télédétection marine. 
- Notions de dynamique océanique.


# **Sujet de stage : Implémentation d’un algorithme “Firework” pour la propagation des système de vague observés par satellite**

  

## Contexte
Plusieurs satellites permettent de mesurer les paramètres de houle (hauteur significative, période, direction) sur de vastes zones océaniques. Cependant, ces observations ponctuelles ou localisées ne permettent pas directement de reconstruire les champs de houle à grande échelle.
L’algorithme “firework”, utilisé en modélisation et dans plusieurs centres météo (ex. ECMWF), consiste à propager les observations de houle en suivant les lois de dispersion et de géométrie des rayons pour “éclairer” le domaine, comme un feu d’artifice qui se propage depuis des sources ponctuelles.
Ce stage vise à implémenter un tel algorithme pour reconstruire des champs de houle cohérents à partir d’observations sporadiques, et à évaluer les performances vis-à-vis de modèles de référence.

## Objectifs du stage

1. Analyser et comprendre le principe du firework algorithm:
    
2. Implémenter en Python l’algorithme

3. Tester sur differentes observations satellites
        
4. Valider avec des observations indépendantes (in-situ, satellite) et des modèles

## Compétences recherchées

- Programmation Python 
- Notions de dynamique des vagues et dispersion.
- Connaissances en océanographie physique / télédétection
  