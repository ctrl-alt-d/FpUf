# Oracle Objecte-Relacional - Juràsic GATTACA
## DAW-MP02-UF4 - Exercici de Bases de dades objectes-relacionals
A la película 'Parc Juràsic' apareix un informàtic orgullós de poder emmagatzemar la informació de les secuències d'ADN dels diferents dinosàures en una base de dades:


```bash
>DinoDNA  "Dinosaur DNA" from Crichton JURASSIC PARK  p. 103 nt 1-1200
GCGTTGCTGGCGTTTTTCCATAGGCTCCGCCCCCCTGACGAGCATCACAAAAATCGACGC
GGTGGCGAAACCCGACAGGACTATAAAGATACCAGGCGTTTCCCCCTGGAAGCTCCCTCG
TGTTCCGACCCTGCCGCTTACCGGATACCTGTCCGCCTTTCTCCCTTCGGGAAGCGTGGC
TGCTCACGCTGTACCTATCTCAGTTCGGTGTAGGTCGTTCGCTCCAAGCTGGGCTGTGTG
CCGTTCAGCCCGACCGCTGCGCCTTATCCGGTAACTATCGTCTTGAGTCCAACCCGGTAA
AGTAGGACAGGTGCCGGCAGCGCTCTGGGTCATTTTCGGCGAGGACCGCTTTCGCTGGAG
ATCGGCCTGTCGCTTGCGGTATTCGGAATCTTGCACGCCCTCGCTCAAGCCTTCGTCACT
CCAAACGTTTCGGCGAGAAGCAGGCCATTATCGCCGGCATGGCGGCCGACGCGCTGGGCT
GGCGTTCGCGACGCGAGGCTGGATGGCCTTCCCCATTATGATTCTTCTCGCTTCCGGCGG
CCCGCGTTGCAGGCCATGCTGTCCAGGCAGGTAGATGACGACCATCAGGGACAGCTTCAA
CGGCTCTTACCAGCCTAACTTCGATCACTGGACCGCTGATCGTCACGGCGATTTATGCCG
CACATGGACGCGTTGCTGGCGTTTTTCCATAGGCTCCGCCCCCCTGACGAGCATCACAAA
CAAGTCAGAGGTGGCGAAACCCGACAGGACTATAAAGATACCAGGCGTTTCCCCCTGGAA
GCGCTCTCCTGTTCCGACCCTGCCGCTTACCGGATACCTGTCCGCCTTTCTCCCTTCGGG
CTTTCTCAATGCTCACGCTGTAGGTATCTCAGTTCGGTGTAGGTCGTTCGCTCCAAGCTG
ACGAACCCCCCGTTCAGCCCGACCGCTGCGCCTTATCCGGTAACTATCGTCTTGAGTCCA
ACACGACTTAACGGGTTGGCATGGATTGTAGGCGCCGCCCTATACCTTGTCTGCCTCCCC
GCGGTGCATGGAGCCGGGCCACCTCGACCTGAATGGAAGCCGGCGGCACCTCGCTAACGG
CCAAGAATTGGAGCCAATCAATTCTTGCGGAGAACTGTGAATGCGCAAACCAACCCTTGG
CCATCGCGTCCGCCATCTCCAGCAGCCGCACGCGGCGCATCTCGGGCAGCGTTGGGTCCT

```

Com pots observar, per emmagatzemar la sequència, el que tenim és un seguit de lletres corresponents a les bàses nitrogenades (AGCT)

**Primera part**: Prepara una tipus objecte (dinosaure_typ) per emmagatzemar el genoma d'un dinosàure, contindrà el nom del dinosàure ( varchar2(250) ) i la seqûència de bases nitrogenades. ( Cal crear genoma_typ com a col·lecció de BaseNitrogenadaSeq_typ, que és un Numeric(10), char(1) )

Crea la taula d'objectes dinosaure i inserta al menys l'ADN (el genoma) d'un dinosaure a la taula, només cal que insertis 8 àcids nuclèics (bases nitrogenades).

*Resum:*

* `BaseNitrogenadaSeq_typ` ens informa de quina base nitrogenada hi ha a una posició determinada de la seqüència d'ADN. Ex:  A la posició '3' hi ha la base nitrogenada.
* `genoma_typ` és una estructura col·lecció d'objectes `BaseNitrogenadaSeq_typ`.
* `dinosaure_typ` és una estructura (tipus objecte) que conté el nom del dinosaure i el seu genoma enmmagatzemant en un `genoma_typ`.
* `dinosaures` és una taula d'objectes `dinosaure_typ`.

