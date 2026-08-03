

450 Heures Confirmed IT à 83,82€ pour 37 719,00€

930 Heures IT Technician à 36,72€ pour 34 149,60€

et 40 heures Project management à 91,95€ pour 3678,00€

soit un total de 1420 heures pour 75 546,60€

soit un total de 1420 heures pour 75 546,60€


Hi Craig,

I'm really sorry if I did some damage with my email ... this was not the intention off course, but internally at ODL the relation with the Lehmkuhl was really painfull, they never saw that before ... and they don't want to deal with them anymore... probably a cultural difference where saying means nothing ... everything needs to be written with the Norwegians !

But thanks for calling and expressing your tought ...

as for OVL science activities :

what we would like to be covered

**Core Objective** : Evolve, maintain, and operate the _Ocean Virtual Laboratory_ platform over a 36-month period, ensuring continuous alignment with the needs of the scientific user community. 

**Real-Time (NRT) Portal Operations**: Ensure automated, continuous updates for data visualization portal. This covers the processing all OVL datasets except Sentinel 1/2/3 (the hudge datasets) meaning all other ESA missions like explorers, non ESA missions, model and in-situ.

**OVL portal new developments** : Improve the OVL portal capabilities to respond to user needs. This includes easy access to download list on CDSE or other ESA data portals, rather than individual download links, intractive plotting beyond the 2D map dimentions (along vertical and temportal dimentions). 

**SEAScope Integration & Evolution**: Improve the standalone SEAScope application—which visualizes actual geophysical measurements on a 3D sphere rather than pre-rendered images—and progressively implement remote data access via cloud streaming from the new Zarr based infrastructure.

**Better integrate OVL tools in existing ESA infrastructure :** Implement gateways and direct download links to official platforms like the CDSE and two way interaction with ESA toolboxes such as CCI or SNAP, for SNAP users to search for usefull datasets to be analised with SNAP and in turn combine SNAP outputs to exploit the synergy amongst various datasets.

**User Consultation Meetings**: Organize yearly consultation meetings with scientific users to gather feedback from the scientific community and dynamically refine the software development roadmap based on their priorities. I remind you the link on Testimonials 

**Educational Tools, Tutorials and Trainings**: Produce interactive tutorials combining OVL portal, SEAScope and Jupyter/iPython notebooks to serve as training material for the ESA Ocean Training Course. Prepare and help to install the tools during trainings and run the interactive lectures.

**Communication, Community Outreach & Support**: Promote tool adoption through active social media communication, SEAShot sharing plateform support and evolution, together with dedicated support sections on the OVL forum to streamline user assistance. Support to ESA projects benefiting from OVL type portals (ingestion of specific datasets is covered separately by the projects themselves)

what is covered with Betlem

Infrastructure for Sentinel 1/2/3 processing and related setup/operation/monotoring/backup...


Hello,  
  
entre deux voyages je transmets la liste des nouvelles features que j'avais commencé.  
Ce sont les features qui ne sont pas dans la dernière version interne de seascope que j'ai partagé mais qui existent dans seascope_next.  
Les tuiles vectorielles seront retirées de la release pour être intégrées dans la prochaine (c'était pas demandé et ça demande un coup de polish).  
  
Déjà fait / bien avancé :  
- GoTo animé : Animation du globe depuis la caméra courante vers les coordonnées données au GoTo.  
- Nouvelle lib netcdf maison plus légère et plus rapide que la lib officielle.  
- Lecture de netcdf en parallèle soit via processus avec la lib netcdf officielle (beurk), soit via threads via la lib netcdf maison (nice :) )  
- Optimisation de la phase d'indexation (temps d'indexation divisé par 3 ou 4 en fonction du PC).  
- Affichage des tuiles de données OVL dans SEAScope.  
- Lecture des valeurs des données OVL (PNG en palette indexée)  
- Changement des palettes des données OVL (PNG en palette indexée)  
- Création d'une lib d'interface graphique moderne  
- Remplacement de la lib Nanogui par la nouvelle lib d'UI maison  
- Ecriture de renderers OpenGL 4.6 et Vulkan permettant l'utilisation de compute shaders permettant d'intégrer certains calculs sur la donnée directement dans SEAScope. (refactoring complet du code de rendu).  
- Affichage de tuiles vectorielles permettant un rendu optimal du texte et du trait de côte.  
- Intégration d'un crash reporter.  
- Affichage de la boite englobante d'un granule.  
- Découpage spatial du globe permettant le chargement et l'affichage des données visibles. Actuellement tous les granules sont chargés et cela peut mener à un crash.  
- Gestion de la mémoire permettant le déchargement des données non utilisées. Actuellement on charge jusqu'au crash.  
- SEAScope en version windows ARM64 ?  
  
