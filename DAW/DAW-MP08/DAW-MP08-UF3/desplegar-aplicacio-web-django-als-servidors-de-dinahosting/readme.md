# Desplegar aplicació Web django als servidors de dinahosting
## DAW-MP08-UF3 - Exercici de Desplegament d’aplicacions web.
Aquest és el procediment a data 2017 per desplegar una aplicació web a dinahosting:

1) Cal assegurar-se que disposem d'un hosting que suporta python. Ves a **hosting**, **storm** i migra a un servidor python, NodeJS, ...

2) Assegura't que tens un usuari per entrar per **ssh**. I conectat-hi.

3) Crea un entorn virtual:  `virtualenv venv`

4) Activa l'entorn virtual, això ho hauràs de fer cada cop que et connectis: `sourve venv/bin/activate`

5) Un cop activat, instal·la la versió de **django** amb la que vulguis treballar. `pip install django` i les llibreries que necessitis.

6) Crea un projecte de proves: `cd ~; django-admin elmeuprojecte`

7) Congigura el `wsgi` per executar l'aplicació:

```bash
(venv)elmeuhosting@h0000:~$ cat elmeuprojecte/elmeuprojecte.wsgi

import os
import sys
import site

# Add the site-packages of the chosen virtualenv to work with
site.addsitedir('/home/elmeuhosting/venv/lib/python2.7/site-packages')

INTERP = os.path.expanduser("~/venv/bin/python")

if sys.executable != INTERP: os.execl(INTERP, INTERP, *sys.argv)

sys.path.insert(0,'$HOME/venv/bin')
sys.path.insert(0,'$HOME/venv/lib/python2.7/site-packages/django')
sys.path.insert(0,'$HOME/venv/lib/python2.7/site-packages')

# Add the app's directory to the PYTHONPATH
sys.path.append('/home/elmeuhosting/elmeuprojecte')

os.environ['DJANGO_SETTINGS_MODULE'] = 'elmeuprojecte.settings'

# Activate your virtual env
activate_env=os.path.expanduser("/home/elmeuhosting/venv/bin/activate_this.py")
execfile(activate_env, dict(__file__=activate_env))

from django.core.wsgi import get_wsgi_application
application = get_wsgi_application()

```

8) Configura els fitxer .htaccess de l'arrel: 

```bash
(venv)elmeuhosting@h0000:~$ cat ~/.htaccess
```


    ##
    ## DHGENERATED
    ## NO EDITAR MANUALMENTE!!!!
    ##
    AddHandler mod_python .py
    PythonHandler mod_python.publisher
    PythonDebug On
    Options +ExecCGI
    AddHandler wsgi-script .wsgi
    
    
    RewriteEngine On
    ##REGLAS_NODE##
    
    ##FIN_REGLAS_NODE##
    
9) Configura l'.htaccess de la carpeta www:

```bash
(venv)elmeuhosting@h0000:~$ cat ~/www/.htaccess 
```

    RewriteEngine off
    PassengerEnabled on
    PassengerBaseURI /
    PassengerAppRoot /home/elmeuhosting/elmeuprojecte
    PassengerAppType wsgi
    PassengerStartupFile /home/elmeuhosting/elmeuprojecte/elmeuprojecte.wsgi
    
10) Connectat amb el navegador al teu domini. Hauria d'estar funcionant.

![Imgur](http://i.imgur.com/kqNvYMA.png)

---

#FpInfor #Daw #DawMp08 #DawMp08Uf03

---

###### Autor: daniel herrera 2017.02.20 14:04:14
###### Editat per: daniel herrera 2017.02.20 14:04:14
###### [CC BY](https://creativecommons.org/licenses/by/4.0/) ![CC BY](https://licensebuttons.net/l/by/3.0/80x15.png)
