# PHP - Manteniment de la informació amb Galetes
## DAW-MP07-UF1 - Exercici de Desenvolupament web en entorn servidor.
El protocol http és sense estat, apren de la wikipedia que és un [protocol sense estat](http://en.wikipedia.org/wiki/Stateless_protocol) i els seus avantatges i inconvenients.

En arquitectura web, disposar d'un protocol *stateless* ens permet crear granjes de servidor i repartir les peticions entre servidors sense cap esforç.

L'inconvenient és que cal que coneguem tècniques per tal de mantenir informació entre peticions.

Una d'aquestes tècniques són les *cookies*.

Pràctica:

 1. Fés tres pàgines enllaçades entre elles: P1.php, P2.php, P3.php (P1.php, ... )
 2. La P1.php enviarà una cookie ('laMevaCookie') al navegador amb valor 100. 
 3. La P3.php mostrarà el valor de la cookie.

Amplicació:

 1. La P1.php comprovarà si la cookie ('laMevaCookie')  existeix, si existeix, en comptes de crear-la amb valor 100 el que farà serà actualitzar-la amb valor 101.

Preguntes:

 1. Quins paràmetres són obligatoris quan creem una cookie?
 2. Que passa si posem el paràmetre [expire](http://es1.php.net/manual/es/function.setcookie.php) a 0?
**Bibliografia:**

 * [Què són les cookies](http://php.net/manual/es/features.cookies.php)
 * [Enviar una cookie](http://www.php.net/manual/es/function.setcookie.php)
 * [Llegir una cookie](http://www.php.net/manual/es/reserved.variables.cookies.php)

**A tenir en compte:**

Les cookies s'envien a les capceleres del missatge http. Això vol dir que no podem enviar ni un caràcter html abans de la cookie, per tant, quan volguem enviar una cookie hem de comprovar sempre que comencem el codi php just al començament del fitxer.

Això estaria bé:

    <?php  
        setcookie("TestCookie", "Hola");

Això malament:

     <?php  
        setcookie("TestCookie", "Hola");

Fixat que la diferència és tot just un inapreciable espai davant *<?php*

**Legislació**

Atenció!! L'ús de les cookie està legislat per tal de mantenir la privacitat de les persones.

*Con el nombre de “Ley de cookies” es como se conoce al punto tercero del articulo 4 del Real Decreto-ley 13/2012, de 30 de marzo que fue publicado en el «Boletín Oficial del Estado» el pasado sábado 31 de marzo de 2012 y entró en vigor al día siguiente. La Ley de cookies, transposición de la Directiva 2009/136/CE, del Parlamento Europeo y del Consejo, de 25 de noviembre de 2009, se integra en la LSSI (Ley 34/2002, de 11 de julio, de servicios de la sociedad de la información y de comercio electrónico) modificando el punto segundo de su artículo 22, que queda redactado de la forma siguiente:*

*Artículo 22.2 de la Ley 34/2002. Los prestadores de servicios podrán utilizar dispositivos de almacenamiento y recuperación de datos en equipos terminales de los destinatarios, a condición de que los mismos hayan dado su consentimiento después de que se les haya facilitado información clara y completa sobre su utilización, en particular, sobre los fines del tratamiento de los datos, con arreglo a lo dispuesto en la Ley Orgánica 15/1999, de 13 de diciembre, de Protección de Datos de Carácter Personal.*

*Cuando sea técnicamente posible y eficaz, el consentimiento del destinatario para aceptar el tratamiento de los datos podrá facilitarse mediante el uso de los parámetros adecuados del navegador o de otras aplicaciones, siempre que aquél deba proceder a su configuración durante su instalación o actualización mediante una acción expresa a tal efecto.*

*Lo anterior no impedirá el posible almacenamiento o acceso de índole técnica al solo fin de efectuar la transmisión de una comunicación por una red de comunicaciones electrónicas o, en la medida que resulte estrictamente necesario, para la prestación de un servicio de la sociedad de la información expresamente solicitado por el destinatario.*

*Más info en [luisjuan.es](http://www.luisjuan.es/seo/normativa-ue-sobre-cookies)*

---

#FpInfor #Daw #DawMp07 #DawMp07Uf01

* Resultats d'aprenentatge 4.a
* Continguts 4.1
---

###### Autor: daniel herrera 2013.10.07 14:16:31
###### Editat per: daniel herrera 2014.10.06 15:01:38
###### [CC BY](https://creativecommons.org/licenses/by/4.0/) ![CC BY](https://licensebuttons.net/l/by/3.0/80x15.png)
