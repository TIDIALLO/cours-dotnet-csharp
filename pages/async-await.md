# Programmation asynchrone: Async/Await en C#

---

## Pourquoi utiliser `async` et `await` ?

&nbsp;

### Amélioration des performances
- Évite de bloquer le thread principal.
- Utile pour les appels réseau ou les bases de données.

&nbsp;

### Meilleure utilisation des ressources
- Libère le thread pour d'autres tâches.
- Optimise la réactivité.

&nbsp;

### Lisibilité accrue
- Plus clair que les callbacks ou tâches imbriquées.

---

## Fonctionnement de `async/await`

&nbsp;

### Déclaration de la méthode
- Mot-clé **`async`** : identifie une méthode asynchrone.

&nbsp;

### Utilisation de `await`
- Attend qu'une **tâche** asynchrone se termine.
- Libère le contrôle temporairement pour d'autres opérations.

&nbsp;


### Retour de `Task` ou `Task<T>`
- **`Task`** : pour une méthode sans retour.
- **`Task<T>`** : pour une méthode qui retourne une valeur.

---

## Exemple de Code : Async/Await

&nbsp;

```csharp
// Opération Asynchrone Exemple
public async Task<Book?> FindBookAndSaveAsync(int id)
{
    using var dbContext = new BookDbContext();

    // Trouver un livre dans la base de données
    var book = await dbContext.Books!.FindAsync(id);
    if (book == null) return null;

    book.LastAccessed = DateTime.Now;
    await dbContext.SaveChangesAsync();

    return book;
}
```