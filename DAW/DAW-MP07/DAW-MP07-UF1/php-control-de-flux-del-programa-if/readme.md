# PHP - Control de flux del programa: IF
## DAW-MP07-UF1 - Exercici de Desenvolupament web en entorn servidor.
En aquesta primera unitat formativa estem treballant sense 'pantilles'. Això vol dir que el codi del programa queda barrejat amb el codi html. Això és una manera de treballar molt bruta, però ens serveix per:

 * Poder fer els exercicis més senzills.
 * Veure lo lleig que és barrejar la presentació amb el codi.

Aquesta manera de treballar **no l'hauriem d'aplicar mai en un programa comercial**, és un treball purament acadèmic i temporal que ens ha de servir només pels punts esmentats.

Dit això, anem a aplicar, d'aquesta manera tant bruta, codi PHP encastat i barrejat amb codi html.

    <!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd">
    <html xmlns="http://www.w3.org/1999/xhtml">
    <head>
    <meta http-equiv="Content-Type" content="text/html; charset=UTF-8">
    
    <title>Comanda IF </title>
    </head>
    <body>
    	
    <div style="margin: 30px 10%;">
    <?php
    if($_SERVER['REQUEST_METHOD'] != 'POST') {
    ?>
    <h3>My form</h3>
    <form action="" method="post" id="myform" name="myform">
    
    	<label>Com et dius?</label> <input type="text" value="" size="30" maxlength="100" name="nom" id="" /><br /><br />
       
    	<button id="mysubmit" type="submit">Submit</button><br /><br />
    
    </form>
    <?php
    } else {
    ?>
    <h3>My results</h3>
    <p>El teu nom és <?php echo( $_POST['nom']); ?> </p>
    <?php
    }
    ?>
    </div>
    </body>
    </html>


 1. Executa aquest codi al teu ordinador.
 2. Identifica on hi ha codi PHP de control de flux de programa.
 3. Fixat que el codi PHP està realment encastat al codi HTML, hi ha operacions que s'obren i no es tanquen fins força més aball.
 4. Fixa't també que action no conté cap valor. Això vol dir la pròpia pàgina.







---

#FpInfor #Daw #DawMp07 #DawMp07Uf01

* Resultats d'aprenentatge 3.a
* Continguts 3.1
---

###### Autor: daniel herrera 2013.09.30 14:21:43
###### Editat per: daniel herrera 2013.10.04 13:25:20
###### [CC BY](https://creativecommons.org/licenses/by/4.0/) ![CC BY](https://licensebuttons.net/l/by/3.0/80x15.png)
