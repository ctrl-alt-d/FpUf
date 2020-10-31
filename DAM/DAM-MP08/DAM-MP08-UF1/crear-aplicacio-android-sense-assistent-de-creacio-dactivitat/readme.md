# Crear aplicació Android sense assistent de creació d'activitat
## DAM-MP08-UF1 - Exercici de Desenvolupament d’aplicacions per dispositius mòbils
Crear aplicació Android sense assistent de creació d'activitat

Primer pas, entrar al IDE i crear nou projecte, desmarcar opció crear activity (pas1)

![Crear projecte](http://i.imgur.com/Jyn4HGI.png)

Es crearà un projecte sense cap fitxer al src (pas2)

![Carpeta src buida](http://i.imgur.com/wdmlvNs.png)

Fem botó de la dreta sobre src i nova classe. Demanem que sigui de tipus activity (pas3) L'anomenem com `ActivitatPrincipal`

![Creem activitat](http://i.imgur.com/wFhxl3O.png)

Sobreescrivim el mètode `onCreate` per cridar la classe super (pas 4):

```java
import android.os.Bundle;
...
```

    @Override
    public void onCreate( Bundle savedInstanceState ) {
        super.onCreate(savedInstanceState);
    }

Creem un layout, dins res / layout creem un nou Android xml file ( pas 5 ), triem LinearLayout, l'anomenarem `layoutprincipal`:

![Creem layout](http://i.imgur.com/OugdHr3.png)

Posem un botó i un textView dins el layout ( arrossegant els controls des de Palette ) ( pas 6 ):

![Posem botons](http://i.imgur.com/gGzQFKo.png)

Carreguem el layout dins l'activity:


```java
import com.example.appaaa.R;
...
```

    @Override
    public void onCreate( Bundle savedInstanceState ) {
        super.onCreate(savedInstanceState);
        this.setContentView( R.layout.layoutprincipal );
    }

Cal tocar el manifest per tal que inclogui aquesta activitat a l'aplicació (pas 7):

![Toquem manifest](http://i.imgur.com/AtYsqWf.png)

Ara l'últim que ens queda és posar les opcions per tal que quan s'engegui l'aplicació es cridi aquesta activitat (pas 8), ho pots fer des de l'assistent o directament a l'xml (pas 8 ):

![Toquem manifest 2](http://i.imgur.com/emRtEOK.png)

```xml
    <activity android:name="appAAA.ActivitatPrincipal">
        <intent-filter>
            <action android:name="android.intent.action.MAIN"/>
            <category android:name="android.intent.category.LAUNCHER"/>
        </intent-filter>                        
    </activity>
```

Ja podem executar l'aplicació: clic dret sobre el projecte i run as android application.







---

#FpInfor #Dam #DamMp08 #DamMp08Uf01

---

###### Autor: daniel herrera 2014.07.02 16:25:14
###### Editat per: daniel herrera 2014.07.02 16:25:12
###### [CC BY](https://creativecommons.org/licenses/by/4.0/) ![CC BY](https://licensebuttons.net/l/by/3.0/80x15.png)
