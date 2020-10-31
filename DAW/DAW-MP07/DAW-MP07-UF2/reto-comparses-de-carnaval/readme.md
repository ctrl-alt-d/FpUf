# "RETO" comparses de carnaval
## DAW-MP07-UF2 - Exercici de Generació dinàmica de pagines web.
**Objectiu**: Confeccionar aplicació Web gestió de comparses de carnestoltes. 

### Estructura de dades:

```bash
Comparsa: número de comparsa ( PK )
          numero de persones
          disfressa (FK )
          tipus de música que l'acompanya (N:M)
          composició ( choice: Homes, Dones, Nens, Famílies )
          porta begudes alcoholiques ( booleà )
          decibels de l'equip de so
          porta instruments acústics no aplificats ( booleà )
          comentaris ( camp de text il·limitat )
```

    Disfressa: nom 
               url a amazon

    Tipus música: nom tipus ( ex: pop, country, ... )

    Peça musical: nom peça
                  artísta
                  àlbum
                  imatge
          

###Funcionalitat:

* Template base conté menú: comparses, disfresses, tipus de música, peces musicals
* Cada model té el seu propi CRUD amb aquest esquema:
    * Index: llistat de tots els elements del model. Botons al costat per: editar i esborrar. Si es clica l'ítem ens porta a pàgina *Detall*.
    * Editar: és un form confeccionat des de form factory. Permet editar o afegir.
    * Detall: Pantalla amb tota la informació de l'ítem. Botons a esborrar i editar.
    * Esborrar: Pantalla/formulari amb confirmació d'esborrar.
* S'utilitzarà sistema de 'missatgeria' per tal d'enviar notificacions a la interfície d'usuari del resultat de les accions ( ex: les dades han estat desades a la base de dades )

* Es modificaran els widgets per defecte. Per a `composició` farem servir un radio button. Per a comentaris es farà servir un `textArea`


###Divisió de la pràctica:

* En cas de fer servir django es faran dues aplicacions. Una amb comparça i disfressa i l'altre amb tipus de música i peces musicals.

###Desenvolupament de la pràctica:

La pràctica es realitza en grup de 4 o màx 5 persones. 

### S'avaluarà:

* Capacitat del grup per organitzar-se i assumir els diferents rols necessaris per a completar el projecte.
* Aplicació de les tècniques i patrons explicats a l'assignatura.

### Entregables:

* Codi font de la web autocomentat en un únic document format pdf on també s'incloguin les captures de pantalla de la web en funcionament. Cal documentar:
    * Template base
    * Documentar la integració amb bootstrap o css en general via STATIC_URL.
    * Exemple de formulari i vista de formulari.
    * Ús del patró PRG
    * Configuració i ús de fitxers d'usuari ( imatges )
    * Exemple de funcionament del framework de missatgeria ( per enviar missatges als usuaris via interface d'usuari )
* Opcional: Directe de la confecció de la web amb converses i visualització de l'evolució del codi.

###Nota per desenvolupadors django:

En aquesta pràctica fem servir fitxers. Cal tenir en compte:

Al fitxer de settings cal informar:

```python
MEDIA_ROOT = os.path.join(BASE_DIR, 'fitxers')  #allà on van a parar els fitxers
MEDIA_URL = '/media/' #carpeta virtual des d'on es serveixen ( per a composar la url )
```

Al fitxer URL's del projecte cal servir els fitxers estàtics:

```python
from django.conf.urls import url, include
from django.contrib import admin
from django.conf import settings
from django.conf.urls.static import static

    urlpatterns = (
        [
        url(r'^algunes_urls/', include('algunes_urls.urls', namespace='les_meves_urls')),
        ]  
        + static(settings.STATIC_URL, document_root=settings.STATIC_ROOT) 
        + static(settings.MEDIA_URL, document_root=settings.MEDIA_ROOT)
                   )

```
Cal assegurar-nos que als templates HTML posem l'enctype:

```html
<form method="post"  enctype="multipart/form-data">
```

Cal recollir els fitxers a les vistes ( no només els 'paràmetres' ):


```python
form = elMeuForm(request.POST,request.FILES,  ... )
```

Per mostrar les imatges des del template:

```html
<td> <img src="{{ cancion.imagen.url }}"></td>
```



---

#FpInfor #Daw #DawMp07 #DawMp07Uf02

---

###### Autor: daniel herrera 2016.01.21 10:08:25
###### Editat per: daniel herrera 2016.01.25 16:23:56
###### [CC BY](https://creativecommons.org/licenses/by/4.0/) ![CC BY](https://licensebuttons.net/l/by/3.0/80x15.png)
