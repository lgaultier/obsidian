---
start time: 2025-07-08 11:00
topics: meeting
Created: 2025-07-08 11:07
Modified: 2025-07-07 21:07
aliases: 
tags:
  - OVL
  - mom
end time: 2025-07-08 13:00
---

---

# meeting-lobellia 

<% tp.file.cursor(1) %>

# 📍 Location
Date: 2025-07-08
Time: 11:00
Location: Google Meet

# 🧑‍🧑‍🧒 Participants
- Allison Shaylor
- Cristian Florindo
- Isadora Jimenez
- Ziad El Khoury Hanna
- Fabrice Collard
- Lucile Gaultier

# 🗓️ Agenda
| Time  | Topic                   |
| ----- | ----------------------- |
| 11:00 | Welcome                 |
| 11:10 | Jupyter tutorial review |
| 11:30 | Feedback mecanism       |

# ✔️ Decisions to make
## Jupyter / tutorial review:
- [x] decide if materials should be on github, ODL website 
- [x] Should we use binder or google Collab ? 
[ ] Add details in Jupyter notebooks before putting them online
- [ ] Add slides into Jupyter notebooks
## Feedback mecanisms
* [x] Decide if we use github, the same for Jupyter ? 
* [x] Should we implement a contact form ? or prefill an email ?

# 🗒️ Notes

## Jupyter / tutorial review:
* Gather resources in the same plot
* Not enough information when using jupyter notebook outside of the event (where it is obvious that an external expert has presented the topic)
* A lot of extra step, lack of clarity for the setup
* more details information and troubleshooting for stand alone online jupyter notebook
* Include slides in Jupyter notebook
* Binder can be associated with github or google collab but how to communicate with SEAScope ? 
* 

## Feedback mecanisms
Fab: add that we are also interested in which datasets are being used

We need to clarify with Briac: **“Can you provide the IDF so that you can choose the dataset you want and the period?”** 

* Main feedback on the OVL portal is that users want more control and easier downloads
* Regarding feedback mecanism, users want no forum, no additional login, the following tools have been mentionned 
	* chatbox ? too disruptive for some
	* emails
	* github
* Recommendation is to use google statistics: Look at the difference between AWS stat vs google analytics and the possibility to get more info regarding the products selected. It is possible using AWStat and send a log. We are interested in statistics per product to know if some are costly and not used. 
* Track also the feature usage
* Github: decide if we use it, is it the same as for the jjupyter
* Permanent form embedded on our website complentary to github for non-geeky people
* Live poll and feedback using "Mentimeter" ?
* Do interviews every few years.
* Add during call for testimony a possibility for people to be interviewed
* ODL requests to be Cited in Publications
* ODL can conduct the interviews but make it clear that we want to hear about the painful points.

# Action
- [x] Check with Sylvain which logs are available and if we can retrieve information regarding the product usage.
- [x] Should we use binder or google Collab ? Binder can be associated with github or google collab but how to communicate with SEAScope ? 
- [ ] Add details in Jupyter notebooks before putting them online -> Lucile + all
- [ ] Add slides into Jupyter notebooks -> Lucile
- [ ] Write text how to cite / tell us if you use it in publication / presentation -> Fab

Difficulty to download
Decision
* Usage analytics: 
	* clique sur carte et timespan, on a peut être déjà l'info pour avoir l'idée des produits utilisées, combien de temps le produit est utilisé. On peut retirer les logs ou le portail est ouvert pad défaut.
	* Track also features: difficult to implement.
* Feedback mechanisms: 
	* contact form: certaines personnes n'ont pas de client mail, pour éviter les spams des solutions existent. Captcha google. contact form envoie un email, peut être après faire une BD mais cela demande plus de developments. Voir aussi comment analyser automatiquement les emails. 
	* Github: les ISSUEs, WIKI, et les jupyter  au même endroit 
	* Google Collab ne communiquera pas par contre à vérifier pour Binder