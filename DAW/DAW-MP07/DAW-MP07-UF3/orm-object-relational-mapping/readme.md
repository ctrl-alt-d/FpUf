# ORM - Object relational mapping
## DAW-MP07-UF3 - Exercici de Tècniques d’accés a dades.
Object relational mapping és una tècnica que serveix per encapsular en objectes les entitats que persistim a la base de dades com a taules.

Aquests són alguns dels ORM que has de conèixer:

 * [Doctrine ORM](http://www.doctrine-project.org/projects/orm.html) *Object relational mapper (ORM) for PHP that sits on top of a powerful database abstraction layer (DBAL). One of its key features is the option to write database queries in a proprietary object oriented SQL dialect called Doctrine Query Language (DQL), inspired by Hibernates HQL. This provides developers with a powerful alternative to SQL that maintains flexibility without requiring unnecessary code duplication.*  

Exemple:

```php
<?php
$employee = new \Entities\Employee();
$employee->setName('test');
$employee->setDepartment('testing');
$em->persist($employee);
$em->flush();
```

 * [Hibernate](http://www.hibernate.org) *Hibernate an open source Java persistence framework project. Perform powerful object relational mapping and query databases using HQL and SQL.*

Exemple:

```Java
String hql = "FROM com.hibernatebook.criteria.Employee";
Query query = session.createQuery(hql);
List results = query.list();
```

 * [Entity Framework](http://msdn.microsoft.com/en-US/data/ef) *Entity Framework (EF) is an object-relational mapper that enables .NET developers to work with relational data using domain-specific objects. It eliminates the need for most of the data-access code that developers usually need to write.*

Exemple:

```VBNET
Using context As New AdventureWorksEntities
    Dim orders As ObjectSet(Of SalesOrderHeader) = context.SalesOrderHeaders

    Dim onlineOrders = _
        From order In orders _
        Where order.OnlineOrderFlag = True _
        Select New With { _
           .SalesOrderID = order.SalesOrderID, _
           .OrderDate = order.OrderDate, _
           .SalesOrderNumber = order.SalesOrderNumber _
        }
```

 * [Django Models](https://docs.djangoproject.com/en/dev/topics/db/models/) *A model is the single, definitive source of information about your data. It contains the essential fields and behaviors of the data you’re storing. Generally, each model maps to a single database table.*

Exemple:

```python linenums
john = Author.objects.create(name="John")
paul = Author.objects.create(name="Paul")
george = Author.objects.create(name="George")
ringo = Author.objects.create(name="Ringo")
entry.authors.add(john, paul, george, ringo)
```

Familiritzat amb el concepte ORM i apren sobre les seves bondats. Els ORM són un bon aliat del programador!

---

#FpInfor #Daw #DawMp07 #DawMp07Uf03

* Resultats d'aprenentatge 1.a
* Continguts 1.1
---

###### Autor: daniel herrera 2013.10.19 20:25:46
###### Editat per: daniel herrera 2013.11.01 16:50:46
###### [CC BY](https://creativecommons.org/licenses/by/4.0/) ![CC BY](https://licensebuttons.net/l/by/3.0/80x15.png)
