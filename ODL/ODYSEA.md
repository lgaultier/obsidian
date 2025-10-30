Merci pour tes infos Clément.  
  
En fait, j'utilise l'angle bearing pour transformer les sigmas de l'erreur instrument along- et across-track en sigma nord et est. 

En utilisant tel quel l'angle défini dans les fichiers obs, je vais donc utiliser les formules :

  

sigma_u = cos(bearing) * sigma_ac + sin(bearing) * sigma_al

sigma_v = -sin(bearing) * sigma_ac + cos(bearing) * sigma_al

En effet le bearing angle est inversé.  
Je m'en sors en appliquant la correction de la manière suivante :  
  
   bearing = numpy.array(fcid.variables['bearing'][:])*numpy.pi/180  
   azimuth_fore = numpy.array(fcid.variables['azimuth_fore'][:])*numpy.pi/180 - 2*bearing[:,numpy.newaxis]  
   azimuth_aft = numpy.array(fcid.variables['azimuth_aft'][:])*numpy.pi/180 - 2*bearing[:,numpy.newaxis]  
  
Ensuite les variables azimut fore et aft sont dans la bonne direction normalement, définis par rapport à un vecteur qui pointe vers l'Est.  
  
Dis moi si ca coince encore, si oui n'hésites pas à m'envoyer tes routines de lecture pour que je regarde.  
  
Clément
  

Merci,

Isabelle