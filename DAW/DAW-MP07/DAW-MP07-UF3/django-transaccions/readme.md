# django - Transaccions
## DAW-MP07-UF3 - Exercici de Tècniques d’accés a dades.
Llegint la documentació [Database transactions](https://docs.djangoproject.com/en/dev/topics/db/transactions/) de django podràs contestar aquestes preguntes:

1. Quin és el comportament per defecte de django respecte les transaccions?
1. Quina seria una manera habitual de manegar les transaccions a la web? Com s'activa aquest comportament a django?
1. Si activem el comportament de transacció x request, com podem deshabilitar-lo per a una vista concreta?
1. Quin és el comportament del següent tall de codi?

Codi:

```python
from django.db import transaction
```

    def viewfunc(request):
        # This code executes in autocommit mode (Django's default).
        do_stuff1()
    
        with transaction.atomic():
            # This code executes inside a transaction.
            do_stuff2()
 
            # Undoing
            transaction.rollback()
    

---

#FpInfor #Daw #DawMp07 #DawMp07Uf03

* Resultats d'aprenentatge 1.g
* Continguts 1.7
---

###### Autor: daniel herrera 2013.11.20 14:32:23
###### Editat per: daniel herrera 2013.11.20 14:32:18
###### [CC BY](https://creativecommons.org/licenses/by/4.0/) ![CC BY](https://licensebuttons.net/l/by/3.0/80x15.png)
