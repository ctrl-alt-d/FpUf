# PHP + Javascript: Execució al cient vs execució al servidor
## DAW-MP07-UF1 - Exercici de Desenvolupament web en entorn servidor.
Estudia i executa aquest tall de codi:

    <!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd">
    <html xmlns="http://www.w3.org/1999/xhtml">
    <head>
    <meta http-equiv="Content-Type" content="text/html; charset=UTF-8">
    
    <title>Pràctica hello world</title>
    
    <script type="text/javascript">
    var i=0;
    var ii=1;	
    function f_incrementa(){
       var iii=i+ii;
       i= ii;
       ii=iii;
       document.getElementById('incrementa').innerHTML += ', ' + iii;   
       return false;
    };
    </script>
    
    <style type="text/css">
    	
    </style>
    
    </head>
    
    <body>
        <?php
        echo( "<h1>La meva sèrie fibonacci</h1>" );
        ?>
        <b id='incrementa'>0</b> </p> 
        <input type='button' onclick='f_incrementa()' value='Següent'/>	
    <p>
    Benvinguts al curs de PHP.	
    </p>
    </body>
    </html>
    
 1. Coloreja en verd la part que s'executa al client i en blau la part s'executa al servidor? Deixa en negra la part que no s'executa, és a dir, la part estàtica.


---

#FpInfor #Daw #DawMp07 #DawMp07Uf01

* Resultats d'aprenentatge 1.a
* Continguts 1.1
---

###### Autor: daniel herrera 2013.09.29 12:31:42
###### Editat per: Sergi Coll 2016.10.07 13:26:37
###### [CC BY](https://creativecommons.org/licenses/by/4.0/) ![CC BY](https://licensebuttons.net/l/by/3.0/80x15.png)
