---
# You can also start simply with 'default'
theme: seriph
# random image from a curated Unsplash collection by Anthony
# like them? see https://unsplash.com/collections/94734566/slidev
background: https://cover.sli.dev
# some information about your slides (markdown enabled)
title: Welcome to Slidev
info: |
  ## Slidev Starter Template
  Presentation slides for developers.

  Learn more at [Sli.dev](https://sli.dev)
# apply unocss classes to the current slide
class: text-center
# https://sli.dev/features/drawing
drawings:
  persist: false
# slide transition: https://sli.dev/guide/animations.html#slide-transitions
transition: slide-left
# enable MDC Syntax: https://sli.dev/features/mdc
mdc: true
---

# ASP.NET Core

 Présenté par Tidiane diallo

<div @click="$slidev.nav.next" class="mt-12 py-1" hover:bg="white op-10">
   <carbon:arrow-right />
</div>

<div class="abs-br m-6 text-xl">
  <button @click="$slidev.nav.openInEditor" title="Open in Editor" class="slidev-icon-btn">
    <carbon:edit />
  </button>
  <a href="https://github.com/slidevjs/slidev" target="_blank" class="slidev-icon-btn">
    <carbon:logo-github />
  </a>
</div>

<!--
The last comment block of each slide will be treated as slide notes. It will be visible and editable in Presenter Mode along with the slide. [Read more in the docs](https://sli.dev/guide/syntax.html#notes)
-->

---
transition: fade-out
---

# Qu'est-ce qu'un DTO ?

&nbsp;

Un DTO (Data Transfer Object) est une classe utilisée pour transférer des données entre différentes couches ou parties d'une application, notamment entre l'API et le client. Contrairement aux entités de la base de données, un DTO est conçu pour contenir uniquement les données nécessaires à une opération particulière.

---

# Pourquoi utiliser des DTOs ?

&nbsp;

- Séparation des responsabilités: 
  - Cela empêche d'exposer des informations sensibles ou inutiles de votre modèle de données.
- Contrôle des données échangées:
  - Avec un DTO, vous pouvez contrôler exactement quelles propriétés sont envoyées ou reçues.
- Flexibilité
  - Vous pouvez transformer ou enrichir les données avant de les transmettre au client.
- Facilitation des validations
  - Les DTOs peuvent inclure des annotations de validation comme [Required], [MaxLength], etc., pour s'assurer que les données envoyées par le client respectent certaines règles.

---

# Résumé

&nbsp;

Les DTOs permettent de :

- Contrôler les données échangées entre les clients et l'API.
- Protéger votre modèle de base de données.
- Faciliter les validations et les transformations.
- Maintenir une flexibilité et une modularité dans votre code.

---

# Mapping (mappage)

## Qu'est-ce que le mapping ?

Le **mapping** consiste à convertir ou copier les données d'un objet vers un autre. Dans le contexte des applications ASP.NET Core, cela signifie généralement **mapper**

- Les données d'un DTO (Data Transfer Object) vers une entité.
- Ou les données d'une entité vers un DTO.

Le mapping est utilisé pour s'assurer que chaque couche de votre application (par exemple, la couche de persistance et la couche d'API) manipule uniquement les objets qui lui sont destinés.

---

# Mapping automatique avec AutoMapper

&nbsp;

AutoMapper est une bibliothèque populaire en .NET qui permet de mapper automatiquement les propriétés similaires entre deux objets.

Les données d'un DTO (Data Transfer Object) vers une entité.
Ou les données d'une entité vers un DTO.
Le mapping est utilisé pour s'assurer que chaque couche de votre application (par exemple, la couche de persistance et la couche d'API) manipule uniquement les objets qui lui sont destinés.

---

# Étapes pour configurer et utiliser AutoMapper

Ajoutez AutoMapper et AutoMapper.Extensions.Microsoft.DependencyInjection à votre projet en utilisant la commande suivante dans le terminal :


1. Installer le package NuGet

```csharp
dotnet add package AutoMapper
dotnet add package AutoMapper.Extensions.Microsoft.DependencyInjection

```

---

# Étapes pour configurer et utiliser AutoMapper

2. Créer un profil de mappage

