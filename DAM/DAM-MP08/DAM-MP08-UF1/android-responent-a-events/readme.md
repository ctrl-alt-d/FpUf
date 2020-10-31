# Android responent a events.
## DAM-MP08-UF1 - Exercici de Desenvolupament d’aplicacions per dispositius mòbils
En aquesta pràctica el que farem serà respondre a un event clic del botó creat a la pràctica [Crear aplicació Android sense assistent de creació d'activitat](/DAM/DAM-MP08/DAM-MP08-UF1/crear-aplicacio-android-sense-assistent-de-creacio-dactivitat/readme.md)

Primer li posarem un mom reiconeixible al nostre botó (pas 1):

![Canvi nom el botó](http://i.imgur.com/cwQE3Jv.png)

Ara anirem a l'act...ivitat principal i li assignarem un listener al botó:


```java
...
import android.util.Log;
import android.view.View;
import android.widget.Button;

public class ActivitatPrincipal extends Activity {

	public ActivitatPrincipal() {
	}

	@Override
	public void onCreate( Bundle savedInstanceState ) {
		super.onCreate(savedInstanceState);
		this.setContentView( R.layout.layoutprincipal );
		
		//localitzem el botó:
		Button button= (Button) findViewById(R.id.botoApp);
		//li assignem un listener
		button.setOnClickListener(new View.OnClickListener() {
		    @Override
		    public void onClick(View v) {
			//Enviem a LogCat: tag i misssatge
		        Log.i("principal","Clicat!!!");
		    }
		});		
	}
}
```

Com es pot veure, un listener és un objecte que implementi onClickListener, al nostre cas una View però podria ser un Button o la propia activitat si li fem implementar la interface. 

Al logCat ens apareixen moltíssima informació, el millor és filtrar per tag:

![Filtrar per tag](http://i.imgur.com/shzP2at.png)

Ara cada cop que piquem el botó a l'aplicació ens ha d'apareixer el missatge:

![Missatge al clicar botó](http://i.imgur.com/6foZ2mW.png)

En aquesta pràctica hem aprés a respondre a un event de la vista i a fer servir el LogCat. 

Busca que és el Log.e, Log.w, Log.i, Log.v, Log.d i el Log.wtf








---

#FpInfor #Dam #DamMp08 #DamMp08Uf01

---

###### Autor: daniel herrera 2014.07.02 16:47:30
###### Editat per: daniel herrera 2014.07.02 16:47:27
###### [CC BY](https://creativecommons.org/licenses/by/4.0/) ![CC BY](https://licensebuttons.net/l/by/3.0/80x15.png)
