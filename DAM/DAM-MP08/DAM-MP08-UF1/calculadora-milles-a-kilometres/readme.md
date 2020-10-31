# Calculadora milles a kilometres:
## DAM-MP08-UF1 - Exercici de Desenvolupament d’aplicacions per dispositius mòbils
Per fer la calculadora partirem de l'exercici [Android responent a events.](/DAM/DAM-MP08/DAM-MP08-UF1/android-responent-a-events/readme.md) Primer hem d'aconseguir un layout com aquest:

![Layout calculadora](http://i.imgur.com/qOjMU8S.png)

Aquest seria l'xml de layout generat:

```xml
<?xml version="1.0" encoding="utf-8"?>
<LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:orientation="vertical" >

    <EditText
        android:id="@+id/editTextNumero"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:ems="10"
        android:inputType="numberDecimal" >

        <requestFocus />
    </EditText>

    <RadioGroup
        android:id="@+id/radioGroupOpcions"
        android:layout_width="match_parent"
        android:layout_height="wrap_content" >

        <RadioButton
            android:id="@+id/radio2Milles"
            android:layout_width="wrap_content"
            android:layout_height="wrap_content"
            android:checked="true"
            android:text="a milles" />

        <RadioButton
            android:id="@+id/radio2Kilometres"
            android:layout_width="wrap_content"
            android:layout_height="wrap_content"
            android:text="a kilometres" />


    </RadioGroup>

    <Button
        android:id="@+id/botoApp"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="Converteix" />

</LinearLayout>
```


Ara has de canviar el codi del programa per tal que quan punxin el botó, en comptes de simplement enviar un missatge pel log, faci els càlculs desitjats:

```java
package appAAA;

import com.example.appaaa.R;
import android.app.Activity;
import android.os.Bundle;
import android.view.View;
import android.widget.Button;
import android.widget.EditText;
import android.widget.RadioButton;

public class ActivitatPrincipal extends Activity {

	
	public ActivitatPrincipal() {
	}

	@Override
	public void onCreate( Bundle savedInstanceState ) {
		super.onCreate(savedInstanceState);
		this.setContentView( R.layout.layoutprincipal );
		
		Button button= (Button) findViewById(R.id.botoApp);
		button.setOnClickListener(new View.OnClickListener() {
		    @Override
		    public void onClick(View v) {
		    	//localitzo el control on m'escriuen el número a convertir:
		    	EditText editTextNumeroEditText = (EditText) findViewById( R.id.editTextNumero) ;
		    	//obtinc el valor (text) que l'usuari ha entrat en aquell botó
		    	String  editTextNumeroString = editTextNumeroEditText.getText().toString();
		    	//converteixo el text a float
		    	float editTextNumero = Float.valueOf(editTextNumeroString);
		    	//Localitzo el radio que em diu si passem a milles
		    	RadioButton passarAMillesRadioButton = ( RadioButton) findViewById( R.id.radio2Milles ) ;
		    	//calculo si passem de milles a kilòmetres
		    	boolean passarAMilles = passarAMillesRadioButton.isChecked(); 
		    	//fem els càlculs
		    	String resultat = Float.toString( editTextNumero * ( passarAMilles? 1.6f : (1.0f/1.6f) ) ); 
		    	//els presentem al mateix lloc on ens els han entrat
		    	editTextNumeroEditText.setText( resultat ); 
		        
		    }
		});
		
	}
}

```

Nota: aquest codi no és gaire net perquè els strings haurien de ser a strings, això ho arreglarem a la propera pràctica.








---

#FpInfor #Dam #DamMp08 #DamMp08Uf01

---

###### Autor: daniel herrera 2014.07.02 17:36:05
###### Editat per: daniel herrera 2014.09.03 11:27:37
###### [CC BY](https://creativecommons.org/licenses/by/4.0/) ![CC BY](https://licensebuttons.net/l/by/3.0/80x15.png)
