# PHP - Autenticació d'usuaris
## DAW-MP07-UF1 - Exercici de Desenvolupament web en entorn servidor.
[Familiaritzat amb els mecanismes d'autenticació en aplicacions web](https://docs.google.com/presentation/d/1miYlgd_uPpoyqeIDMFKn-Y9uUMo5xMvX2JaptBq-sMs/edit). Utilitzarem en aquesta pràctica l' [autenticació amb formulari](https://docs.google.com/presentation/d/1miYlgd_uPpoyqeIDMFKn-Y9uUMo5xMvX2JaptBq-sMs/edit#slide=id.ge718d2ff9_0_104) (*).

![Autenticació amb formulari](http://i.imgur.com/48YsJ4b.png)

Típicament emmagatzemem els usuaris a una base de dades: usuari, password (com a hash de la password ). Però encara no hem estudiat l'accés a dades, per tant, el que farem serà un array d'usuaris:

    <?php
    $usuaris = array( "pere"=>"secret", "joan"=>"rambo", "marta"=>"ramba", ...

Podran entrar els usuaris que apareixen llistats a l'array sempre que presenti la seva passwod.

Pràctica:

 1. **P0.php** Fes un formulari que demani usuari i passwd.
 2. **P1.php** Valida l'usuari respecte $usuaris. Si és correcta mostrarà un enllaç per anar a **P2.php** en cas contrari, apareixerà un enllaç per anar a **P0.html**.
 3. **P2.php** És una pàgina que només poden veure els usuaris registrats. Cal comprovar que l'usuari està registrat.

Com farem per registrar usuaris? **P1.php** validarà l'usuari i si es correcta crearà una entrada a $_SESSION['usuari']=usuari_que_hem_validat.

Com ho farem per controlar l'accés a **P2.php**? Només podran entrar els usuaris registrats, si no apareix l'entrada *$_SESSION['usuari']* llavors cal reenviar a **P0.php**

Fixat que és necessari l'ús de sessions en aquesta pràctica.


(*)Presentació i dibuixos de [Xavi Sala](https://uf.ctrl-alt-d.net/usuaris/mostra/22/)


Solució 
====

*by [@darth_rafas](https://twitter.com/darth_rafas)*

**primer fitxer:**


    
    <?php 
        session_start();
    ?>
    <!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd">
    <html xmlns="http://www.w3.org/1999/xhtml">
        <head>
            <meta http-equiv="Content-Type" content="text/html; charset=UTF-8"> 
            <title>Exemple de formulari</title> 
        </head> 
        <body> 
            <div style="margin: 30px 10%;">
                <form action="Ex27_1.php" method="post" id="myform" name="myform"> 
                  
                    <label>Ususari</label> 
                    <input type="text" value="" size="30" maxlength="100" name="UserName" id="" /><br /><br /> 
                    <label>Contraseña</label> 
                    <input type="password" value="" size="30" maxlength="100" name="Password" id="" /><br /><br /> 
                    <button id="mysubmit" type="submit">Entra</button><br /><br /> 
                </form>
            </div> 
        </body>
    </html>
    
**segon fitxer**    

    <?php
        session_start();
        include_once("Ex27_DADES.php");
        $uSER = $_POST['UserName'];
        $PASS = $_POST['Password'];
        $CORRECTE =  isset($_POST['UserName']) 
                  && isset($_POST['Password'])
                  && isset($usuaris[$uSER])
                  && $usuaris[$uSER] == $PASS;
    ?>
    <!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd">
    <html xmlns="http://www.w3.org/1999/xhtml">
    <head>
    <meta http-equiv="Content-Type" content="text/html; charset=UTF-8"> 
    <title>Pagina Temporal</title> 
    </head> 
    <body> 
    <div style="margin: 30px 10%;">
      <?php
        if($CORRECTE){
          $_SESSION['Usuari'] = $uSER;
      ?>
          <a href="Ex27_2.php">HOLAL </a>
      <?php
        }else{
      ?>
          <a href="Ex27.php">HOLAL </a>
      <?php
       } 
      ?>
    </div> 
    </body>
    </html>

**tercer fitxer**

    <?php
    session_start();
    if(!isset($_SESSION['Usuari'])){
      die("<a href='Ex27.php'>");
    }else{
    ?>
    <!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd">
    <html xmlns="http://www.w3.org/1999/xhtml">
    <head>
    <meta http-equiv="Content-Type" content="text/html; charset=UTF-8"> 
    <title>Exemple de formulari</title> 
    </head> 
    <body> 
    <div style="margin: 30px 10%;">
      <?php 
        echo $_SESSION['Usuari'];
      ?>
      <a href="https://www.youtube.com/watch?v=8UW7PvLYjc4&index=21&list=LL3yMpyy9ESY-Q1Faunr0z3Q"> MAGIC </a>
      
      <a href="https://www.youtube.com/watch?v=0GdzjolQzHc&list=LL3yMpyy9ESY-Q1Faunr0z3Q&index=20"> ORIGINAL </a>
    </div> 
    </body>
    </html>
    <?php
    }
    ?>    

---

#FpInfor #Daw #DawMp07 #DawMp07Uf01

* Resultats d'aprenentatge 4.d
* Continguts 4.4
---

###### Autor: daniel herrera 2013.10.07 14:47:25
###### Editat per: daniel herrera 2016.10.10 15:41:45
###### [CC BY](https://creativecommons.org/licenses/by/4.0/) ![CC BY](https://licensebuttons.net/l/by/3.0/80x15.png)
