# PHP - El patró PGR (Post/Redirect/Get)
## DAW-MP07-UF1 - Exercici de Desenvolupament web en entorn servidor.
El [patró PGR](http://en.wikipedia.org/wiki/Post/Redirect/Get) consisteix a fer una redirecció després d'haver rebut dades via POST. La intenció és prevenir submits duplicats.

Per a realitzar aquest exercici cal utilitzar el codi desenvolupat a l'exercici [PHP, treball amb post](/DAW/DAW-MP07/DAW-MP07-UF1/php-treball-amb-post/readme.md)

 1. Executa el codi anterior: Ompla el formulari i fes submit (via post) de les dades.
 2. Fes un refresh del resultat del form. Observaràs que el navegador et pregunta si vols tornar a enviar les dades, això és el que volem evitar.
 3. Per evitar això, després de processar les dades, [redirigirem](http://php.net/manual/en/function.header.php) o bé al formulari si hi ha errors o bé a una segona pàgina **p1.php**.


Què es fa a la programació real? Doncs es treballa semblant amb això, si hi ha errors es torna a mostrar el formulari, amb els valors que ja havia entrar l'usuari, per tal que no els hagi de tornar a picar, i mostrant quin és l'error. I si no hi ha error, s'envia a una pàgina genèrica tot utilitzant algun [sistema de missatges](https://docs.djangoproject.com/en/dev/ref/contrib/messages/) per indicar que tot ha anat bé.

![Patró PRG](http://i.imgur.com/CqjHGzE.png)



---

#FpInfor #Daw #DawMp07 #DawMp07Uf01

* Resultats d'aprenentatge 3.f
* Continguts 3.6
---

###### Autor: daniel herrera 2013.09.30 14:01:39
###### Editat per: daniel herrera 2016.10.22 11:25:54
###### [CC BY](https://creativecommons.org/licenses/by/4.0/) ![CC BY](https://licensebuttons.net/l/by/3.0/80x15.png)