```csharp

public class BookMapping : Profile
{
    public BookMapping()
    {
        CreateMap<Book, BookDto>();
        CreateMap<CreateBookDto, Book>();
    }
}

```

---

#  Étapes pour configurer et utiliser AutoMapper

3. Configurer AutoMapper dans le projet

```csharp

using AutoMapper;
builder.Services.AddAutoMapper(typeof(Program));

```

---

#  Étapes pour configurer et utiliser AutoMapper

4. Utiliser AutoMapper dans vos endpoints

Injectez l'interface IMapper pour effectuer le mappage.

Exemple : Endpoint pour récupérer une liste de livres (Mapping de Book vers BookDto)
```csharp

```

---

# Introduction à Entity Framework Core (EF Core)

&nbsp;

Entity Framework Core (EF Core) est un ORM (Object-Relational Mapper) open source pour .NET. Il simplifie les interactions entre une application .NET et une base de données en permettant de manipuler les données comme des objets C# sans écrire de requêtes SQL complexes.

En termes simples, EF Core fait le lien entre vos classes C# (entités) et votre base de données, en vous permettant d'effectuer des opérations CRUD (Create, Read, Update, Delete) avec des objets.

---

# Pourquoi utiliser EF Core ?

&nbsp;

- Code maintenable : Les entités et leurs relations sont définies dans le code, ce qui facilite les modifications et la compréhension du projet.
- Indépendance du fournisseur : EF Core prend en charge plusieurs bases de données (SQL Server, MySQL, PostgreSQL, SQLite, etc.).
- Migrations : Vous pouvez facilement créer, modifier ou synchroniser les schémas de base de données avec vos entités via les migrations.
- Support des relations complexes : EF Core gère les relations entre tables (un-à-un, un-à-plusieurs, plusieurs-à-plusieurs).
- nteropérabilité LINQ : Vous pouvez écrire des requêtes avec LINQ (Language-Integrated Query) pour interroger les données.

---

#  Comment fonctionne EF Core ?

&nbsp;

EF Core repose sur trois concepts principaux :

1. **Entités** : Ce sont des classes C# qui représentent les tables de votre base de données.

Exemple: Une entité Book correspondra à une table Books.

```csharp
namespace GestionBibilotheque.Api.Entities
{
    public class Book
    {
        public int Id { get; set; }
        public required string Title { get; set; }
        public required string Author { get; set; }
        public DateOnly DatePub{ get; set; }
    }
}
```

---

# install
- dotnet add package Microsoft.EntityFrameworkCore.Sqlite --version 8.0.11
- dotnet tool install --global dotnet-ef
- dotnet add package Microsoft.EntityFrameworkCore.Design
- dotnet ef migrations add InitialCreate    
- dotnet ef database update   

---

#  Comment fonctionne EF Core ?

&nbsp;

2. DbContext : Une classe spéciale qui gère la connexion à la base de données et le suivi des entités.

Exemple : BookDbContext permet à EF Core de gérer la table Books.

```csharp
public class BookDbContext : DbContext
{
    public BookDbContext(DbContextOptions<BookDbContext> options) : base(options) { }

    public DbSet<Book> Books { get; set; }
}
// ou bien avec Primary constructor
public class BookDbContext(DbContextOptions<BookDbContext> options) : DbContext(options)
{
    public DbSet<Book>? Books { get; set; }

}
```
Ajouter
---

#  Comment fonctionne EF Core ?

&nbsp;

3. Migrations : EF Core utilise un système de migrations pour gérer les modifications du schéma de la base de données.

dotnet ef migrations add InitialCreate
dotnet ef database update

---

# COnfigurer  EF Core dans Program.cs

&nbsp;

Ajouter dans Program.cs

```csharp
// Ajouter EF Core Sqlite
//var connectionString = "Data  Souce = Bibliotheque.db";
var connectionString = builder.Configuration.GetConnectionString("Bibliotheque");
builder.Services.AddSqlite<BookDbContext>(connectionString);
var builder = WebApplication.CreateBuilder(args);



 // Ajouter EF Core avec SQL Server
builder.Services.AddDbContext<BookDbContext>(options =>
    options.UseSqlServer(builder.Configuration.GetConnectionString("DefaultConnection")));

var app = builder.Build();

```
