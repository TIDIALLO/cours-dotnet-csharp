---
theme: seriph
background: https://images.unsplash.com/photo-1532619187608-e5375cab36a6?auto=format&fit=crop&w=1470&q=80
title: Cours de Programmation C#
info: |
  ## Présenté par Tidiane Diallo  
  Développeur Full Stack & Formateur  
  Contact : tidiane.dev@example.com
class: text-center
transition: slide-left
mdc: true
font: 'Poppins, sans-serif'
drawings:
  persist: false
---

<div class="text-center">
  <h1 style="font-size: 3rem; color: #007bff; font-family: 'Poppins', sans-serif;">Cours de Programmation C#</h1>
</div>

<div class="abs-bl text-left p-4">
  <p style="font-weight: bold; font-family: 'Poppins', sans-serif;"><strong>Tidiane Diallo: </strong> Développeur Full Stack & Formateur</p>
  <p style="font-family: 'Poppins', sans-serif;"><strong>Contact : </strong> diallotidiane014@gmail.com</p>
</div>

<div class="mt-10">
  <carbon:arrow-down class="text-4xl animate-bounce text-indigo-500" />
</div>

---

# <span style="color: #007bff;"> Introduction à la programmation C#</span>

## <span style="color: #007bff;">Qu’est-ce que C# ?</span>

&nbsp;

>C# (prononcé "C sharp") est un langage moderne, orienté objet, créé par **Microsoft**.

&nbsp;
Il est

-  **Fortement typé** : sécurité et clarté
-  **Orienté objet** : classes, héritage, encapsulation
-  **Polyvalent** : web, desktop, mobile, jeux, cloud…
-  **Écosystème .NET** : puissant et complet

---

# <span style="color: #007bff;"> Pourquoi choisir C# ?</span>

&nbsp;

-  **Facile à apprendre** : bien adapté pour les débutants
-  **Robuste et sécurisé** : parfait pour les applications critiques
-  **Excellente documentation et communauté**
-  **Prise en charge des dernières technologies** : microservices, cloud, et plus

---

