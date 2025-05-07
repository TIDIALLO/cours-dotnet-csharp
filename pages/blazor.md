---
title: Introduction à Blazor WebAssembly
theme: seriph
---

# Introduction à Blazor WebAssembly

&nbsp;

Blazor WebAssembly (WASM) est un framework de développement web basé sur .NET, permettant de créer des applications web interactives côté client directement dans le navigateur, sans nécessiter JavaScript.
&nbsp;
Il repose sur le standard **WebAssembly**, une technologie permettant d'exécuter des applications proches des performances natives dans les navigateurs modernes.

---

## Objectifs du cours

- Comprendre ce qu'est Blazor WebAssembly.
- Découvrir les principales fonctionnalités de Blazor WebAssembly.
- Apprendre à créer une application simple avec Blazor WebAssembly.
- Manipuler les composants, les données, et les formulaires.
- Comprendre comment Blazor WebAssembly s'intègre à une API backend.

---

## Qu'est-ce que Blazor WebAssembly ?

&nbsp;

- **Blazor** est un framework .NET pour les applications web.
- **WebAssembly** est un format binaire permettant l'exécution de code proche des performances natives dans un navigateur.
- Avec Blazor WASM, le code .NET est exécuté directement dans le navigateur.

---

## Pourquoi utiliser Blazor WebAssembly ?

&nbsp;

- Partage de code entre le frontend et le backend.
- Pas besoin de connaître JavaScript pour créer des applications interactives.
- Un écosystème puissant grâce à .NET.
- Support multiplateforme et open source.

---

## Fonctionnalités principales

&nbsp;

- **Composants réutilisables** : Les applications sont construites à l'aide de composants.
- **Binding bidirectionnel** : Synchronisation automatique entre le modèle et l'interface utilisateur.
- **Injection de dépendances** : Support intégré pour DI (Dependency Injection).
- **Interopérabilité avec JavaScript** : Possibilité d'appeler des bibliothèques JavaScript existantes.
- **Support des formulaires et validation** : Intégration simplifiée pour manipuler des formulaires complexes.

---

## Créer une application avec Blazor WebAssembly


### Étapes pour créer une application

&nbsp;

```csharp

dotnet new blazorwasm -o GestionBibliotheque.Blazor
cd GestionBibliotheque.Blazor
dotnet run
```

Cela va créer un projet Blazor WebAssembly complet, comprenant :

---

## Structure du projet Frontend

![Texte alternatif](../images/b1.png)

---

## Intégrer le projet backend (nos APIs) avec le frontend

&nbsp;

Créer deux dossiers sur le projet Frontend:
- Models: Contenir des modèles(DTOs) de données pour représenter les livres 
- Services: contient  service dans le client Blazor pour interagir avec les endpoints du backend. Par exemple, un service BookService :

Démo

---

## Créer un model DTO pour la liste des BookService

&nbsp;

dans le dossier model, créer une classe BookDto.cs:

```csharp
namespace GestionBibliotheque.Blazor.Models
{
    public class BookDto
    {
        public int Id { get; set; }
        public string Title { get; set; } = string.Empty;
        public string Author { get; set; } = string.Empty;
        public DateTime DatePub{ get; set; }
    }
}
```
&nbsp;

cette classe sera utiliser pour la liste des livres
Pour les autres opérations (Recupérer  un livre par son Id, Ajouter et supprimer), on devra ajouter un model ie une classe
---

##  Créer un Service 

L'étape suivante est de créer un service pour encapsuler les données
Pour ce faire, on créer une interface IBookService pour définir nos différents méthodes,
ensuite créer une classe BookService qui va implémenter cette interface

&nbsp; 
Créer IBookService.cs et BookService.cs dans le dossier Service

```csharp
using  GestionBibliotheque.Blazor.Models;

namespace GestionBibliotheque.Blazor.Services
{
    public interface IBookService
    {
        
        Task<BookDto?> GetBookByIdAsync(int id);
    }
}
```

---

##  Créer un Service 

&nbsp;

créer la classe BookService qui implémente IBookService
```csharp

```