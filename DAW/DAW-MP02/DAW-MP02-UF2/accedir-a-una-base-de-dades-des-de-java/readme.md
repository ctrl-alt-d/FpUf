# Accedir a una base de dades des de java
## DAW-MP02-UF2 - Exercici de Llenguatges SQL: DML i DDL
1) Instal·la un SGBD per exemple MySQL:

```bash
sudo apt-get install mysql-server mysql-client
```

Instal·la també el driver MySQL per a Java:

```bash
sudo apt-get install libmysql-java
export CLASSPATH=$CLASSPATH:/usr/share/java/mysql-connector-java.jar

```
2) Crea un usuari i una base de dades, dona permisos sobre la base de dades a l'usuari. 



```bash
mysql -u root -p

mysql> create database elPenjat
    -> ;
Query OK, 1 row affected (0.00 sec)

mysql> create user penjat identified by "i";
Query OK, 0 rows affected (0.00 sec)

mysql> grant all privileges on elPenjat.* to penjat;
Query OK, 0 rows affected (0.00 sec)
```


A partir d'ara sempre et connectaràs amb aquest usuari `penjat`. 

3) Crea una estructura de taules, pots fer servir les taules de l'exercici ['el Penjat'](/DAW/DAW-MP02/DAW-MP02-UF2/el-penjat-cdm-ldm-selects-ddl/readme.md)


```bash
dani@dbteacher:~/tmp/73737373$ mysql -u penjat -p
Enter password: 
Welcome to the MySQL monitor.  Commands end with ; or \g.
Your MySQL connection id is 48
Server version: 5.5.54-0ubuntu0.12.04.1 (Ubuntu)

Copyright (c) 2000, 2016, Oracle and/or its affiliates. All rights reserved.

Oracle is a registered trademark of Oracle Corporation and/or its
affiliates. Other names may be trademarks of their respective
owners.

Type 'help;' or '\h' for help. Type '\c' to clear the current input statement.

mysql> use elPenjat;
Database changed
mysql> create table partides ( 
            id_estat int, jugador varchar(100), paraula varchar(100) );
Query OK, 0 rows affected (0.20 sec)

mysql> insert into partides values ( 1, 'Dani', 'Hola' );
Query OK, 1 row affected (0.05 sec)

mysql> insert into partides values ( 1, 'Dani', 'Adeu' );
Query OK, 1 row affected (0.06 sec)
```

4) Escriu un programa que faci una consulta sobre la base de dades. Exemple:

```java
//STEP 1. Import required packages
import java.sql.*;

public class PenjatDB {
   // JDBC driver name and database URL
   static final String JDBC_DRIVER = "com.mysql.jdbc.Driver";
   static final String DB_URL = "jdbc:mysql://localhost/elPenjat";

   //  Database credentials
   static final String USER = "penjat";
   static final String PASS = "i";

   public static void main(String[] args) {
   Connection conn = null;
   Statement stmt = null;
   try{
      //STEP 2: Register JDBC driver
      Class.forName("com.mysql.jdbc.Driver");

      //STEP 3: Open a connection
      System.out.println("Connecting to database...");
      conn = DriverManager.getConnection(DB_URL,USER,PASS);

      //STEP 4: Execute a query
      System.out.println("Creating statement...");
      stmt = conn.createStatement();
      String sql;
      sql = "SELECT jugador, id_estat, paraula FROM partides";
      ResultSet rs = stmt.executeQuery(sql);

      //STEP 5: Extract data from result set
      while(rs.next()){
         //Retrieve by column name
         int id_estat  = rs.getInt("id_estat");
         String jugador = rs.getString("jugador");
         String paraula = rs.getString("paraula");

         //Display values
         System.out.print("id_estat: " + id_estat);
         System.out.print(", jugador: " + jugador);
         System.out.println(", paraula: " + paraula);
      }
      //STEP 6: Clean-up environment
      rs.close();
      stmt.close();
      conn.close();
   }catch(SQLException se){
      //Handle errors for JDBC
      se.printStackTrace();
   }catch(Exception e){
      //Handle errors for Class.forName
      e.printStackTrace();
   }finally{
      //finally block used to close resources
      try{
         if(stmt!=null)
            stmt.close();
      }catch(SQLException se2){
      }// nothing we can do
      try{
         if(conn!=null)
            conn.close();
      }catch(SQLException se){
         se.printStackTrace();
      }//end finally try
   }//end try
   System.out.println("Goodbye!");
}//end main
}//end 
```


5) Ja pots compilar i provar el programa:

```bash
dani@dbteacher:~/tmp/73737373$ javac PenjatDB.java
dani@dbteacher:~/tmp/73737373$ java PenjatDB 
Connecting to database...
Creating statement...
id_estat: 1, jugador: Dani, paraula: Hola
id_estat: 1, jugador: Dani, paraula: Adeu
Goodbye!
dani@dbteacher:~/tmp/73737373$ 
```

6) Modifica el programa per tal que permeti entrar noves paraules.

7) Modifica el programa per tal que et permeti jugar.

Exemple de com insertar dades:

```java
String sql = "INSERT INTO paraules (paraula)" +
             "VALUES (?)";

PreparedStatement preparedStatement = conn.prepareStatement(sql);
preparedStatement.setString(1, "Forani");
preparedStatement.executeUpdate();
```

---

#FpInfor #Daw #Dam #Asix #AsixMp02 #DawMp02 #DamMp02 #DawMp02Uf02 #AsixMp02Uf02 #DamMp02Uf02

---

###### Autor: daniel herrera 2017.02.16 16:28:40
###### Editat per: daniel herrera 2017.02.20 18:17:40
###### [CC BY](https://creativecommons.org/licenses/by/4.0/) ![CC BY](https://licensebuttons.net/l/by/3.0/80x15.png)
