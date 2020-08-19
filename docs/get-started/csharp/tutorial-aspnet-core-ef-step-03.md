---
title: 'Paso 3: Trabajar con datos en la aplicación de ASP.NET Core'
description: Empiece a trabajar con datos mediante Entity Framework Core en su aplicación web de ASP.NET Core con este tutorial en vídeo y con instrucciones detalladas.
ms.custom: get-started
ms.date: 03/31/2019
ms.technology: vs-ide-general
ms.prod: visual-studio-windows
monikerRange: vs-2019
ms.topic: tutorial
ms.devlang: CSharp
author: ardalis
ms.author: ornella
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- aspnet
- dotnetcore
ms.openlocfilehash: 42bc0442dc5901f92fc8a83b7af41c1fc42f4be4
ms.sourcegitcommit: 577c905de52057a741e68c2ed168ea527813fda5
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2020
ms.locfileid: "88250795"
---
# <a name="step-3-work-with-data-using-entity-framework"></a>Paso 3: Trabajo con datos mediante Entity Framework

Siga estos pasos para empezar a trabajar con datos mediante Entity Framework Core en su aplicación web de ASP.NET Core.

_Vea este vídeo y siga el tutorial para agregar datos a su primera aplicación de ASP.NET Core._

> [!VIDEO https://www.youtube.com/embed/dulJCwNrqhM]

## <a name="open-your-project"></a>Apertura del proyecto

Si está siguiendo estos vídeos, abra el proyecto de aplicación web que creó en la sección anterior. Si va a empezar aquí, necesita crear un proyecto y elegir **Aplicación web ASP.NET** y, después, **Aplicación web**. Deje el resto de las opciones con su configuración predeterminada.

## <a name="add-your-model"></a>Adición de un modelo

Lo primero que debe hacer para trabajar con datos en la aplicación ASP.NET Core es describir cuál debe ser el aspecto de los datos. A esto lo llamamos crear un *modelo* de los aspectos implicados en el problema que estamos tratando de solucionar. En las aplicaciones del mundo real, vamos a agregar una lógica de negocios personalizada a estos modelos para que puedan comportarse de determinadas formas y automatizar las tareas por nosotros. Para este ejemplo, vamos a crear un sistema sencillo para realizar el seguimiento de los juegos de mesa. Se necesita una clase que representa un juego e incluye algunas propiedades que podríamos registrar sobre ese juego, como cuántos jugadores puede admitir. Esta clase se almacenará en una nueva carpeta que crearemos en la raíz del proyecto web, denominada *Modelos*.

```csharp
public class Game
{
    public int Id { get; set; }
    public string Title { get; set; }
    public int PublicationYear { get; set; }
    public int MinimumPlayers { get; set; }
    public int MaximumPlayers { get; set; }
}
```

## <a name="create-the-pages-to-manage-your-game-library"></a>Creación de las páginas para administrar la biblioteca de juegos

Ahora estamos listos para crear las páginas que vamos a usar para administrar nuestra biblioteca de juegos. Esto puede parecer abrumador, pero es sorprendentemente fácil. En primer lugar, debemos decidir en qué parte de la aplicación se ubicará esta funcionalidad. Abra la carpeta Páginas del proyecto web y agregue ahí una nueva carpeta. Llámela *Juegos*.

Ahora, haga clic con el botón derecho en Juegos y elija **Agregar** > **Nuevo elemento con scaffold**. Elija las instancias de Razor Pages que usan la opción **Entity Framework (CRUD)** . CRUD significa "crear, leer, actualizar y eliminar" y esta plantilla creará páginas para cada una de estas operaciones (incluida una página "Mostrar todo" y una página "Ver los detalles de un elemento").

![Agregar páginas con scaffolding de ASP.NET Core en Visual Studio 2019](media/vs-2019/vs2019-add-scaffold.png)

Seleccione la clase del modelo de juego y use el icono "+" para agregar una nueva clase Contexto de datos. Denomínelo `AppDbContext`. Deje las demás opciones con su configuración predeterminada y haga clic en **Agregar**.

Verá las siguientes instancias de Razor Pages agregadas a la carpeta Juegos:

- Create.cshtml
- Delete.cshtml
- Details.cshtml
- Edit.cshtml
- Index.cshtml

![Páginas con scaffolding de ASP.NET Core en Visual Studio 2019](media/vs-2019/vs2019-scaffolded-pages.png)

Además de agregar páginas a la carpeta *Juegos*, la operación de scaffolding agregó código a la clase *Startup.cs*. Al buscar en el método `ConfigureServices` de esta clase, observará que se ha agregado este código:

```csharp
services.AddDbContext<AppDbContext>(options =>
    options.UseSqlServer(Configuration.GetConnectionString("AppDbContext")));
```

También verá que la cadena de conexión `AppDbContext` se ha agregado al archivo *appsettings.json* del proyecto.

Si ejecuta la aplicación ahora, se puede producir un error porque todavía no se ha creado ninguna base de datos. Puede configurar la aplicación para crear automáticamente la base de datos si es necesario con la [adición del mismo código a Program.cs](/aspnet/core/data/ef-rp/intro?view=aspnetcore-2.1&tabs=visual-studio#update-main):

```csharp
public static void Main(string[] args)
{
    var host = CreateWebHostBuilder(args).Build();

    using (var scope = host.Services.CreateScope())
    {
        var services = scope.ServiceProvider;

        try
        {
            var context = services.GetRequiredService<Data.AppDbContext>();
            context.Database.EnsureCreated();
        }
        catch (Exception ex)
        {
            var logger = services.GetRequiredService<ILogger<Program>>();
            logger.LogError(ex, "An error occurred creating the DB.");
        }
    }

    host.Run();
}
```

Para resolver los valores TypeNames del código anterior, agregue las siguientes instrucciones Using a *Program.cs* al final del bloque de instrucciones Using existente:

```csharp
using Microsoft.Extensions.DependencyInjection;
using WebApplication1.Models;
```

Asegúrese de usar el nombre del proyecto en lugar de WebApplication1 en el código.

La mayor parte del código sirve para el control de errores y para proporcionar acceso al atributo `AppDbContext` de EF Core antes de que se ejecute la aplicación. La línea importante es aquella que dice `context.Database.EnsureCreated()`, que creará la base de datos si aún no existe. Ahora la aplicación está lista para ejecutarse.

## <a name="test-it-out"></a>Pruébela

Ejecute la aplicación y vaya a `/Games` en la barra de direcciones. Verá una página con una lista vacía. Haga clic en **Crear** para agregar un nuevo elemento `Game` a la colección. Rellene el formulario y haga clic en **Crear**. Debe verlo en la vista de lista. Haga clic en **Detalles** para ver los detalles de un único registro.

Agregue otro registro. Puede hacer clic en *Editar* para cambiar los detalles de un registro o en **Eliminar** para quitarlo, para lo que se le pedirá su confirmación antes de eliminar realmente el registro.

![Páginas con scaffolding en el explorador en ASP.NET Core en Visual Studio 2019](media/vs-2019/vs2019-game-list.png)

Eso es todo lo que necesita para empezar a trabajar con datos en una aplicación ASP.NET Core mediante EF Core y Visual Studio 2019.

## <a name="next-steps"></a>Pasos siguientes

En el vídeo siguiente, obtendrá información sobre cómo agregar compatibilidad con la API web a la aplicación.

[Paso 4: Exposición de una API web desde la aplicación de ASP.NET Core](tutorial-aspnet-core-ef-step-04.md)

## <a name="see-also"></a>Vea también

- [Razor Pages con Entity Framework Core en ASP.NET Core](/aspnet/core/data/ef-rp/intro?view=aspnetcore-2.1&tabs=visual-studio)
- [Razor Pages en ASP.NET Core con EF Core](/aspnet/core/data/?view=aspnetcore-2.1)