# <span style="color: #007bff;">Prérequis et Outils</span>
>Aucune connaissance préalable de C# ou .NET n’est exigée  
>On part **de zéro** jusqu’à un **niveau avancé avec la pratique**
&nbsp;

 **1. .NET SDK 8.0 ou supérieur**  
 Téléchargement : [https://dotnet.microsoft.com/en-us/download](https://dotnet.microsoft.com/en-us/download)

&nbsp;

 **2. Un éditeur de code** (au choix) :
-  **Visual Studio 2022+** (idéal pour projets ASP.NET Core) 
[https://visualstudio.microsoft.com/fr/](https://visualstudio.microsoft.com/fr/)

&nbsp;

-  **Visual Studio Code** + Extension **C# Dev Kit** : [https://code.visualstudio.com/](https://code.visualstudio.com/)

---

#  Structure de base d’un programme C#

&nbsp;

```csharp
using System;

class Program
{
    static void Main(string[] args)
    {
        Console.WriteLine("Bonjour, monde !");
    }
}

```
Ce code :

- ***using System;*** :  importe l’**espace de noms(namespace) System**, qui contient ***Console***.
- Déclare une **classe** Program

- Contient une ***méthode Main()*** qui est le point d’entrée du programme

- ***Console.WriteLine*** : Affiche un message dans la **console**

---

# Variables et types de base

## Qu’est-ce qu’une variable ?

> Une variable est **une boîte nommée** dans laquelle on stocke une valeur.

En C#, on doit :
- Déclarer son **type**
- Lui donner un **nom**
- Optionnellement lui donner une **valeur**

---

# Les types de base en C#


| Type        | Description                            | Valeur par défaut | Exemple           |
|-------------|----------------------------------------|-------------------|-------------------|
| `int`       | Nombre entier                          | `0`               | `int x = 10;`     |
| `double`    | Nombre décimal                         | `0.0`             | `double pi = 3.14;`|
| `float`     | Nombre décimal simple précision        | `0.0f`            | `float t = 1.5f;` |
| `decimal`   | Nombre décimal haute précision (argent)| `0.0m`            | `decimal d = 5.99m;` |
| `bool`      | Booléen : vrai ou faux                 | `false`           | `bool actif = true;`|
| `char`      | Un seul caractère                      | `'\0'`            | `char lettre = 'A';`|
| `string`    | Texte (chaîne de caractères)           | `null`            | `string nom = "Ali";`|
| `byte`      | Entier de 0 à 255                      | `0`               | `byte b = 255;`   |
| `short`     | Petit entier signé                     | `0`               | `short s = 10000;`|
| `long`      | Grand entier signé                     | `0L`              | `long id = 123456789L;`|

---

##  Astuce

 `float`, `double`, et `decimal` sont tous décimaux, mais :
- `float` : rapide, moins précis
- `double` : bon compromis
- `decimal` : très précis (comptabilité, argent)

---

## Exemple:

&nbsp;


```csharp

int age = 25;
string nom = "Diallo";
bool estActif = true;
double poids = 72.5;
char initiale = 'B';

Console.WriteLine("Quel est ton prénom ?");
string prenom = Console.ReadLine();
Console.WriteLine($"Bienvenue, {prenom} !");

```


---
title: Instructions de contrôle en C#
---  

# Introduction au contrôle de flux en C#  

&nbsp;

>- Les **instructions de contrôle** permettent de guider l’exécution du programme (conditions, boucles, etc.).  

&nbsp;
>- Nous verrons ici les structures `if`, `else if`, `else`, `switch`, les boucles (`for`, `foreach`, `while`, `do...while`), et les sauts de boucle (`break`, `continue`) ainsi que `return`. 

&nbsp;

> - Ces mécanismes sont essentiels pour faire des choix ou répéter du code en C#.  

---

## Les conditions : `if`, `else if`, `else`  
- L’instruction `if` exécute un bloc de code uniquement si une condition booléenne est vraie:contentReference[oaicite:0]{index=0}.  
- On peut enchaîner plusieurs tests avec `else if` pour tester plusieurs cas.  
- L’instruction `else` permet de définir le bloc exécuté lorsque toutes les conditions précédentes sont fausses.

---

###  Exemple de structure conditionnelle :  
```csharp
int temperature = 15;
if (temperature < 20)
{
    Console.WriteLine("Froid.");   // si condition vraie (température < 20)
}
else if (temperature <= 30)
{
    Console.WriteLine("Chaud.");   // sinon si température entre 20 et 30
}
else
{
    Console.WriteLine("Très chaud !"); // sinon (température > 30)
}
```
---

## Exemple2  : if / else if / else
```csharp
int nombre = 0;
if (nombre > 0)                  // Cas 1 : nombre positif
{
    Console.WriteLine("Nombre positif");
}
else if (nombre < 0)             // Cas 2 : nombre négatif
{
    Console.WriteLine("Nombre négatif");
}
else                             // Cas 3 : nombre est zéro
{
    Console.WriteLine("Zéro");
}
```
---

## L’instruction switch (cas classique)

&nbsp;

>La structure ***switch*** sélectionne le bloc de code à exécuter en comparant une expression à plusieurs cas (valeurs constantes ou patterns)

&nbsp;

- Chaque ***case*** correspond à une valeur (ou condition) possible, et on termine généralement chaque cas par ***break***;.

&nbsp;

- Le bloc --- est exécuté si aucun des cas précédents ne correspond

---

## L’instruction switch (cas classique)

&nbsp;

### Syntaxe basique :

```csharp
switch (variable)
{
    case valeur1:
        // actions si variable == valeur1
        break;
    case valeur2:
        // actions si variable == valeur2
        break;
    default:
        // actions sinon
        break;
}

```
---

## L’instruction switch (cas classique)

&nbsp;

### Exemple : switch sur une valeur entière
```csharp
int jour = 3;
switch (jour)
{
    case 1:
        Console.WriteLine("Lundi");
        break;
    case 2:
        Console.WriteLine("Mardi");
        break;
    default:
        Console.WriteLine("Autre jour");  // exécuté pour 3, 4, 5...
        break;
}

```
---

## **switch** avec ***pattern matching***

> Depuis C# 8+, on peut utiliser des patterns dans les case (par exemple des constantes, des comparaisons, des types)

Par exemple ***case < 0:*** teste si la valeur est inférieure à 0 (mot-clé < introduit un pattern relationnel).

Exemple :

```csharp
   double mesure = -5.0;
switch (mesure)
{
    case < 0:
        Console.WriteLine("Mesure trop basse");   // pour valeurs < 0
        break;
    case > 100:
        Console.WriteLine("Mesure trop haute");   // pour valeurs > 100
        break;
    default:
        Console.WriteLine("Mesure normale");      // pour 0 à 100 inclus
        break;
}

```

---

## Exercice : Que va afficher ce code ?

```csharp
int score = 85;
switch (score)
{
    case int n when (n >= 90):
        Console.WriteLine("Excellent");
        break;
    case int n when (n >= 50):
        Console.WriteLine("Passable");
        break;
    default:
        Console.WriteLine("Insuffisant");
        break;
}

```

---

# Les boucles : répétition de code

> Les boucles permettent de répéter un bloc d'instructions plusieurs fois.

&nbsp;

> Les principales boucles en C# sont : `for`, ``foreach``, ``while``, ``do...while``.

&nbsp;

>On utilise une boucle lorsqu’on doit exécuter du code de façon répétée, par exemple sur un tableau ou jusqu'à une condition donnée.

---

## Boucle ``for``

>La boucle for répète son corps tant qu’une condition est vraie.

**Syntaxe générale** : ``for(initialisation; condition; incrément) { ... }``.


- Initialisation : exécute une fois au début (ex. int i = 0).
- Condition : testée avant chaque itération (la boucle s’arrête quand elle devient fausse).
- Incrément : exécuté à la fin de chaque itération (ex. i++).

&nbsp;


### Exemple:
```csharp
for (int i = 0; i < 3; i++)
{
    Console.WriteLine($"i = {i}");
}

```
---

# Boucle `foreach`

>La boucle foreach parcourt chaque élément d’une collection (tableau, liste, etc.) qui implémente IEnumerable.


**Syntaxe** : ``foreach(type element in collection) { ... }.``

- Elle est utile pour itérer sur tous les éléments d'un tableau ou d'une liste sans gérer soi-même l'indice.

&nbsp;

Exemple :
```csharp
string[] fruits = { "pomme", "banane", "cerise" };
foreach (string fruit in fruits)
{
    Console.WriteLine(fruit); // affiche chaque élément du tableau
}

```

---

## Boucles ``while`` et ``do...while``

>La boucle while répète son bloc tant qu’une condition est vraie.

&nbsp;

- La condition est testée avant chaque itération.
- Si la condition est fausse dès le départ, le corps peut ne jamais s’exécuter (0 itération possible).

Exemple. ``while (condition) { ... }.``

&nbsp;

La boucle ``do...while`` répète son bloc au moins une fois, puis teste la condition après chaque itération.

Syntaxe :

```csharp
do {
    // bloc à exécuter
} while (condition);

```