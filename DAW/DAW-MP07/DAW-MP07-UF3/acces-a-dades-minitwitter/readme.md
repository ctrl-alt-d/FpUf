# Accés a dades - MiniTwitter
## DAW-MP07-UF3 - Exercici de Tècniques d’accés a dades.
# MiniTwitter
En aquesta pràctica es treballa:

- Variables de sessió $_SESSION.
- Seguretat: zona restringida i control d'usuaris. 
- Formularis: mètode POST (opcionalment GET). 
- Accés a dades amb PDO. 

En aquesta activitat es tracta de fer una aplicació web amb PHP i MySQL similar al Twitter que l’anomenarem el **MiniTwitter**.

L’estructura de la base de dades de l’aplicació serà la següent:

![Base de dades](http://i.imgur.com/fbbMzMl.png)

### Requeriments mínims per aprovar

Les pàgines a realitzar són les següents:

- ***funcions.php*** - Per tal d’organitzar el codi de l’aplicació, totes les funcions que accedeixin a la base de dades estaran en aquest fitxer. Hi haurà funcions com:  
    - comprovarUsuari (user, passwd) 
    - addUsuari (name, username, passwd) 
    - getMissatges (userId) 
    - addMissatge (userId, text) 

    ***Nota:*** Hi ha altres formes millors d’organitzar el codi de l’aplicació, per exemple utilitzant patrons de disseny com MVC.

- ***formulari_signin.php*** - Recull amb un formulari les dades de l’usuari i crea un nou compte per aquest usuari a la base de dades. 

    **Important!** Les contrassenyes MAI s'emmagatzemen en text pla, cal fer una transformació hash de les mateixes, per exemple amb MD5.

- ***formulari_login.php*** - Recull usuari i password amb un formulari.  

    Envia usuari i passwd a processa_login.php.

- ***processa_login.php*** - Comprova usuari i password respecte la base de dades.  
   Si és correcte, redirigeix cap a inici.php posant les dades de l'usuari a la l'array associatiu de sessió. 
    En cas contrari, si usuari i password no és correcte, informa de l'error i redirigeix cap a formulari_login.php.

A partir d'aquí totes les pàgines requereixen haver-se autenticat poder accedir-hi: 

**Atenció!** el codi per comprovar que l'usuari ha iniciat sessió ha d'estar dins un include.

- ***inici.php*** - Dona la benviguda a l’usuari mostrant un missatge de “Benvingut al MiniTwitter NOM_USUARI” i mostra tots els seus tuits ordenats de més actual a més antic. 

    Conté enllaç a un formulari que permet afegir un tuit amb l’usuari actual.

- ***formulari_tweet.php*** - Formulari per crear un tweet, només usuaris autenticats.

- ***processa_tweet.php*** - Crea el tweet. Patró PRG. Ens porta a inici.php i mostra missatge 'Tweet creat correctament'. Envia el missatge per cookie.

- ***sortir.php*** - Finalitza la sessió i elimina les variables de sessió.

Nota: la pàgina inici.php ens mostra opció de login o registrar-nos en cas de no haver fet loguin. Aquesta pàgina, si voleu, es pot dir index.php. 

### Requeriments opcionals 

- Fes que la pàgina inici.php mostri els missatges segons l'usuari escollit amb un desplegable on es mostren tots els usuaris de la base de dades. 
- Fes que es pugui eliminar un tuit. 
- Fes que es pugui fer un *Like* a un tuit i es mostri el nombre de *Likes* que cada tuit. 
- Fes que es pugui seguir a altres usuaris i al entrar al MiniTwitter es mostrin tots els tuits dels usuaris que segueixes.

---

#FpInfor #Daw #DawMp07 #DawMp07Uf03

---

###### Autor: Sergi Coll 2016.12.01 13:33:25
###### Editat per: daniel herrera 2017.10.26 15:14:22
###### [CC BY](https://creativecommons.org/licenses/by/4.0/) ![CC BY](https://licensebuttons.net/l/by/3.0/80x15.png)
