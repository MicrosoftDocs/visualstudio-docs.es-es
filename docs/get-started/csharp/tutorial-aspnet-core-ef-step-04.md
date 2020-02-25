---
title: 'Paso 4: Exposición de una API web desde la aplicación de ASP.NET Core'
description: Agregue una API web a la aplicación web de ASP.NET Core con este tutorial en vídeo y con instrucciones detalladas.
ms.custom: get-started
ms.date: 02/13/2020
ms.technology: vs-ide-general
ms.prod: visual-studio-windows
monikerRange: vs-2019
ms.topic: tutorial
ms.devlang: CSharp
author: ardalis
ms.author: tglee
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- aspnet
- dotnetcore
ms.openlocfilehash: 67d3887c7cf665f9fd8d2789d460cc1a595e2bff
ms.sourcegitcommit: 68f893f6e472df46f323db34a13a7034dccad25a
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/15/2020
ms.locfileid: "77271507"
---
# <a name="step-4-expose-a-web-api-from-your-aspnet-core-app"></a>Paso 4: Exposición de una API web desde la aplicación de ASP.NET Core

Siga estos pasos para agregar una API web a la aplicación de ASP.NET Core existente.

_Vea este vídeo y siga el tutorial para agregar compatibilidad con la API web a la primera aplicación de ASP.NET Core._

