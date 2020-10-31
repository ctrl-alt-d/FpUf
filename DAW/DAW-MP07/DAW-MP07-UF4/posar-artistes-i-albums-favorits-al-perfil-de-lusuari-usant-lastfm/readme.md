# Posar artistes i àlbums favorits al perfil de l'usuari usant Last.fm
## DAW-MP07-UF4 - Exercici de Serveis web. Pàgines dinàmiques interactives. Webs Híbrids.
Es tracta de fer una pràctica amb django, MVC de microsoft o algun altre framework que suporti usuaris.

Cal fer un nou model `ArtistaFavorit` de manera que un usuari tingui N artistes favorits.

Pots extendre el model usuari tal com et proposi el teu framework, si fas servir django et suggereixo crear un model `Perfil` en relació 1:1 amd User.

La pràctica consisteix en crear un formulari per a que l'usuari, un cop loginat, pugui posar al seu perfil quins són els seus artístes favorits.

Per això li apareixerà un text box amb typeahead, pots fer servir [Twitter Bootstrap Ajax Typeahead Plugin](https://github.com/biggora/bootstrap-ajax-typeahead).

És important que la crida ajax es faci a la teva aplicació django i que sigui aquesta qui consulti a last.fm l'artista i retorni a l'usuari la resposta. D'aquesta manera mai veuran quina és YOUR_API_KEY.

Pots trobar més informació sobre com registrar-te i fer servir la api de last fm a l'exercici [Consultant la API de last.fm
](/DAW/DAW-MP04/DAW-MP04-UF2/consultant-la-api-de-lastfm/readme.md)

####Nota: pots començar per fer un simple formulari per triar artista preferit sense haver d'assignar-lo al teu perfil. ####


***Solució***

* Codi: https://github.com/ctrl-alt-d/practicaLastFM
* Video: https://youtu.be/gArdYcp_UHs

---

#FpInfor #Daw #DawMp07 #DawMp07Uf04

---

###### Autor: daniel herrera 2017.02.21 15:11:24
###### Editat per: daniel herrera 2017.03.20 15:26:05
###### [CC BY](https://creativecommons.org/licenses/by/4.0/) ![CC BY](https://licensebuttons.net/l/by/3.0/80x15.png)
