# Obtenir informació sobre un objectiu 2
## SMX-MP06-UF4 - Exercici de seguretat activa.
Informació a Internet
---------------------------
Un dels primers objectius d’un atacant sol ser tenir tanta informació de la víctima com sigui possible. Per tant la primera cosa que ha de fer és obtenir tota la informació que pugui de la víctima.

### Google Hacking

Una font d’informació evident són els cercadors. Fent servir els operadors dels cercadors es poden fer cerques molt més afinades del que es pot fer normalment

    site: Permet obtenir resultats inclosos en determinats llocs o dominis.
    related:Permet cercar llocs similars a l’adreça especificada
    OR: Permet cercar pàgines que inclouen una o diverses paraules 
    info: Permet obtenir informació sobre una adreça web, com ara la versió de la pàgina desada a la memòria cau, pàgines semblants i pàgines amb enllaços al lloc
    cache: Permet veure l’aspecte que tenia una pàgina la darrera vegada que Google hi va accedir
    intext: Els resultats tindran el text especificat
    intitle: Cerca segons el títol de la pàgina
    inurl: Cerca que el text estigui en la URL
    inarchor: Resultats en els enllaços
    filetype: Els resultats només seran fitxers del tipus especificat

### FOCA
FOCA (Fingerprinting Organizations with Collected Archives) és una eina que es fa servir sobretot per trobar metadades que està emmagatzemada en documents que les empreses publiquen a la web. Pot analitzar documents de diferents tipus que van des de Office, OpenOffice, PDF, o fins i tot imatges per extreure'n informació sobre usuaris, hosts, etc... 

Es pot trobar a [ElevenPaths](https://www.elevenpaths.com/labstools/foca/index.html#) 


Activitat
----------------

### Google Hacking

1. Feu servir Google per descobrir quins són els noms de host que hi ha definits a iescendrassos.net

2. Feu servir Google per descobrir en quines pàgines es parla de la directora

3. Localitzeu els fitxers PDF que té Google registrats i que hi ha en la web del cendrassos www.iescendrassos.net

### Foca

4. Descobriu el domini de dues empreses de la comarca i fent servir FOCA comproveu si els documents que tenen en les seves webs tenen "metadades"
    - Quina informació hi heu descobert?
    - N'heu pogut deduir alguna cosa més? (Sistema operatiu, hosting, etc ... )

5. Feu servir la part de descobrir la xarxa per intentar fer-vos una idea més clara de com és cada empresa
    - Dominis públics a Internet
    - Sistemes operatius que fan servir
    - Programes que usen
    - Noms de treballadors

---

#FpInfor #Smx #SmxMp06 #SmxMp06Uf04

---

###### Autor: Xavier Sala 2017.02.06 09:52:00
###### Editat per: Xavier Sala 2017.02.06 09:52:00
###### [CC BY](https://creativecommons.org/licenses/by/4.0/) ![CC BY](https://licensebuttons.net/l/by/3.0/80x15.png)