> [!VIDEO https://www.youtube.com/embed/o_fYPOsAXts]

## <a name="open-your-project"></a>Apertura del proyecto

Abra la aplicación de ASP.NET Core en Visual Studio 2019. La aplicación ya debe usar EF Core para administrar los tipos de modelos, como se configuró en el [paso 3 de esta serie de tutoriales](tutorial-aspnet-core-ef-step-03.md).

## <a name="add-an-api-controller"></a>Adición de un controlador de API

Haga clic con el botón derecho en el proyecto y agregue una nueva carpeta denominada *Api*. A continuación, haga clic con el botón derecho en esta carpeta y elija **Agregar** > **Nuevo elemento con scaffold**. Elija **Controlador de API con acciones mediante Entity Framework**. Ahora, elija una clase de modelo existente y haga clic en **Agregar**.

![Controlador de API con scaffolding de ASP.NET Core en Visual Studio 2019](media/vs-2019/vs2019-add-scaffold-api.png)

## <a name="reviewing-the-generated-controller"></a>Revisión del controlador generado

El código generado incluye una nueva clase de controlador. En la parte superior de la definición de clase hay dos atributos.

```csharp
[Route("api/[controller]")]
[ApiController]
public class GamesController : ControllerBase
```

El primero especifica la ruta de las acciones en este controlador como `api/[controller]`, lo que significa que, si el controlador se denomina `GamesController`, la ruta será `api/Games`.

El segundo atributo, `[ApiController]`, agrega algunas validaciones útiles a la clase, como asegurarse de que cada método de acción incluye su propio atributo `[Route]`.

```csharp
public class GamesController : ControllerBase
{
    private readonly AppDbContext _context;

    public GamesController(AppDbContext context)
    {
        _context = context;
    }
```

El controlador usa el atributo `AppDbContext` existente, que se pasa a su constructor. Cada acción utilizará este campo para trabajar con los datos de la aplicación.

```csharp
// GET: api/Games
[HttpGet]
public IEnumerable<Game> GetGame()
{
    return _context.Game;
}
```

El primer método es una solicitud GET sencilla, como se especifica mediante el atributo `[HttpGet]`. No toma ningún parámetro y devuelve una lista de todos los juegos de la base de datos.

```csharp
// GET: api/Games/5
[HttpGet("{id}")]
public async Task<IActionResult> GetGame([FromRoute] int id)
{
    if (!ModelState.IsValid)
    {
        return BadRequest(ModelState);
    }

    var game = await _context.Game.FindAsync(id);

    if (game == null)
    {
        return NotFound();
    }

    return Ok(game);
}
```

El método siguiente especifica `{id}` en la ruta, que se agregará a la ruta después de `/`, de tal forma que la ruta completa tenga un aspecto similar a `api/Games/5`, como se muestra en el comentario en la parte superior. La entrada `id` se asigna al parámetro `id` del método. Dentro del método, si el modelo no es válido, se devuelve un resultado `BadRequest`. De lo contrario, EF intentará encontrar el registro coincidente con el atributo `id` proporcionado. Si no es posible, se devuelve un resultado `NotFound`; de lo contrario, se devuelve el registro `Game` apropiado.

```csharp
// PUT: api/Games/5
[HttpPut("{id}")]
public async Task<IActionResult> PutGame([FromRoute] int id, [FromBody] Game game)
{
    if (!ModelState.IsValid)
    {
        return BadRequest(ModelState);
    }

    if (id != game.Id)
    {
        return BadRequest();
    }

    _context.Entry(game).State = EntityState.Modified;

    try
    {
        await _context.SaveChangesAsync();
    }
    catch (DbUpdateConcurrencyException)
    {
        if (!GameExists(id))
        {
            return NotFound();
        }
        else
        {
            throw;
        }
    }

    return NoContent();
}
```

A continuación, se utiliza la solicitud `[HttpPut]` realizada a la API para ejecutar las actualizaciones. El nuevo registro `Game` se proporciona en el cuerpo de la solicitud. Se realiza alguna validación y comprobación de errores y, si todo se completa correctamente, el registro de la base de datos se actualiza con los valores proporcionados en el cuerpo de la solicitud. De lo contrario, se devuelve una respuesta de error apropiada.

```csharp
// POST: api/Games
[HttpPost]
public async Task<IActionResult> PostGame([FromBody] Game game)
{
    if (!ModelState.IsValid)
    {
        return BadRequest(ModelState);
    }

    _context.Game.Add(game);
    await _context.SaveChangesAsync();

    return CreatedAtAction("GetGame", new { id = game.Id }, game);
}
```

Se usa una solicitud `[HttpPost]` para agregar nuevos registros al sistema. Igual que con `[HttpPut]`, se agrega el registro al cuerpo de la solicitud. Si es válido, EF Core agrega el registro a la base de datos y la acción devuelve el registro actualizado (con el identificador de la base de datos generado) y un vínculo al registro de la API.

```csharp
// DELETE: api/Games/5
[HttpDelete("{id}")]
public async Task<IActionResult> DeleteGame([FromRoute] int id)
{
    if (!ModelState.IsValid)
    {
        return BadRequest(ModelState);
    }

    var game = await _context.Game.FindAsync(id);
    if (game == null)
    {
        return NotFound();
    }

    _context.Game.Remove(game);
    await _context.SaveChangesAsync();

    return Ok(game);
}
```

Por último, se usa una ruta `[HttpDelete]` con un identificador para eliminar un registro. Si la solicitud es válida y existe un registro con el identificador especificado, EF Core lo elimina de la base de datos.

## <a name="adding-swagger"></a>Adición de Swagger

Swagger es una herramienta de pruebas y documentación de API que se puede agregar como un conjunto de servicios y middleware a una aplicación de ASP.NET Core. Para ello, haga clic con el botón derecho en el proyecto y elija **Administrar paquetes NuGet**. A continuación, haga clic en **Examinar**, y busque `Swashbuckle.AspNetCore` e instale la versión 4.0.1.

![Agregar Swashbuckle desde Nuget en Visual Studio 2019](media/vs-2019/vs2019-nuget-swashbuckle.png)

Una vez instalado, abra `Startup.cs` y agregue lo siguiente al final del método `ConfigureServices`:

```csharp
services.AddSwaggerGen(c =>
{
    c.SwaggerDoc("v1", new Info { Title = "My API", Version = "v1" });
});
```

También deberá agregar `using Swashbuckle.AspNetCore.Swagger;` en la parte superior del archivo.

A continuación, agregue lo siguiente al método `Configure`, justo antes de `UseMvc`:

```csharp
// Enable middleware to serve generated Swagger as a JSON endpoint.
app.UseSwagger();

// Enable middleware to serve swagger-ui (HTML, JS, CSS, etc.), 
// specifying the Swagger JSON endpoint.
app.UseSwaggerUI(c =>
{
    c.SwaggerEndpoint("/swagger/v1/swagger.json", "My API V1");
});
```

Ahora debería poder compilar y ejecutar la aplicación. En el explorador, vaya a `/swagger` en la barra de direcciones. Debería ver una lista de los modelos y los puntos de conexión de API de la aplicación. 

![Página de Swagger en el explorador en Visual Studio 2019](media/vs-2019/vs2019-swagger-browser.png)

Haga clic en un punto de conexión en Juegos y, a continuación, ejecute `Try it out` y `Execute` para ver cómo se comportan los diferentes puntos de conexión.

## <a name="next-steps"></a>Pasos siguientes

En el vídeo siguiente, obtendrá información sobre cómo implementar la aplicación en Azure.

[Paso 5: Implementación de la aplicación de ASP.NET Core en Azure](tutorial-aspnet-core-ef-step-05.md)

## <a name="see-also"></a>Vea también

- [Introducción a Swashbuckle y ASP.NET Core](/aspnet/core/tutorials/getting-started-with-swashbuckle?view=aspnetcore-2.2&tabs=visual-studio)
- [Páginas de ayuda de ASP.NET Core Web API con Swagger/Open API](/aspnet/core/tutorials/web-api-help-pages-using-swagger?view=aspnetcore-2.2)