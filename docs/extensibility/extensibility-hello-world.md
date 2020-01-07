---
title: Tutorial de extensión de Hola mundo | Microsoft Docs
ms.date: 03/14/2019
ms.topic: conceptual
ms.assetid: f74e1ad1-1ee5-4360-9bd5-d82467b884ca
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 0345d67a4202b8b267d213e0c288847e2774f722
ms.sourcegitcommit: 8e123bcb21279f2770b28696995450270b4ec0e9
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/25/2019
ms.locfileid: "75404139"
---
# <a name="create-your-first-extension-hello-world"></a>Cree la primera extensión: Hola mundo

En este Hola mundo ejemplo se explica cómo crear la primera extensión para Visual Studio. En este tutorial se muestra cómo agregar un nuevo comando a Visual Studio.

En el proceso, obtendrá información sobre cómo:

* **[Crear un proyecto de extensibilidad](#create-an-extensibility-project)**
* **[Agregar un comando personalizado](#add-a-custom-command)**
* **[Modificar el código fuente](#modify-the-source-code)**
* **[Ejecútelo](#run-it)**

En este ejemplo, usará visual C# para agregar un botón de menú personalizado denominado "Say Hola mundo!" tiene el siguiente aspecto:

![Comando Hola mundo](media/hello-world-say-hello-world.png)

> [!NOTE]
> Este artículo se aplica a Visual Studio en Windows. Para obtener Visual Studio para Mac, consulte la [Guía de extensibilidad en Visual Studio para Mac](/visualstudio/mac/extending-visual-studio-mac-walkthrough).

## <a name="prerequisites"></a>Requisitos previos

Antes de empezar, asegúrese de que ha instalado la carga de trabajo **desarrollo de extensión de Visual Studio** , que incluye la plantilla VSIX que necesitará y el código de ejemplo.

> [!NOTE]
> Puede usar cualquier edición de Visual Studio (Community, Professional o Enterprise) para crear un proyecto de extensibilidad de Visual Studio.

## <a name="create-an-extensibility-project"></a>Crear un proyecto de extensibilidad

::: moniker range="vs-2017"

Paso 1. En el menú **Archivo**, seleccione **Nuevo** > **Proyecto**.

Paso 2. En el cuadro de búsqueda de la parte superior derecha, escriba "VSIX" y seleccione C# el proyecto de Visual **VSIX**. Escriba "HelloWorld" como **nombre** en la parte inferior del cuadro de diálogo y seleccione **Aceptar**.

![nuevo proyecto](media/hello-world-new-project.png)

Ahora debería ver la página Introducción y algunos recursos de ejemplo.

Si necesita abandonar este tutorial y volver a él, puede encontrar el nuevo proyecto HelloWorld en la **Página de inicio** de la sección **reciente** .

::: moniker-end

::: moniker range=">=vs-2019"

Paso 1. En el menú **Archivo**, seleccione **Nuevo** > **Proyecto**. Busque "VSIX" y seleccione el proyecto visual C# **VSIX** y luego **siguiente**.

Paso 2. Escriba "HelloWorld" como **nombre del proyecto** y seleccione **crear**.

![nuevo proyecto](media/hello-world-new-project-2019.png)

Ahora debería ver el proyecto HelloWorld en **Explorador de soluciones**.

::: moniker-end

## <a name="add-a-custom-command"></a>Agregar un comando personalizado

Paso 1. Si selecciona el archivo de manifiesto *. vsixmanifest* , puede ver qué opciones son modificables, como descripción, autor y versión.

Paso 2. Haga clic con el botón secundario en el proyecto (no en la solución). En el menú contextual, seleccione **Agregar**y, a continuación, **nuevo elemento**.

Paso 3. Seleccione la sección **extensibilidad** y, a continuación, elija **comando**.

Paso 4. En el campo **nombre** de la parte inferior, escriba un nombre de archivo como *Command.CS*.

![comando personalizado](media/hello-world-vsix-command.png)

El nuevo archivo de comandos está visible en **Explorador de soluciones**. En el nodo **recursos** , encontrará otros archivos relacionados con el comando. Por ejemplo, si desea modificar la imagen, el archivo PNG está aquí.

## <a name="modify-the-source-code"></a>Modificar el código fuente

En este momento, el texto del comando y del botón se genera automáticamente y no es muy interesante. Puede modificar el archivo VSCT y el archivo CS Si desea realizar cambios.

* El archivo VSCT es donde puede cambiar el nombre de los comandos, así como definir dónde van en el sistema de comandos de Visual Studio. A medida que explore el archivo VSCT, verá comentarios que explican lo que cada sección del código de VSCT controla.

* El archivo CS es donde puede definir acciones, como el controlador de clics.

::: moniker range="vs-2017"

Paso 1. En **Explorador de soluciones**, busque el archivo VSCT para el nuevo comando. En este caso, se llamará *CommandPackage. Vsct*.

![paquete de comandos Vsct](media/hello-world-command-package-vsct.png)

::: moniker-end

::: moniker range=">=vs-2019"

Paso 1. En **Explorador de soluciones**, busque el archivo VSCT de la extensión vs package. En este caso, se llamará *HelloWorldPackage. Vsct*.

::: moniker-end

Paso 2. Cambie el parámetro `ButtonText` a `Say Hello World!`.

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

Paso 3. Vuelva a **Explorador de soluciones** y busque el archivo *Command.CS* . En el método `Execute`, cambie la cadena `message` de `string.Format(..)` a `Hello World!`.

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

## <a name="run-it"></a>Ejecútelo.

Ahora puede ejecutar el código fuente en la instancia experimental de Visual Studio.

Paso 1. Presione **F5** para ejecutar el comando **iniciar depuración** . Este comando compila el proyecto e inicia el depurador, iniciando una nueva instancia de Visual Studio denominada **instancia experimental**.

::: moniker range="vs-2017"

Verá las palabras **instancia experimental** en la barra de título de Visual Studio.

![barra de título de instancia experimental](media/hello-world-exp-instance.png)

::: moniker-end

Paso 2. En el menú **herramientas** de la **instancia experimental**, haga clic en **Say Hola mundo!** .

![resultado final](media/hello-world-final-result.png)

Debería ver el resultado del nuevo comando personalizado, en este caso el cuadro de diálogo en el centro de la pantalla que le proporciona el **Hola mundo.** no encontrada".

## <a name="next-steps"></a>Pasos siguientes

Ahora que conoce los conceptos básicos sobre cómo trabajar con extensibilidad de Visual Studio, aquí puede obtener más información:

* [Comience a desarrollar extensiones de Visual Studio](starting-to-develop-visual-studio-extensions.md) : ejemplos, tutoriales. y publicación de la extensión
* [Novedades del SDK de Visual studio 2017](what-s-new-in-the-visual-studio-2017-sdk.md) : nuevas características de extensibilidad en visual Studio 2017
* [Novedades del SDK de Visual studio 2019](whats-new-visual-studio-2019-sdk.md) : nuevas características de extensibilidad en visual Studio 2019
* [En el SDK de Visual Studio](internals/inside-the-visual-studio-sdk.md) : obtener información detallada sobre la extensibilidad de Visual Studio
