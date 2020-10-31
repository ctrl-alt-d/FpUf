# Emmagatzematge en xarxa
## SMX-MP06-UF2 - Exercici de còpies de seguretat.
Introducció
--------------
Sovint els sistemes de xarxa necessiten algun tipus d'espai d'emmagatzematge en el que desar els seus resultats de manera que sigui accessible. Però quan aquestes dades són vitals per l'organització s'ha s'ha de minimitzar al màxim la possibilitat de que es perdin. La solució obvia consisteix en emmagatzemar aquestes dades en més d'un lloc

Tenir discs en RAID és una possible solució però la seguretat s'incrementa si les dades no s'emmagatzemen només en la mateixa màquina sinó que s'emmagatzemen en diferents màquines alhora. Per això s'han creat els clusters d'emmagatzematge

Hi ha diversos sistemes de fitxers de cluster d'alta disponibilitat que estan pensats per replicar les dades en diferents sistemes alhora formant un cluster però en sistemes Unix un de senzill és [Glusterfs](http://www.gluster.org) 

Glusterfs és un sistemes de fitxers distribuït de codi obert que pot escalar-se per arribar fins a 72 brontobytes i pot atendre a milers de clients alhora. Pot funcionar a través de Infiniband RDMA o TCP/IP

Gluster pot funcionar de diferents formes. Per exemple permet unir els diferents espais de disc de les diferents màquines en un de manera que tot es vegi com un sol espai de disc amb la suma dels espais (també pot funcionar com un volum 'stripped')

![suma espais](http://img593.imageshack.us/img593/7230/v7a9.png "fucionament gluster")


I també permet fer que el contingut dels espais d'emmagatzematge de diferents màquines sigui exactament el mateix

![Mirroring](http://img833.imageshack.us/img833/8411/igpj.png "fucionament gluster")

I qualsevol combinació que se'ns acudeixi

###Instal·lació
La majoria de distribucions de Linux tenen *Gluster *en els seus repositoris. En general hi sol haver un paquet pels servidors anomenat 'server' i un paquet pels clients anomenat 'client'. Per tant es pot instal·lar el paquet en cada una de les màquines:

    # apt-get install glusterfs-server

En alguns casos s'ha trobat que hi havia problemes si es barregen les versions de gluster. 

Una de les formes d'evitar trànsit de xarxa innecessari és eliminar la possibilitat de que s'hagin de fer peticions DNS per resoldre els membres del grup. Per tant es recomanen dues coses:

1. Definir els membres en el fitxer */etc/hosts*

    Això minimitzarà les peticions 

2. Crear una  subxarxa específica per connectar el trànsit entre màquines

    D'aquesta forma el trànsit de Gluster no interferirà en el funcionament de la xarxa

O sigui que: 

    127.0.0.1 localhost.localdomain localhost
    192.168.0.101 servidor1.emmagatzematge server1
    192.168.0.102 servidor2.emmagatzematge server2

Un cop instal·lat el servidor en les diferents màquines des només d'un d'ells (la configuració es replica automàticament) s'han de definir quins són els servidors que formen part de l'emmagatzematge. 

    # gluster peer probe server2

Sempre es pot comprovar quants “companys” hi ha i si estan disponibles amb la comanda “*gluster peer status*”

Un cop es tenen els companys només cal definir que volem fer amb els diferents volums: 

a. Definir un espai de disc replicat en els dos servidors es pot fer: 

    # gluster volume create compartit replica 2 transport tcp server1:/disc server2:/disc

b. Fer una agregació dels espais de disc s'han de crear grups: 

    # gluster volume create mega transport tcp server1:/disc server2:/disc

c. Definir un volum stripped (emmagatzemar-ho tot en blocs petits a través dels volums: 
 
    # gluster volume create tease stripe 2 transport tcp server1:/disc server2:/disc

Si es tenen diferents volums es poden combinar les opcions per fer coses més elaborades

###Iniciar el servei
Un cop creat el volum s'ha d'iniciar: 

    # gluster volume start compartit 

Hi ha moltes altres comandes que permetran gestionar el funcionament del volum. Per comprovar en quin estat es troben els volums:

    # gluster volume info

Gluster per defecte deixa que tothom accedeixi al volum però es pot controlar l'accés al volum amb les comandes auth.allow i auth.deny

    # gluster volume set compartit auth.allow 192.168.5.1

Els volums es poden expandir, fer més petits, afegir i treure particions, etc... 

###Instal·lació del client
Per fer servir un volum Gluster s'ha d'instal·lar el paquet client

    # apt-get install glusterfs-client

I després només cal fer el que es fa sempre en dispositius Unix: muntar-lo amb **mount**. Per muntar-lo es pot fer servir qualsevol dels dos servidors de rèplica

    # mount -t glusterfs server1:/compartit /mnt/compartit

I evidentment es pot definir a /etc/fstab:

    server1:/testvol /mnt/glusterfs glusterfs defaults,_netdev 0 0

Un cop muntat no hi ha cap diferència amb un volum normal. Es pot compartir amb Samba, NFS, etc...

Tasca: Muntar un cluster de discs
------------------------------------

1. Configureu dues màquines virtuals Linux que estiguin connectades entre elles a través d'una interfície pont però que també tinguin una interfície amb adaptador pont

![Gluster](http://img12.imageshack.us/img12/3033/lxg5.png "GLuster en acció")

2. Afegiu un disc d'1GB a les dues màquines

3. Configureu glusterfs en les dues màquines perquè facin mirror dels discs

4. Des d'una altra màquina munteu el volum i afegiu un arxiu amb el vostre nom

5. Des dels dos servidors comproveu si l'arxiu ha aparegut

6. Accediu a l'espai de disc des de Windows (feu el que calgui)

7. Afegiu un arxiu des de Windows i comproveu si l'altre client el pot veure

8. Atureu una màquina virtual i comproveu si els clients encara tenen accés al sistema de fitxers. 

9. Afegiu un arxiu i comproveu que es replica

10. Torneu a iniciar la màquina virtual que havíeu aturat  i comproveu si sincronitza o no

11. Un cop hagin sincronitzat munteu el disc compartit des del servidor A i afegiu un arxiu. El veuen els clients?

---

#FpInfor #Smx #SmxMp06 #SmxMp06Uf02

* Resultats d'aprenentatge 1.3 1.4
* Continguts 1.2 1.3
---

###### Autor: Xavier Sala 2013.10.28 09:27:45
###### Editat per: Xavier Sala 2013.11.03 22:01:39
###### [CC BY](https://creativecommons.org/licenses/by/4.0/) ![CC BY](https://licensebuttons.net/l/by/3.0/80x15.png)
