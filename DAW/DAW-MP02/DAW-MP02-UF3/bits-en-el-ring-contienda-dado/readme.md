# Bits en el ring. Contienda. Dado.
## DAW-MP02-UF3 - Exercici de Llenguatges SQL: DCL i extensió procedimental
El joc està basat en [Ignotum](http://bitsenelring.blogspot.com.es/2013/08/nueva-competencia-ignotum.html) consiteix en el següent:

* Es juga per torns.
* Es llença un dau.
* El jugador que té el torn decideix si:
    * S'anota els punts i perd el torn.
    * S'anota els punts el rival i no perd el torn.
* No sé sap quantes vegades es llençarà el dau.
* Quan s'acaba la partida guanya qui ha acumulat més punts.

Els punts es guararan en aquesta taula:

    marcador ( tirada int pk, nJugadorAnota, puntsAnotats )

Es tracta de fer la funció `mElsQuedo`  que prengui la decissió si es queda els punts i perd el torn o no se'ls queda i perd el torn.

La funció té aquesta signatura:

```sql
create function dbo.mElsQuedo( nJugador int, punts int ) returns bit
```

* La funció l'ha de desenvolupar l'alumne.
* La funció tindrà una estratègia per decidir si es queda els punts ( retorna 1 ) o no ( retorna 0 )
* La funció té accés lectura a la taula `marcador`.
* La funció s'ha descriure de manera neta i llegible. Ben indentada.
* Agafarem totes les funcions i les farem compatir entre elles.

Aquest és el codi que fa competir funcions:

```sql
declare @n int;
set @n = 10000;

drop table if exists Marcador;
create table Marcador (
tirada int not null identity,
nJugadorAnota int,
puntsAnotats int
)

while @n > 0 BEGIN
	declare @dau int;
	declare @selqueda bit;
    set @selqueda = 0;
    while (@selqueda = 0 and @n > 0 ) begin
	    set @dau = (cast(rand()*10000 as int) % 6 ) + 1;
        set @selqueda = dbo.f1( 1, @dau );
        insert into Marcador (nJugadorAnota, puntsAnotats)
               values (1, @dau );
        set @n = @n - 1;
        print 'Jugador 1: ' + str(@dau) + ' s''el queda ' + str(@selqueda)
    end
    set @selqueda = 0;
    while ( @selqueda = 0 and @n > 0 ) begin
	    set @dau = (cast(rand()*10000 as int) % 6 ) + 1;
        set @selqueda = dbo.f2( 2, @dau );
        insert into Marcador (nJugadorAnota, puntsAnotats)
               values (2, @dau );
        set @n = @n - 1;
        print 'Jugador 2: ' + str(@dau) + ' s''el queda ' + str(@selqueda)
    end
END

--resultats
select nJugadorAnota, sum(puntsAnotats)
from marcador
group by nJugadorAnota
order by nJugadorAnota;
```

---

#FpInfor #Daw #Dam #Asix #AsixMp02 #DawMp02 #DamMp02 #DamMp02Uf03 #DawMp02Uf03 #AsixMp02Uf03

---

###### Autor: daniel herrera 2018.04.27 15:42:33
###### Editat per: daniel herrera 2018.05.04 17:54:22
###### [CC BY](https://creativecommons.org/licenses/by/4.0/) ![CC BY](https://licensebuttons.net/l/by/3.0/80x15.png)
