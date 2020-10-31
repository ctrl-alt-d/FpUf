# Desnormalització
## DAW-MP02-UF1 - Exercici de Introducció a les bases de dades
La desnormalització consisteix en trecar voluntàriament alguna de les regles de normalització a favor d'un increment en el rendiment de la base de dades.

Desnormalitzar és una decisió molt perillosa perquè estem hipotecant el creixement natural de la base de dades així com la coherència i integritat de les dades. Tanmateix hi ha escenaris on treballar sense desnormalitzar és molt costos per a la base de dades. Posarem dos exemples:

1) **Materialitzar agregacions**. Suposem una base de dades que registre les entrades i sortides de material del magatzem tal com aquest:

```bash
Productes
codi  Nom
   1  Kuda
   2  Weevil
   3  Vesper
```

    Moviments Estoc
         moment  producte qtat
     1/1/1 9:15         1   50
     1/1/1 9:16         2  150
     1/1/1 9:21         1  -30
     1/1/1 9:37         1  -20


Per conèixer l'estoc actual d'un producte ens caldria fer una suma de les entrades de producte - sortides de producte des de l'inici dels temps, això poden ser milers i milers de fileres. Al nostre exemple l'estoc actual de Kuda seria 0 i el de Weevil seria 150.

Un exemple de desnormalització seria afegir aquest camp calculat a producte. D'aquesta manera no caldria fer cap operació per conèixer estoc:

```bash
Productes
codi  Nom     estoc actual
   1  Kuda               0
   2  Weevil           150
   3  Vesper             0
```

    Moviments Estoc
         moment  producte qtat
     1/1/1 9:15         1   50
     1/1/1 9:16         2  150
     1/1/1 9:21         1  -30
     1/1/1 9:37         1  -20

Com es pot apreciar aquí hi ha una redundàcia de dades. Llavors cal assegurar que totes les aplicacions que toquen la base de dades mantindran aquesta coherència i s'enrecordaran d'actualitzar la taula productes després de fer moviments d'estoc. Existeixen altres mecanismes, dins la mateixa base de dades, per evitar que siguin les aplicacions qui mantinguin aquest agregat: triggers, procediments emmagatzemants, vistes materialitzades. S'estudiaran més endavant.

2) **Claus subrogades**. Per millorar l'eficiència del sistema a cada tupla se li assigna un identificador únic que serveix de clau primària. LLavors les claus primàries són uns identificadors artificials (normalment claus autonomèriques o bé UUIDs per a bases de dades distribuides ). Llavors passem de treballar amb *claus naturals* o *claus de negoci* a treballar amb *claus subrogades*. És especialment útil a les taules que provenen d'entitats febles on hi ha molta propagació de claus que acaben formant part de la clau primària.

**Exercicis**

1) Posa dos exemples de desnormalització.

2) Fes una ullada a [Surrogate vs. natural/business keys](http://stackoverflow.com/questions/63090/surrogate-vs-natural-business-keys) i contesta: quin tipus de clau recomanen a stackoverflow?

3) Fes una ullada a [Lookup Table — Natural or Surrogate key as primary key?](http://stackoverflow.com/questions/34372118/lookup-table-natural-or-surrogate-key-as-primary-key). Dibuixa el diagrama ER de la base de dades que allà es presenta. Digues quins arguments presenten els usuaris a favor (o en contra) de treballar amb claus subrogades.

4) Fes una ullada a [Relational database design question - Surrogate-key or Natural-key?](http://stackoverflow.com/questions/3747730/relational-database-design-question-surrogate-key-or-natural-key). Passa diagrama ER a relacional ( notació SQL ). Digues quins arguments presenten els usuaris a favor (o en contra) de treballar amb claus subrogades.

5)  Fes una ullada a [Database development mistakes made by application developers](http://stackoverflow.com/questions/621884/database-development-mistakes-made-by-application-developers) Identifica quines bones pràctiques tenen a veure amb la normalització i extreu les idees més importants.




>
>######Aquest exercici està extret del llibre [d'exercicis Introducció a les Bases de Dades. UF1 MP2 DAM DAW ASIX](https://www.amazon.es/Introducci%C3%B3-Bases-Dades-asix-MP02-UF1/dp/153735096X) amb permís del seu autor. 
>



---

#FpInfor #Daw #Dam #Asix #AsixMp02 #DawMp02 #DamMp02 #DawMp02Uf01 #AsixMp02Uf01 #DamMp02Uf01

---

###### Autor: daniel herrera 2016.08.28 10:24:40
###### Editat per: daniel herrera 2016.08.30 16:58:47
###### [CC BY](https://creativecommons.org/licenses/by/4.0/) ![CC BY](https://licensebuttons.net/l/by/3.0/80x15.png)
