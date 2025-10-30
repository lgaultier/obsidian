# Fronts
[https://journals.ametsoc.org/view/journals/atot/38/2/JTECH-D-20-0118.1.xml](https://journals.ametsoc.org/view/journals/atot/38/2/JTECH-D-20-0118.1.xml)

  

[https://www.sciencedirect.com/science/article/abs/pii/S0924796309000682](https://www.sciencedirect.com/science/article/abs/pii/S0924796309000682)

  

[https://www.sciencedirect.com/science/article/abs/pii/S0924796309000682](https://www.sciencedirect.com/science/article/abs/pii/S0924796309000682)

  

[https://www.sciencedirect.com/science/article/abs/pii/S0924796309000694?via%3Dihub](https://www.sciencedirect.com/science/article/abs/pii/S0924796309000694?via%3Dihub)

Here’s the poster I presented on Tuesday:

“Linking shelf-sea fronts and biodiversity for improved planning of offshore renewable developments”

[https://rsg.pml.ac.uk/shared_files/pim/presentations/miller_frontward_poster_lps_vienna_jun2025_a4.pdf](https://rsg.pml.ac.uk/shared_files/pim/presentations/miller_frontward_poster_lps_vienna_jun2025_a4.pdf)

I mentioned I spotted a front dataset paper recently, but don’t know if it’s any good:

Xing, Qinwang, Haiqing Yu, Wei Yu, Xinjun Chen, and Hui Wang. ‘A Global Daily Mesoscale Front Dataset from Satellite Observations: In Situ Validation and Cross-Dataset Comparison’. _Earth System Science Data_ 17, no. 6 (24 June 2025): 2831–48. [https://doi.org/10.5194/essd-17-2831-2025](https://doi.org/10.5194/essd-17-2831-2025).

And here’s an older global front paper:

Mauzole, Y.L. (2022) ‘Objective delineation of persistent SST fronts based on global satellite observations’, _Remote Sensing of Environment_, 269, p. 112798. Available at: [https://doi.org/10.1016/j.rse.2021.112798](https://doi.org/10.1016/j.rse.2021.112798).

# PM2
Dear Johnny and all,  
  
thank you again for the opportunity today, the meeting was very inspiring!  
Here I send the link to the paper Bruno asked me to send around:  
[https://doi.org/10.5194/os-20-1611-2024](https://doi.org/10.5194/os-20-1611-2024)  
  
Looking forward to seeing you again!  
  
Best wishes  
Luca

Not sure if this is useful, but NIOZ has been running a profiling mooring array in the Irminger Sea from which might be useful for validating MLD. Here is a link to part of that data (including some refs)

  

[https://dataverse.nioz.nl/dataset.xhtml?persistentId=doi:10.25850/nioz/7b.b.rg](https://dataverse.nioz.nl/dataset.xhtml?persistentId=doi:10.25850/nioz/7b.b.rg)

  

Best,

  

-Aleksi


disponible tout de suite au téléchargement on a :

  - la [SSH, SSU, SSV horaire](https://ige-meom-opendap.univ-grenoble-alpes.fr/thredds/catalog/meomopendap/extract/MEOM/eNATL60/eNATL60-BLB002/1h/eNATL/all_nc/catalog.html) sur tout le domaine : 1.9T (run sans marée, du 01/07/2009 au 30/06/2010)

  - [idem](https://ige-meom-opendap.univ-grenoble-alpes.fr/thredds/catalog/meomopendap/extract/MEOM/eNATL60/eNATL60-BLBT02/1h/eNATL/all_nc/catalog.html) pour le run avec marée : 1.8T

  - la [SSH](https://ige-meom-opendap.univ-grenoble-alpes.fr/thredds/catalog/meomopendap/extract/MEOM/eNATL60/eNATL60-BLB002/1d/SSH/catalog.html), [SST](https://ige-meom-opendap.univ-grenoble-alpes.fr/thredds/catalog/meomopendap/extract/MEOM/eNATL60/eNATL60-BLB002/1d/SST/catalog.html) journalière sur tout le domaine : 264G (run sans marée, du 01/07/2009 au 30/06/2010)

  - des champs 3D TSUVW dans la [région SICIL](https://meom-group.github.io/meom-data-catalog/content/regions/SICIL.html) pour les 2 runs

  - des champs 3D TS dégradés au 1/20° dans [la région GULF](https://meom-group.github.io/meom-data-catalog/content/regions/GULF.html)

  

disponible facilement (après transfert depuis supercaculateur) on a :

  - MLD  journalière run avec marée : 130G

  - MLD horaire run sans marée : 474G

  - d’autres petites régions en 3D : Labrador, golfe du Lion, entre les îles Faroé et Shetland

  

je peux aussi facilement extraire la SSS pour tout le domaine + autre région en 3D

  

Par contre on n’a pas sauvé N2 au cours de la simu mais je peux la recalculer avec un [cdftool](https://github.com/meom-group/CDFTOOLS/blob/master/src/cdfbn2.f90) mais ça risque d’être long.

  

Dis-moi ce qu’il te faut !

++

Aurélie

Hello Fabrice,
les profileurs déployés dans la zone du Dôme de Guinée étaient pour le 
projet SEANOX
de Xavier Capet. C'étaient 1 profileur DO-ARGO et 1 BGC-ARGO en 2021.
le BGC: WMO 6903091 IMEI 300125061203860
le DO: 6903067 et 300534060600580
bb