A faire:  
- Chargement des netcdf en parallèle, gros gain potentiel sur les drifters par exemple.  
- Affichage de données distantes autres que les pyramides de tuiles PNG (zarr ?)  
- Amélioration de l'animation temporelle.  
- Animation de streamlines pendant une animation temporelle.  
- Optimisation des flèches / barbs, utilisation du découpage spatial pour les rendre beaucoup plus légères en ressources.  
- Amélioration du rendu des flèches / barbs, passage d'une icone raster qui bave à un rendu de glyph avec antialiasing.  
- Suppression de la sortie console pour un affichage 100% dans l'interface graphique de SEAScope (indexation surtout).  
- Ajout de données sans avoir besoin de redémarrer seascope.  
- Changement de tous les paramètres sans avoir besoin de fermer et réouvrir seascope. Dans le "pire cas" seascope se relance tout seul.  
- ... tellement de choses possibles.  
  
J'ai pas la roadmap sous les yeux mais vous pouvez vous lâcher sur les grosses features demandées depuis longtemps.  
Le socle de seascope 2 est en place et permet plus de choses.  
  
Guillaume


  
  
  
-------- Message transféré --------

|   |   |
|---|---|
|Sujet :|OVL-bridging Contract|
|Date :|Mon, 15 Jun 2026 17:11:55 +0000|
|De :|Craig James Donlon [<Craig.Donlon@esa.int>](mailto:Craig.Donlon@esa.int)|
|Pour :|[dr.fab@odl.bzh](mailto:dr.fab@odl.bzh) [<dr.fab@odl.bzh>](mailto:dr.fab@odl.bzh)|
|Copie à :|Diego Fernandez Prieto [<Diego.Fernandez@esa.int>](mailto:Diego.Fernandez@esa.int), Marie-Helene Rio [<Marie-Helene.RIO@esa.int>](mailto:Marie-Helene.RIO@esa.int)|

  
  

Dear Fabrice:

  

I hope all is well. Based on our discussions today, please can you send a proposal for Bridging the OVL for the next 2 years.

  

I discussed this with Diego a few weeks back and he considers  2 years at ~200K.  This should cover the time to mature the initial transfer activities with Betlem (as agreed 2 weeks ago via CapGemini) and allow time for you to make a proposal to the new EOF Ground Segment call in 2027/28 all being well.

  

This shall include:

**Core Objective** : Evolve, maintain, and operate the _Ocean Virtual Laboratory_ platform over a 24-month period, ensuring continuous alignment with the needs of the scientific user community. 

**Real-Time (NRT) Portal Operations**: Ensure automated, continuous updates for data visualization portal. This covers the processing all OVL datasets except Sentinel 1/2/3 (the huge datasets) meaning all other ESA missions like explorers, non ESA missions, model and in-situ.

**OVL portal new developments** : Improve the OVL portal capabilities to respond to user needs. This includes easy access to download list on CDSE or other ESA data portals, rather than individual download links, interactive plotting beyond the 2D map dimensions (along vertical andtemporal dimensions). 

**SEAScope Integration & Evolution**: Improve the standalone SEAScope application—which visualizes actual geophysical measurements on a 3D sphere rather than pre-rendered images—and progressively implement remote data access via cloud streaming.

**Support to other ESA projects (e.g. SARwave,** **Meddicane project, Oceanhealth, Sentinel-1 MPC, UpperDyn, PiMEP and others)** **:** Implement a dedicated branded OVL interface to support new ESA projects as required (10% of Contract value).

