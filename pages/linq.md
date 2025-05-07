# Introduction à Language Integrated Query (LINQ) 

---

## Qu'est-ce que LINQ ?

&nbsp;

- **LINQ** est un acronyme pour **Language Integrated Query**.
- C'est une fonctionnalité de .NET qui permet d'écrire des requêtes sur des sources de données.
- LINQ fournit une syntaxe **déclarative** pour interroger des données.
- Il fonctionne avec diverses sources de données : 
  - Collections en mémoire (listes, tableaux).
  - Bases de données SQL.
  - Fichiers XML.
  - Autres sources via des bibliothèques personnalisées.

---

## Les Avantages de LINQ

&nbsp;

1. **Lisibilité accrue** : Les requêtes ressemblent au SQL.
2. **Moins de code** : Facilite l’écriture et la maintenance.
3. **Détection des erreurs à la compilation** : Type-safe.
4. **Uniformité** : Une syntaxe unique pour toutes les sources de données.
5. **Performances optimisées** : Utilise le principe du "lazy loading" pour évaluer les données uniquement quand nécessaire.

---

## Principaux Types de LINQ
1. **LINQ to Objects**
   - Interroger les collections en mémoire (`List<T>`, tableaux, etc.).
   - Permet de trier, filtrer et transformer les objets.
   
2. **LINQ to SQL**
   - Interroge une base de données relationnelle.
   - Traduit la requête LINQ en SQL.
   
3. **LINQ to XML**
   - Traite et manipule des données XML.

4. **LINQ to Entities**
   - Fonctionne avec Entity Framework pour les bases de données.

5. **LINQ to JSON** *(via des bibliothèques externes comme Newtonsoft.Json)* :
   - Interroge et transforme des documents JSON.

---

## Syntaxe LINQ
### Deux approches
1. **Syntaxe de Requête** (similaire au SQL) :
```csharp
   var results = from item in collection
                 where item.Condition
                 select item;
```

&nbsp;

2. **Syntaxe de Méthode** (à l'aide de méthodes d'extension comme Where, Select) :

```csharp
var results = collection.Where(item => item.Condition);
```

---

##
- **Language Integrated Query (LINQ)** est une fonctionnalité de .NET.
- Fournit une **syntaxe déclarative** pour interroger des données.
- Fonctionne avec diverses sources de données :
  - Collections en mémoire (listes, tableaux).
  - Bases de données SQL.
  - Fichiers XML.
  - Autres sources via des bibliothèques personnalisées.

---

## Les Avantages de LINQ

&nbsp;


1. **Lisibilité accrue** : Les requêtes ressemblent au SQL.
2. **Moins de code** : Facilite l’écriture et la maintenance.
3. **Détection des erreurs à la compilation** : Type-safe.
4. **Uniformité** : Une syntaxe unique pour toutes les sources de données.
5. **Performances optimisées** : Utilise le principe du "lazy loading" pour évaluer les données uniquement quand nécessaire.

---

## Principaux Types de LINQ
1. **LINQ to Objects**
   - Interroger les collections en mémoire (`List<T>`, tableaux, etc.).
   - Permet de trier, filtrer et transformer les objets.
   
2. **LINQ to SQL**
   - Interroge une base de données relationnelle.
   - Traduit la requête LINQ en SQL.
   
3. **LINQ to XML**
   - Traite et manipule des données XML.

4. **LINQ to Entities**
   - Fonctionne avec Entity Framework pour les bases de données.

5. **LINQ to JSON** *(via des bibliothèques externes comme Newtonsoft.Json)* :
   - Interroge et transforme des documents JSON.

---

## Syntaxe LINQ
### Deux approches
1. **Syntaxe de Requête** (similaire au SQL) :
```csharp
   var results = from item in collection
                 where item.Condition
                 select item;
```

&nbsp;

2. **Syntaxe de Méthode** (à l'aide de méthodes d'extension comme Where, Select) :


```csharp
var results = collection.Where(item => item.Condition);
```

---

## Exemple : LINQ to Objects

### Syntaxe de requête

```csharp
    List<int> numbers = new() { 1, 2, 3, 4, 5, 6 };

    var evenNumbers = from n in numbers
                    where n % 2 == 0
                    select n;

    foreach (var num in evenNumbers)
    {
        Console.WriteLine(num);
    }

```
---

# Exemples Simples d'Utilisation de LINQ

---

## Exemple 1 : Filtrer une Liste

```csharp
using System;
using System.Collections.Generic;
using System.Linq;

public class Program
{
    public static void Main()
    {
        List<int> numbers = new List<int> { 1, 2, 3, 4, 5, 6, 7, 8, 9, 10 };
        var evenNumbers = numbers.Where(n => n % 2 == 0);

        Console.WriteLine("Nombres pairs:");
        foreach (var num in evenNumbers)
        {
            Console.WriteLine(num);
        }
    }
}
```

---

# Exemple 2 : Sélectionner des Propriétés d'Objets


```csharp
using System;
using System.Collections.Generic;
using System.Linq;

public class Person
{
    public string Name { get; set; }
    public int Age { get; set; }
}

public class Program
{
    public static void Main()
    {
        List<Person> people = new List<Person>
        {
            new Person { Name = "Alice", Age = 30 },
            new Person { Name = "Bob", Age = 25 },
            new Person { Name = "Charlie", Age = 35 }
        };

        var names = people.Select(p => p.Name);

        Console.WriteLine("Noms des personnes:");
        foreach (var name in names)
        {
            Console.WriteLine(name);
        }
    }
}
```

---

# Exemple 3 : Trier une Liste

```csharp

using System;
using System.Collections.Generic;
using System.Linq;

public class Program
{
    public static void Main()
    {
        List<string> fruits = new List<string> { "Banana", "Apple", "Cherry", "Blueberry" };
        var sortedFruits = fruits.OrderBy(f => f);

        Console.WriteLine("Fruits triés:");
        foreach (var fruit in sortedFruits)
        {
            Console.WriteLine(fruit);
        }
    }
}
```