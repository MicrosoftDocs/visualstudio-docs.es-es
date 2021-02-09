---
title: Tutorial de la extensión Hola mundo | Microsoft Docs
description: Aprenda a agregar un nuevo comando como extensión a Visual Studio, lo que conlleva crear un proyecto, agregar un comando y modificar el código fuente.
ms.custom: SEO-VS-2020
ms.date: 03/14/2019
ms.topic: tutorial
ms.assetid: f74e1ad1-1ee5-4360-9bd5-d82467b884ca
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 7e943da6745832cbe59cfe94013650a503265636
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99903288"
---
# <a name="tutorial---create-your-first-extension-hello-world"></a>Tutorial: Creación de la primera extensión: Hello World

En este ejemplo Hola mundo se explica cómo crear la primera extensión para Visual Studio. En este tutorial se muestra cómo agregar un nuevo comando a Visual Studio.

En el proceso, obtendrá información sobre cómo:

* **[Crear un proyecto de extensibilidad](#create-an-extensibility-project)**
* **[Agregar un comando personalizado](#add-a-custom-command)**
* **[Modificar el código fuente](#modify-the-source-code)**
* **[Ejecútelo.](#run-it)**

En este ejemplo, usará Visual C# para agregar un botón de menú personalizado con el nombre "Diga Hola mundo" que tiene este aspecto:

![Comando Hola mundo](media/hello-world-say-hello-world.png)

> [!NOTE]
> Este artículo se aplica a Visual Studio para Windows. En el caso de Visual Studio para Mac, vea [Tutorial de extensibilidad en Visual Studio para Mac](/visualstudio/mac/extending-visual-studio-mac-walkthrough).

## <a name="prerequisites"></a>Requisitos previos

Antes de empezar, asegúrese de que ha instalado la carga de trabajo **Desarrollo de extensiones de Visual Studio**, en la que se incluye la plantilla VSIX que necesitará y el código de ejemplo.

> [!NOTE]
> Puede usar cualquier edición de Visual Studio (Community, Professional o Enterprise) para crear un proyecto de extensibilidad de Visual Studio.

## <a name="create-an-extensibility-project"></a>Creación de un proyecto de extensibilidad

::: moniker range="vs-2017"

Paso 1. En el menú **Archivo**, seleccione **Nuevo** > **Proyecto**.

Paso 2. En el cuadro de búsqueda de la parte superior derecha, escriba "vsix" y seleccione el **Proyecto VSIX** de Visual C#. Escriba "HelloWorld" para el **Nombre** en la parte inferior del cuadro de diálogo y seleccione **Aceptar**.

![nuevo proyecto](media/hello-world-new-project.png)

Ahora debería ver la página Introducción y algunos recursos de ejemplo.

Si tiene que salir de este tutorial y después regresar, puede encontrar el nuevo proyecto HelloWorld en la **Página de inicio** en la sección **Recientes**.

::: moniker-end

::: moniker range=">=vs-2019"

Paso 1. En el menú **Archivo**, seleccione **Nuevo** > **Proyecto**. Busque "vsix", seleccione el **Proyecto VSIX** de Visual C# y después **Siguiente**.

Paso 2. Escriba "HelloWorld" en **Nombre del proyecto** y seleccione **Crear**.

![nuevo proyecto](media/hello-world-new-project-2019.png)

Ahora debería ver el proyecto HelloWorld en el **Explorador de soluciones**.

::: moniker-end

## <a name="add-a-custom-command"></a>Adición de un comando personalizado

Paso 1. Si selecciona el archivo de manifiesto *.vsixmanifest*, puede ver qué opciones se pueden cambiar, como la descripción, el autor y la versión.

Paso 2. Haga clic con el botón derecho en el proyecto (no en la solución). En el menú contextual, seleccione **Agregar** y después **Nuevo elemento**.

Paso 3. Seleccione la sección **Extensibilidad** y después **Comando**.

Paso 4. En el campo **Nombre** de la parte inferior, escriba un nombre de archivo como *Command.cs*.

![Comando personalizado](media/hello-world-vsix-command.png)

El nuevo archivo de comandos se muestra en el **Explorador de soluciones**. En el nodo **Recursos** encontrará otros archivos relacionados con el comando. Por ejemplo, si quiere modificar la imagen, aquí se incluye el archivo PNG.

## <a name="modify-the-source-code"></a>Modificación del código fuente

En este momento, el texto del comando y del botón se generan de forma automática y no son muy interesantes. Puede modificar los archivos VSCT y CS si quiere realizar cambios.

* En el archivo VSCT puede cambiar el nombre de los comandos, así como definir su destino en el sistema de comandos de Visual Studio. A medida que explore el archivo VSCT, verá comentarios que explican lo que controla cada sección del código de VSCT.

* En el archivo CS puede definir acciones, como el controlador de clics.

::: moniker range="vs-2017"

Paso 1. En el **Explorador de soluciones**, busque el archivo VSCT para el nuevo comando. En este caso, se llamará *CommandPackage.vsct*.

![CommandPackage.vsct](media/hello-world-command-package-vsct.png)

::: moniker-end

::: moniker range=">=vs-2019"

Paso 1. En el **Explorador de soluciones**, busque el archivo VSCT del paquete VS de la extensión. En este caso, se llamará *HelloWorldPackage.vsct*.

::: moniker-end

Paso 2. Cambie el parámetro `ButtonText` a `Say Hello World!`.

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

Paso 3. Vuelva al **Explorador de soluciones** y busque el archivo *Command.cs*. En el método `Execute`, cambie la cadena `message` de `string.Format(..)` a `Hello World!`.

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

Asegúrese de guardar los cambios en todos los archivos.

## <a name="run-it"></a>Ejecútelo.

Ahora puede ejecutar el código fuente en la instancia experimental de Visual Studio.

Paso 1. Presione **F5** para ejecutar el comando **Iniciar depuración**. Este comando compila el proyecto e inicia el depurador, e inicia una nueva instancia de Visual Studio denominada **Instancia experimental**.

::: moniker range="vs-2017"

Verá las palabras **Instancia experimental** en la barra de título de Visual Studio.

![Barra de título de Instancia experimental](media/hello-world-exp-instance.png)

::: moniker-end

Paso 2. En el menú **Herramientas** de **Instancia experimental**, haga clic en **Say Hello World!** (Diga Hola mundo).

![Resultado final](media/hello-world-final-result.png)

Debería ver el resultado del nuevo comando personalizado, en este caso el cuadro de diálogo en el centro de la pantalla en el que se muestra **Hola mundo.** de la directiva).

## <a name="next-steps"></a>Pasos siguientes

Ahora que conoce los conceptos básicos sobre cómo trabajar con la extensibilidad en Visual Studio, aquí puede obtener más información:

* [Comienzo del desarrollo de extensiones de Visual Studio](starting-to-develop-visual-studio-extensions.md): ejemplos, tutoriales y publicación de la extensión
* [Novedades del SDK de Visual Studio 2017](what-s-new-in-the-visual-studio-2017-sdk.md): nuevas características de extensibilidad en Visual Studio 2017
* [Novedades del SDK de Visual Studio 2019](whats-new-visual-studio-2019-sdk.md): nuevas características de extensibilidad en Visual Studio 2019
* [Dentro del SDK de Visual Studio](internals/inside-the-visual-studio-sdk.md): información detallada sobre la extensibilidad de Visual Studio