**User Consultation Meetings**: Organize yearly consultation meetings with scientific users to gather feedback from the scientific community and dynamically refine the software development roadmap based on their priorities. I remind you the link on Testimonials 

**Educational Tools, Tutorials and Trainings**: Produce interactive tutorials combining OVL portal, SEAScope and Jupyter/iPython notebooks to serve as training material for the ESA Ocean Training Course. Prepare and help to install the tools during trainings and run the interactive lectures.

**Communication, Community Outreach & Support**: Promote tool adoption through active social media communication, SEAShot sharingplatform support and evolution, together with dedicated support sections on the OVL forum to streamline user assistance. Support to ESA projects benefiting from OVL type portals (ingestion of specific datasets is covered separately by the projects themselves)

  

Take care and all the best

Craig

  

  

**—**

**![image.png](cid:part1.k2IiHCo0.AlHL21Ep@oceandatalab.com)**

**Dr. CRAIG DONLON**

Head of Earth Observation System Architecture Office

Directorate for Earth Observation Programmes

  

[+](tel:+33153697404 "tel:+33153697404")31  (0)6 27 01 32 44

Craig.Donlon[@esa.int](mailto:name.surname@esa.int "mailto:name.surname@esa.int")

**ESA ESTEC**

Keplerlaan 1, PO Box 299  
NL-2200 AG Noordwijk, The Netherlands

[www.esa.int](http://www.esa.int/ "http://www.esa.int/")

  

  

![ESA_SLOGAN_DS_email.png](cid:part2.kETUnV6L.ae3Fxk1O@oceandatalab.com)

![image.png](cid:part3.bxh8oIY0.xzQdTsW0@oceandatalab.com)

This message is intended only for the recipient(s) named above. It may contain proprietary information and/or protected content. Any unauthorised disclosure, use, retention or dissemination is prohibited. If you have received this e-mail in error, please notify the sender immediately. ESA applies appropriate organisational measures to protect personal data, in case of data privacy queries, please contact the ESA Data Protection Officer ([dpo@esa.int](mailto:dpo@esa.int)).


what we would like to be covered

**Core Objective** : Evolve, maintain, and operate the _Ocean Virtual Laboratory_ platform over a 36-month period, ensuring continuous alignment with the needs of the scientific user community. 

**Real-Time (NRT) Portal Operations**: Ensure automated, continuous updates for data visualization portals. This covers the processing all OVL datasets except Sentinel 1/2/3 (the hudge datasets) meaning all other ESA missions like explorers, non ESA missions, model and in-situ.

**SEAScope Integration & Evolution**: Improve the standalone SEAScope application—which visualizes actual geophysical measurements on a 3D sphere rather than pre-rendered images—and progressively implement remote data access via cloud streaming from the new Zarr based infrastructure.

**Integrate OVL tools in existing ESA infrastructure :** Implement gateways and direct download links to official platforms like the CDSE and two way interaction with ESA toolboxes such as SNAP. OVL tools could be used to allow SNAP users to search for usefull datasets to be analised with SNAP but also combine SNAP outputs to exploit the synergy amongst various datasets.

**User Consultation** : Organize yearly consultation meetings with scientific users to gather feedback from the scientific community and dynamically refine the software development roadmap based on their priorities. I remind you the link on Testimonials 

**Community Outreach & Support**: Promote tool adoption through active social media communication and open dedicated support sections on the OVL forum to streamline user assistance. Support to ESA projects benefiting from OVL type portals (ingestion of specific datasets is covered separately by the projects themselves)

**Educational Tutorials**: Produce interactive tutorials combining OVL portal, SEAScope and Jupyter/iPython notebooks to serve as training material for the ESA Ocean Training Course

what is covered with Betlem

Infrastructure for Sentinel 1/2/3 processing and related setup/operation/monotoring/backup...

what might be out of scope is the Outreach/Education part (apparently Inge's departement is reorganising and communication/outreach/education/promotion will not be kept at division (like Diego) level ?