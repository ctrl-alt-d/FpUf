# PHP - Patrons CRUD. No reinventem la roda!
## DAW-MP07-UF2 - Exercici de Generació dinàmica de pagines web.
Un 80% de les aplicacions clàssiques de gestió es basa en operacions CRUD.
CRUD és l'acrònim de Create (insert), Retrieve (select), Update, Delete.
No té sentit, a cada pantalla que fem, rumiar-nos com la plantejem, és per això que partirem d'uns patrons que sabem que funcionen.
Els patrons que farem servir nosaltres consistiran en:

* Menú d'opcions: ens porta a la gestió de les diferents entitats emmagatzemades a la BD ( usuaris, comandes, productes, categories, ...)
* CRUD d'una entitat:
    * Entrem en una pantalla de consulta. Incialment mostrarem totes les entitats, més endavant aprendrem a paginar i fer búsquedes. Cada entitat llistada a la pantalla té associades dues accions: Editar, Esborrar. A més, tenim l'opció Insertar.
    * Pantalla d'esborrat: Presentem les dades a esborrar i demanem confirmació.
    * Pantalla d'editar i insertar: Presentem formulari i ens enviem les dades a nosaltres mateixos.

Nota: Aquests patrons són purament acadèmics. Quan avanci l'assignatura i a les empreses, treballareu amb Frameworks que us facilitaran la feina. Ara ho fem tot a mà per conèixer els internals.


```console
//PATRÓ Generic _R__ (Retrieve)
iniciar sessió
connexió a la base de dades
si ( usuari no té suficients permisos ):
    afegir msg a la cookie
    redirecció a 'menú'
    die
mostrar enllaç a Insert
per tots els elements de la col·leció:
    mostrar element
    mostrar accions (enllaços): Edit | Delete

```


    
    //PATRÓ Generic __D (Delete)
    iniciar sessió
    connexió a la base de dades
    si ( usuari no té suficients permisos ):
        afegir msg a la cookie
        redirecció a 'resultat consulta'
        die
    llegir PK del hidden o del GET
    si valida les regles de negoci:
        esborrar
    else:
        afegir msg a la cookie
        redirecció a 'resultat consulta'
        die
    si és POST:
        esborrar element
        msg a la cookie 
        redirecció a 'resultat consulta'
        die   
    mostrar dades de l'element a esborrar
    mostrar formulari de confirmació d'esborrat
    //nota: el formulari conté hidden amb PK
    


    
    //PATRÓ Generic C_U_ (Create i Udate)
    iniciar sessió
    connexió a la base de dades
    si ( usuari no té suficients permisos ):
        afegir msg a la cookie
        redirecció a 'resultat consulta'
        die
    si es POST:
        //ens hem auto enviat dades
        si les dades no són correctes:
            afegir msg a la cookie
        else:
            aplicar canvis a la bdd
            afegir msg a la cookie
            redirecció a 'resultat consulta'
            die
    //si ha arribat aquí pot ser perquè
    //és get o perquè hi ha errors a la
    //validació del post
    obrir tags html ( $titol )
    mostrar i esborrar missatges de la cookie
    //preparar variables 'value'
    per cada camp del formulari:
       $value[camp] = 1) POST[camp] si és POST
                      2) valor a la BD si és GET
                      3) en blanc si és insert
    mostrar formulari amb els valors
    tancar tags html


**Exercicis**

Exercici 1: Fés un manteniment d'usuaris i grups tenint en compte aquests patrons.

Disposarem de dues entitats interrelacionades amb tipus de correspondència N:M, que són els usuaris i els grups.
D'aquí sorgeixen 3 taules: **Usuaris**, **Grups** i **UsuariPertanyGrup**.

Crearem les taules a la base de dades i insertarem alguns usuaris usuaris. Pots fer ajudar-te de la pràctica [PHP - Autenticació d'usuaris amb PDO - SQL Injection](/DAW/DAW-MP07/DAW-MP07-UF3/php-autenticacio-dusuaris-amb-pdo-sql-injection/readme.md) per fer aquest pas.

Caldrà que desenvolupis els següents fitxers PHP:

* **formulari_login.php**: Demanem usuari i contrasenya i ho enviem a ...
* **valida_login.php**: Rep les dades de **formulari_login.php** si són correctes ens apuntem l'usuari a $_SESSION i redirecció a 
* **menu.php**. Si no és correcta, apuntem a la cookie l'error i redirecció a **formulari_login.php**
* **consulta_usuaris.php**: utilitza el patró generic R (Retrieve)
* **edicio_o_insercio_usuari.php**: utilitza el patró generic C_U_ (Create i Udate)
* **esborrar_usuari.php**: utilitza el patró genéric __D (Delete)

Exercici 2: Comenta perquè fem el delete utilitzant POST i no GET. Et donaré una pista: els proxys existeixen.

---

#FpInfor #Daw #DawMp07 #DawMp07Uf02

* Resultats d'aprenentatge 1.b 1.c 1.d 1.e
* Continguts 1.2 1.3 1.4 1.5
---

###### Autor: daniel herrera 2013.11.02 10:18:18
###### Editat per: daniel herrera 2013.11.03 16:53:10
###### [CC BY](https://creativecommons.org/licenses/by/4.0/) ![CC BY](https://licensebuttons.net/l/by/3.0/80x15.png)
