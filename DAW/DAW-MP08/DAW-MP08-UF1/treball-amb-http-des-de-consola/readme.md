# Treball amb HTTP des de consola
## DAW-MP08-UF1 - Exercici de Servidors web i de transferència de fitxers.
*Objectius: Usar diferents eines per interrogar servidors web que es poden fer servir per depurar programes*

En instal·lació de servidors, però també en desenvolupament web és habitual haver de recórrer a programes aliens per veure què és el que està tornant una aplicació determinada davant de les peticions dels clients: capçaleres, cookies, ... 

Eines per treballar amb HTTP
---------------------------------

### Telnet

El client de telnet es pot fer servir per connectar amb un servidor web i mantenir-hi una conversació fent servir el protocol HTTP. 

1. Feu servir la comanda 'telnet' per connectar-vos a Google (www.google.com) i demaneu per l’arrel. 

2. Mostreu la capçalera obtinguda explicant què significa la línia amb el codi de resposta i les línies de les capçaleres

3. Connecteu amb telnet al servidor de Google España (www.google.es) i demaneu per la pàgina arrel indicant “Connection close”. Captureu la resposta i mostreu les diferències amb la petició anterior

### HTTPie i CURL

L’ús del client telnet no serà possible quan es faci servir HTTP 2. Per això s’haurà de recórrer a altres eines com Httpie o Curl

Comproveu que teniu les eines instal·lades i si no les teniu instal·leu-les (en Windows és una mica més complicat però no massa més … )

4. Connecteu amb http://192.168.0.19  (o http://192.168.4.1) i afegiu una capçalera d'idioma. Comproveu que el mateix recurs es pot obtenir en diferents idiomes ([configuració del servidor](http://192.168.0.19))

- Com es fa amb HTTPie?
- Com es fa amb CURL

5. Voleu enviar un POST a http://projectes.iescendrassos.net/entrada/checklogin.php amb l’usuari ‘coll’ i contrasenya ‘sex’

6. Quina és la resposta? Què faria un navegador en aquest moment?
Heu rebut una cookie? Creieu que podreu reutilitzar-la?

- Com es pot fer amb HTTPie?
- Quina comanda s’ha d’executar amb Curl?

Components del navegador
-----------------------------

### Instal·leu Postman

7. Feu una petició la la pàgina a la que us ha redirigit l’exercici 5. On us ha portat?

8. Feu la mateixa petició però en aquest cas en la petició afegiu-hi la cookie rebuda.

---

#FpInfor #Daw #DawMp08 #DawMp08Uf01

---

###### Autor: Xavier Sala 2017.02.06 09:28:09
###### [CC BY](https://creativecommons.org/licenses/by/4.0/) ![CC BY](https://licensebuttons.net/l/by/3.0/80x15.png)
