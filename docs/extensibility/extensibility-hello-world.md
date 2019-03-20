---
title: Tutorial de Hello World extensión | Microsoft Docs
ms.date: 03/14/2019
ms.topic: conceptual
ms.assetid: f74e1ad1-1ee5-4360-9bd5-d82467b884ca
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 3beedce039d1c093b5dfebce07b09d7d3a5795dc
ms.sourcegitcommit: 4d9c54f689416bf1dc4ace058919592482d02e36
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/19/2019
ms.locfileid: "58194741"
---
# <a name="create-your-first-extension-hello-world"></a>Cree su primera extensión: Hello World

En este ejemplo Hello World explica cómo crear su primera extensión para Visual Studio. Este tutorial muestra cómo agregar un comando nuevo a Visual Studio.

En el proceso, obtendrá información sobre cómo:

* **[Crear un proyecto de extensibilidad](#create-an-extensibility-project)**
* **[Agregar un comando personalizado](#add-a-custom-command)**
* **[Modificar el código fuente](#modify-the-source-code)**
* **[Ejecútelo](#run-it)**

Para este ejemplo, va a usar Visual C# para agregar que un botón de menú personalizado denominado "Por ejemplo Hello World!" es similar a esto:

![Comando de Hello World](media/hello-world-say-hello-world.png)

> [!NOTE]
> En este artículo se aplica a Visual Studio en Windows. Para Visual Studio para Mac, consulte [tutorial de extensibilidad en Visual Studio para Mac](/visualstudio/mac/extending-visual-studio-mac-walkthrough).

## <a name="prerequisites"></a>Requisitos previos

Antes de empezar, asegúrese de que ha instalado el **desarrollo de extensiones de Visual Studio** carga de trabajo, que incluye la plantilla VSIX a necesita y código de ejemplo.

> [!NOTE]
> Puede usar cualquier edición de Visual Studio (Community, Professional o Enterprise) para crear un proyecto de extensibilidad de Visual Studio.

## <a name="create-an-extensibility-project"></a>Crear un proyecto de extensibilidad

::: moniker range="vs-2017"

Paso 1. En el menú **Archivo**, seleccione **Nuevo** > **Proyecto**.

Paso 2. En el cuadro de búsqueda en la esquina superior derecha, escriba "vsix" y seleccione el objeto Visual C# **proyecto VSIX**. Escriba "Hola a todos" para el **nombre** en la parte inferior del cuadro de diálogo y seleccione **Aceptar**.

![nuevo proyecto](media/hello-world-new-project.png)

Ahora debería ver la página de introducción y algunos recursos de ejemplo.

Si tiene que dejar este tutorial y se vuelve a ella, puede encontrar el nuevo proyecto HelloWorld en la **página de inicio** en el **recientes** sección.

::: moniker-end

::: moniker range=">=vs-2019"

Paso 1. En el menú **Archivo**, seleccione **Nuevo** > **Proyecto**. Busque "vsix" y seleccione el objeto Visual C# **proyecto VSIX** y, a continuación, **siguiente**.

Paso 2. Escriba "Hola a todos" para el **nombre del proyecto** y seleccione **crear**.

![nuevo proyecto](media/hello-world-new-project-2019.png)

Ahora debería ver el proyecto HelloWorld en **el Explorador de soluciones**.

::: moniker-end

## <a name="add-a-custom-command"></a>Agregar un comando personalizado

Paso 1. Si selecciona el *.vsixmanifest* archivo de manifiesto, puede ver qué opciones son modificables, como descripción, autor y versión.

Paso 2. Haga clic en el proyecto (no la solución). En el menú contextual, seleccione **agregar**y, a continuación, **nuevo elemento**.

Paso 3. Seleccione el **extensibilidad** sección y, a continuación, elija **comando personalizado**.

Paso 4. En el **nombre** en la parte inferior, escriba un nombre de archivo como *Command.cs*.

![comando personalizado](media/hello-world-custom-command.png)

El nuevo archivo de comandos está visible en **el Explorador de soluciones**. En el **recursos** nodo, encontrará otros archivos relacionados con el comando. Por ejemplo, si desea modificar la imagen, el archivo PNG es aquí.

## <a name="modify-the-source-code"></a>Modificar el código fuente

En este punto, el comando y el texto del botón están generado automáticamente y no muy interesante. Puede modificar el archivo VSCT y el archivo CS si desea realizar cambios.

* El archivo VSCT es donde se puede cambiar el nombre de los comandos, así como definir donde entran en el sistema de comandos de Visual Studio. Explorar el archivo VSCT, observará los comentarios que explican lo que cada sección de los controles de código VSCT.

* El archivo CS es donde puede definir las acciones, como el controlador de clics.

::: moniker range="vs-2017"

Paso 1. En **el Explorador de soluciones**, busque el archivo VSCT para el nuevo comando. En este caso, se llamará *CommandPackage.vsct*.

![comando paquete vsct](media/hello-world-command-package-vsct.png)

::: moniker-end

::: moniker range=">=vs-2019"

Paso 1. En **el Explorador de soluciones**, busque el archivo VSCT para el paquete de extensión de VS. En este caso, se llamará *HelloWorldPackage.vsct*.

::: moniker-end

Paso 2. Cambiar el `ButtonText` parámetro `Say Hello World!`.

```xml
  ...
  <Button guid="guidCommandPackageCmdSet" id="CommandId" priority="0x0100" type="Button">
     <Parent guid="guidCommandPackageCmdSet" id="MyMenuGroup" />
     <Icon guid="guidImages" id="bmpPic1" />
     <Strings>
        <ButtonText>Say Hello World!</ButtonText>
     </Strings>
  </Button>
  ...
```

Paso 3. Vuelva a **el Explorador de soluciones** y busque el *Command.cs* archivo. En el `Execute` método, cambie la cadena `message` desde `string.Format(..)` a `Hello World!`.

```csharp
  ...
  private void Execute(object sender, EventArgs e)
  {
    ThreadHelper.ThrowIfNotOnUIThread();
    string message = "Hello World!";
    string title = "Command";

    // Show a message box to prove we were here
    VsShellUtilities.ShowMessageBox(
        this.ServiceProvider,
        message,
        title,
        OLEMSGICON.OLEMSGICON_INFO,
        OLEMSGBUTTON.OLEMSGBUTTON_OK,
        OLEMSGDEFBUTTON.OLEMSGDEFBUTTON_FIRST);
  }
  ...
```

Asegúrese de guardar los cambios en cada archivo.

## <a name="run-it"></a>Ejecútelo

Ahora puede ejecutar el código fuente en la instancia Experimental de Visual Studio.

Paso 1. Presione **F5** para ejecutar el **Iniciar depuración** comando. Este comando compila el proyecto y se inicia el depurador, iniciar una nueva instancia de Visual Studio denominada el **instancia Experimental**.

::: moniker range="vs-2017"

Verá las palabras **instancia Experimental** en la barra de título de Visual Studio.

![barra de título de la instancia experimental](media/hello-world-exp-instance.png)

::: moniker-end

Paso 2. En el **herramientas** menú de la **instancia Experimental**, haga clic en **Say Hello World!**.

![resultado final](media/hello-world-final-result.png)

Debería ver la salida desde el nuevo comando personalizado, en este caso, el cuadro de diálogo en el centro de la pantalla que le ofrece la **Hello World!** no encontrada".

## <a name="next-steps"></a>Pasos siguientes

Ahora que conoce los conceptos básicos de trabajar con la extensibilidad de Visual Studio, aquí es donde puede obtener más información:

* [Empezar a desarrollar extensiones de Visual Studio](starting-to-develop-visual-studio-extensions.md) -ejemplos, tutoriales. y publicar la extensión
* [Novedades de Visual Studio 2017 SDK](what-s-new-in-the-visual-studio-2017-sdk.md) -nuevas características de extensibilidad de Visual Studio 2017
* [Novedades en el SDK de Visual Studio 2019](whats-new-visual-studio-2019-sdk.md) -nuevas características de extensibilidad de Visual Studio de 2019
* [Dentro de Visual Studio SDK](internals/inside-the-visual-studio-sdk.md) -Obtenga información sobre los detalles de extensibilidad de Visual Studio