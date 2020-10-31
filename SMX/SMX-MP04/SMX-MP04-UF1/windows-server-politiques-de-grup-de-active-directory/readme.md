# Windows Server - Polítiques de grup de Active Directory
## SMX-MP04-UF1 - Exercici de sistemes operatius propietaris en xarxa.
#Activitat 5 Polítiques de grup de Active Directory

![Active Directory](https://seicoll.gitbooks.io/sox/content/assets/ActiveDirectory.png)

## Activitat

### 1. Creació de polítiques de grup globals

Estableix les directives de grup globals (Default Domain Policy) que s'indiquen a continuació a tots els equips i usuaris del domini.

Comprova el correcte funcionament i adjunta captures de pantalla.

1. El usuaris puguin canviar l’hora del sistema 
*(Configuración del equipo > Configuración de Windows > Configuración de seguridad > Directivas locales > Asignación de derechos de usuarios > Cambiar la hora del sistema) *

2. Tinguin l’accés restringit a la unitat C:/ del seu equip.
*(Configuración del usuario > Directivas > Plantillas > Componentes de Windows > Explorador de archivos > Ocultar estas unidades específicas en MiPC)*

3. Tots els usuaris tinguin el mateix fondo de pantalla.

### 2. Creació de polítiques de grup a Professors

4. Només els usuaris que tenen delegat el control de la OU poden modificar l'hora i data.

5. Treure l'administrador de tasques.

6. Ocultar la Unitat c:

7. Denegar accés de lectura/escriptura a medis extraibles.

8. Que els usuaris no puguin modificar el temps que triga a saltar el protector de pantalla.

### 3. Creació de polítiques de grup a Alumnes

9. Crea un GPO per a la **UO Alumnes**. per tal que la barra de tasques quedi bloquejada.

10. No puguin anar al panell de control.
*(Configuracion del usuario > Directivas > Plantillas > Panel de Control)*

11. No puguin canviar el fons d'escriptori.
*(Configuracion del usuario > Directivas > Plantillas > Panel de Control>Personalizacion)*

12. Que s'iniciï automàticament la calculadora cada cop que un usuari de alumnes comenci una nova sessió.

13. Que no puguin obrir el paint.

14. Que no puguin modificar el registre de Windows.

### 4. Creació de polítiques de grup a Direcció

15. Modificar la pàgina d'inici del navegador per [www.infobosccoma.net](http://www.infobosccoma.net)

16. No es permetrà el canvi de proxy.

17. Que no puguin accedir a l'administrador de tasques mitjançant la combinació "CTR+ALT+SUPR"

18. Limitar la mida de la paperera de reciclatge a 200Mb.

19. Que no els hi permeti contrasenyes de menys de 10 caràcters.

### 5. Ordre d’aplicació GPOs

20. Crea primer una GPO a les directives de configuració d'equip i després fes-ne una a les directives de configuració d'usuari que contradigui la primera. Quina preval? Com ho has provat?

### 6. (Ampliació) GPOs d’instal·lació de programari

21. Crea una GPO que **instal·li el paquet PDFCreator automàticament de forma assignada** a tots els equips d’una OU.
Pots ajudar-te del següent enllaç:
  [http://ebarrova.blogspot.com.es/2014/02/instalar-impresora-mediante-gpos.html](http://ebarrova.blogspot.com.es/2014/02/instalar-impresora-mediante-gpos.html)

  Elimineu el paquet i comproveu com es desinstal·la del client.

22. Crea una GPO que **instal·li el Chrome automàticament de forma publicada ** a tots els equips d'una OU.
Documenteu la instal·lació del paquet des del Tauler de Control.

---

#FpInfor #Smx #SmxMp04 #SmxMp04Uf01

---

###### Autor: Sergi Coll 2017.06.05 17:10:15
###### Editat per: Sergi Coll 2017.06.05 17:10:15
###### [CC BY](https://creativecommons.org/licenses/by/4.0/) ![CC BY](https://licensebuttons.net/l/by/3.0/80x15.png)