**Segona part**: Gattaca és una pel·lícula de ciència-ficció de 1997. La pel·lícula presenta una visió pròpia d'una distopia d'un món on és possible la selecció genètica extrema, de manera que els fills es veuen lliures de tares i malalties hereditàries. Això ocasiona que només els seleccionats puguin optar a determinats treballs. La película rep el nom de les bases nitrogenades de l'ADN.

Modifica l'exercici anterior i crea un mètode a dinosaure_typ que comprovi si aquell dinosaure conté la seqüencia GATTACA ( GTTC ). No cal que sigui eficient, pot recorrer tota la col·lecció.

Seleccionana tots els dinosaures tot mostrant si són dinosaures GATTACA.

*Resum:*

* Cal afegir el mètode `esGATTACA` al tipus objecte `dinosaure_typ`. Aquest mètode ens dirà si la propietat genoma de l'objecte conté la seqüència GTTC de bases nitrogenades.
* Cal fer una select on s'invoqui aquest mètode per a cada dinosaure de la taula.

**Solució**:

Creació dels tipus objecte:

```SQL    
create type genomaBase_typ as object (
   numero_a_la_sequencia numeric( 13 ),
   base_nitrogenada char(1) 
);
/
create type genoma_typ as table of genomaBase_typ;
/
create type dinosaure_typ as OBJECT (
    nom varchar(250 ),
    genoma genoma_typ
);
```

Creació de la taula d'objectes dinosaure i inserció de dades:

```SQL
/
create table dinosaures of dinosaure_typ nested table genoma store as genoma_nt;
/
insert into dinosaures values
( new dinosaure_typ( 'Rex', 
                     genoma_typ( genomaBase_typ( 1, 'G' ), 
                                 genomaBase_typ( 2, 'T' ), 
                                 genomaBase_typ( 3, 'T' ), 
                                 genomaBase_typ( 4, 'C' ), 
                                 genomaBase_typ( 5, 'C' ), 
                                 genomaBase_typ( 6, 'A' ), 
                                 genomaBase_typ( 7, 'A' ), 
                                 genomaBase_typ( 8, 'A' ) 
                     ) 
  ) 
);
/
insert into dinosaures values
( new dinosaure_typ( 'Velociraptor', 
                     genoma_typ( genomaBase_typ( 1, 'A' ), 
                                 genomaBase_typ( 2, 'T' ), 
                                 genomaBase_typ( 3, 'C' ), 
                                 genomaBase_typ( 4, 'C' ), 
                                 genomaBase_typ( 5, 'C' ), 
                                 genomaBase_typ( 6, 'A' ), 
                                 genomaBase_typ( 7, 'A' ), 
                                 genomaBase_typ( 8, 'A' ) 
                     ) 
  ) 
);
```


Creació del mètode `esGATTACA`:

```SQL
alter type dinosaure_typ add member function esGATTACA return number cascade;
/
create or replace type body dinosaure_typ as 
member function esGATTACA  return number is
 begin
  for i in 4..self.genoma.COUNT LOOP
     if (genoma(i-3).base_nitrogenada = 'G' and 
         genoma(i-2).base_nitrogenada = 'T' and 
         genoma(i-1).base_nitrogenada = 'T' and 
         genoma(i-0).base_nitrogenada = 'C' ) then
      return 1;
     end if;     
  end loop;
 return 0;
 end;
end;
/
```

Selecció dels dinosàures i execució del mètode:
    
```SQL
select s.nom, s.esGATTACA() from dinosaures s;
/

```
Alternativa més eficient a recòrrer tota la taula, per a millorar l'eficiència, però, cal crear els indexos corresponents:
    
```SQL
create or replace type body dinosaure_typ as 
member function esGATTACA  return number is
 n numeric(1);
 begin
  select min( T1.numero_a_la_sequencia ) into n
  from 
       table( genoma  ) T1 
  inner join 
       table( genoma  ) T2 on 
              T1.numero_a_la_sequencia + 1 = T2.numero_a_la_sequencia
  inner join 
       table( genoma  ) T3 on 
              T2.numero_a_la_sequencia + 1 = T3.numero_a_la_sequencia 
  inner join 
       table( genoma  ) T4 on 
              T3.numero_a_la_sequencia + 1 = T4.numero_a_la_sequencia 
  where T1.base_nitrogenada = 'G' and 
        T2.base_nitrogenada = 'T' and
        T3.base_nitrogenada = 'T' and
        T4.base_nitrogenada = 'C' 
  ;
  return n;
 end;
end;
/
```

---

#FpInfor #Daw #DawMp02 #DawMp02Uf04

---

###### Autor: daniel herrera 2014.05.07 14:00:45
###### Editat per: daniel herrera 2014.05.11 10:02:12
###### [CC BY](https://creativecommons.org/licenses/by/4.0/) ![CC BY](https://licensebuttons.net/l/by/3.0/80x15.png)
