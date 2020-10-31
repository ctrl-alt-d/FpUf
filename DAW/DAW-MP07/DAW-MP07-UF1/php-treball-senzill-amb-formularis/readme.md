# PHP - Treball senzill amb formularis
## DAW-MP07-UF1 - Exercici de Desenvolupament web en entorn servidor.
Per fer aquesta pràctica crearem dues pàgines php:

 * **pinta_formulari.php** encarregat de generar el formulari i enviar-lo al navegador.
 * **processa_dades.php** recull i tracta les dades del formulari.

Contingut del primer fitxer, **pinta_formulari.php**
    
    <!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd">
    <html xmlns="http://www.w3.org/1999/xhtml">
    <head>
    <meta http-equiv="Content-Type" content="text/html; charset=UTF-8">
    
    <title>Exemple de formulari</title>
    
    </head>
    
    <body>
    
    <div style="margin: 30px 10%;">
    <h3>My form</h3>
    <form action="processa_dades.php" method="post" id="myform" name="myform">
    
    	<label>Text</label> <input type="text" value="" size="30" maxlength="100" name="mytext" id="" /><br /><br />
    
    	<input type="radio" name="myradio" value="1" /> First radio
    	<input type="radio" checked="checked" name="myradio" value="2" /> Second radio<br /><br />
    
    	<input type="checkbox" name="mycheckbox[]" value="1" /> First checkbox
    	<input type="checkbox" checked="checked" name="mycheckbox[]" value="2" /> Second checkbox<br /><br />
    
    	<label>Select ... </label>
    	<select name="myselect" id="">
    		<optgroup label="group 1">
    			<option value="1" selected="selected">item one</option>
    		</optgroup>
    		<optgroup label="group 2" >
    			<option value="2">item two</option>
    		</optgroup>
    	</select><br /><br />  
       
    	<textarea name="mytextarea" id="" rows="3" cols="30">
    Text area
    	</textarea> <br /><br />
       
    	<button id="mysubmit" type="submit">Submit</button><br /><br />
    
    </form>
    </div>
    
    </body>
    </html>
    
El fitxer **processa_dades.php** és el que rebrà les dades. Les dades es reben en un array associatiu, en aquest cas utilitzarem l'array **$_REQUEST**. 

 1. Analitza els controls que fem servir per a recollir dades, fixat que hi ha controls amb corxets al costat del nom, són per a variables que poden contenir més d'un valor.
 1. Mitjançant la funció *print_r( $variable )* analitza el contingut de la variable *$_REQUEST*. Diferencia el contingut de les variables que contenien corxets amb les que no.
 2. Pinta camp a camp les dades rebudes. Hi haurà camps que podràs pintar directament (Ex: *echo "El valor de text és " . $_REQUEST["mytext"];* ) Altres valors, els que són un array, els hauràs de recorrer tal com s'ha treballat en [exercicis d'arrays](/DAW/DAW-MP07/DAW-MP07-UF1/php-concatenar-elements-dun-array/readme.md) 

Bibliografia: 

 * [$_request](http://www.php.net/manual/es/reserved.variables.request.php)

![Formulari](http://i.imgur.com/k7t8YvQ.png)

Possible solució:

  * [Solució 1](https://docs.google.com/a/xtec.cat/document/d/1Xbpc_GCO-KvfdNeW4nuQhrMg8YjI-llfkb0j0fTS7KA/edit?usp=sharing)

---

#FpInfor #Daw #DawMp07 #DawMp07Uf01

* Resultats d'aprenentatge 3.e
* Continguts 3.5
---

###### Autor: daniel herrera 2013.09.29 13:29:38
###### Editat per: daniel herrera 2016.10.22 11:28:10
###### [CC BY](https://creativecommons.org/licenses/by/4.0/) ![CC BY](https://licensebuttons.net/l/by/3.0/80x15.png)
