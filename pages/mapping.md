# Tidiane Diallo

**Développeur Fullstack et Formateur**

---

# Entity Framework Core

## 1. Installation des packages nécessaires

Ajoutez les packages NuGet nécessaires dans votre projet pour travailler avec EF Core. Cela peut être fait via la console du gestionnaire de packages ou le fichier `.csproj`.

### Exemple pour SQLite :

```xml
<ItemGroup>
  <PackageReference Include="Microsoft.EntityFrameworkCore" Version="8.0.0" />
  <PackageReference Include="Microsoft.EntityFrameworkCore.Sqlite" Version="8.0.0" />
  <PackageReference Include="Microsoft.EntityFrameworkCore.Tools" Version="8.0.0" />
</ItemGroup>
```

---

## 2. Création d'un contexte de base de données

Créez une classe héritant de `DbContext` pour gérer vos entités.

### Exemple :

```csharp
using Microsoft.EntityFrameworkCore;

namespace MonProjet.Data;

public class BookDbContext : DbContext
{
    public BookDbContext(DbContextOptions<BookDbContext> options) : base(options) { }

    public DbSet<Book> Books { get; set; }

    protected override void OnModelCreating(ModelBuilder modelBuilder)
    {
        modelBuilder.Entity<Book>().HasData(
            new Book { Id = 1, Title = "Clean Code", Author = "Robert C. Martin", DatePub = new DateTime(2008, 8, 1) },
            new Book { Id = 2, Title = "The Pragmatic Programmer", Author = "Andrew Hunt", DatePub = new DateTime(1999, 10, 20) }
        );
    }
}
```

---

## 3. Configuration de la chaîne de connexion

Ajoutez une chaîne de connexion dans `appsettings.json` pour spécifier la base de données.

### Exemple :

```json
{
  "ConnectionStrings": {
    "Bibliotheque": "Data Source=Bibliotheque.db"
  }
}
```

---

## 4. Configuration dans `Program.cs`

Configurez EF Core pour utiliser la chaîne de connexion.

### Exemple :

```csharp
var builder = WebApplication.CreateBuilder(args);
var connectionString = builder.Configuration.GetConnectionString("Bibliotheque");
builder.Services.AddSqlite<BookDbContext>(connectionString);
var app = builder.Build();
```

---

## 5. Création des migrations

Créez et appliquez les migrations avec les outils EF Core :

### Commandes :

```bash
dotnet ef migrations add InitialCreate
dotnet ef database update
```

---

## 6. Utilisation dans l'application

Injectez `BookDbContext` dans vos contrôleurs ou endpoints pour effectuer des opérations CRUD.

### Exemple :

```csharp
app.MapGet("/books", async (BookDbContext dbContext) =>
{
    var books = await dbContext.Books.ToListAsync();
    return Results.Ok(books);
});
```

---

## 7. Migration automatique de la base de données

Ajoutez une méthode pour appliquer automatiquement les migrations lors du démarrage de l'application.

### Exemple :

```csharp
public static class DataExtensions
{
    public static async Task MigrateDbAsync(this WebApplication app)
    {
        using var scope = app.Services.CreateScope();
        var dbContext = scope.ServiceProvider.GetRequiredService<BookDbContext>();
        await dbContext.Database.MigrateAsync();
    }
}

// Appel dans `Program.cs` :
await app.MigrateDbAsync();
```

---

Avec ces étapes, votre application est configurée pour utiliser Entity Framework Core avec une base de données SQLite.
