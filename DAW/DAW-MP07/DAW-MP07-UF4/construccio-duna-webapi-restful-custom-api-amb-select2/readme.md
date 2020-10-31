# Construcció d'una WebApi RESTful + custom api amb select2
## DAW-MP07-UF4 - Exercici de Serveis web. Pàgines dinàmiques interactives. Webs Híbrids.
Es tracta de construir una aplicació senzilla i dotar-la d'una RESTful API i d'una custom API que s'integra amb AJAX.

Farem servir a la part client les llibreries [select2](https://select2.org/data-sources/ajax) que ens aïllaran de la complexitat de la part client.

L'aplicació ja està construida per passes a github, hi ha [14 commits](https://github.com/ctrl-alt-d/net-core-webapi-select2/commits/master) des de la creació de l'aplicació fins al ple funcionament.

La idea és la següent: de vegades no és correcta enviar tots els valors a una `<select>`, per exemple una taula amb 1000 persones no és convenient enviar-la sencera al client, només hauriem d'enviar aquelles persones que el client vol veure, les que contingun certs caràcters al nom, per exemple.

A la pràctica és crea una taula de persones i s'emplena. Inicialment s'envien totes les persones en un formulari i després es modificar per enviar només les persones que l'usuari tria:

![](https://raw.githubusercontent.com/ctrl-alt-d/net-core-webapi-select2/master/wwwroot/images/demo_select2_dotnet_core.gif)

Les passes per a fer la pràctica serien:

* [Explicació del que farem](https://youtu.be/YDjYbBN8ILM) 11'
* [Creació de l'aplicació, dependències i paquets.](https://youtu.be/0HoAKaDVH4E) 16'
* [Afegir models i context. Configurar la connexió a la base de dades.](https://youtu.be/HJp7yd9x6cs) 13'
* [Migracions](https://youtu.be/8_w-T6pirmI) 13'
* [Fer pàgina senzilla que inserti dades de prova.](https://youtu.be/WYsd_SLvQco) 19'
* [Afegir controlador MVC per fer CRUP de persones.](https://youtu.be/pj0IKHV50nI) 14'
* [Afegir controlador RESTFul api.](https://youtu.be/73ja_DHszeI) 6'
* [Crear pàgina Razor amb una `<select>` html clàsica.](https://youtu.be/6g8gTo6fnjA) 7'
* [Afegir select2 per transformar la select bàsica en una select rica.](https://youtu.be/xpwWeq-pH0g)
* [Carregar les dades via ajax en comptes d'enviar totes les dades des del client.](https://youtu.be/qyeXE9-TlO0)

---

#FpInfor #Daw #DawMp07 #DawMp07Uf04

---

###### Autor: daniel herrera 2018.03.10 22:20:05
###### Editat per: daniel herrera 2018.03.15 14:46:04
###### [CC BY](https://creativecommons.org/licenses/by/4.0/) ![CC BY](https://licensebuttons.net/l/by/3.0/80x15.png)
