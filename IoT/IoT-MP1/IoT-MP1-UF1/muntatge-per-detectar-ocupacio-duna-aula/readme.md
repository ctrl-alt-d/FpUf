# Muntatge per detectar ocupació d'una aula
## IoT-MP1-UF1 - Exercici de Arduino i els seus amics
Es tracta de fer un dispositiu que detecti si una aula està buida o ocupada i envii aquesta informació a un servidor. Amb les dades del servidor podrem fer estadístiques d'ocupació d'aquella aula.

**Material**

1. Farem servir un arduino o similar ( ESP8266 )
2. Pensarem quin sensor dels que disposem ens ajuda a determinar si hi ha ocupació a l'aula.
3. Usarem un led com a xivato quan detecti ocupació.
4. En franges de 10 minuts detectarem ocupació o no `delay(10 * 60 * 1000)`;.
5. En franges de 10 minuts enviarem informació al servidor indicant si hi ha hagut ocupació.

**Programació**

1. Utilitzarem les [interrupcions](https://www.arduino.cc/en/Reference/AttachInterrupt) amb el sensor que fem servir per detectar ocupació de l'aula.

**Servidor**

1. Podem fer servir [keen.io](http://keen.io) per a recollir els events si som valents enviat un [POST](https://techtutorialsx.com/2016/07/21/esp8266-post-requests/)
2. Podem fer servir [thinger](http://docs.thinger.io/arduino/#overview) que disposem de llibreries que ens faciliten la vida.

---

#FpInfor #Iot #IotMp01 #IotMp01Uf01

---

###### Autor: daniel herrera 2017.05.29 14:51:38
###### Editat per: daniel herrera 2017.05.29 15:21:26
###### [CC BY](https://creativecommons.org/licenses/by/4.0/) ![CC BY](https://licensebuttons.net/l/by/3.0/80x15.png)
