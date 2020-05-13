---
title: Tutorial de extensión de Hello World ( Hello World extension tutorial) Microsoft Docs
ms.date: 03/14/2019
ms.topic: conceptual
ms.assetid: f74e1ad1-1ee5-4360-9bd5-d82467b884ca
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c66f48a4b3c5948393e10f34810f3cb87c78c924
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80711657"
---
# <a name="create-your-first-extension-hello-world"></a>Crea tu primera extensión: Hello World

Este ejemplo de Hello World le guía a través de la creación de la primera extensión para Visual Studio. En este tutorial se muestra cómo agregar un nuevo comando a Visual Studio.

En el proceso, aprenderá a:

* **[Crear un proyecto de extensibilidad](#create-an-extensibility-project)**
* **[Agregar un comando personalizado](#add-a-custom-command)**
* **[Modificar el código fuente](#modify-the-source-code)**
* **[Ejecútelo.](#run-it)**

En este ejemplo, usará Visual C para agregar un botón de menú personalizado denominado "Say Hello World!" que se ve así:

![Comando Hello World](media/hello-world-say-hello-world.png)

> [!NOTE]
> Este artículo se aplica a Visual Studio en Windows. Para Visual Studio para Mac, vea Tutorial de [extensibilidad en Visual Studio para Mac](/visualstudio/mac/extending-visual-studio-mac-walkthrough).

## <a name="prerequisites"></a>Prerrequisitos

Antes de empezar, asegúrese de que ha instalado la carga de trabajo de desarrollo de extensiones de **Visual Studio,** que incluye la plantilla VSIX que necesitará y código de ejemplo.

> [!NOTE]
> Puede usar cualquier edición de Visual Studio (Community, Professional o Enterprise) para crear un proyecto de extensibilidad de Visual Studio.

## <a name="create-an-extensibility-project"></a>Crear un proyecto de extensibilidad

::: moniker range="vs-2017"

Paso 1. En el menú **Archivo**, seleccione **Nuevo** > **Proyecto**.

Paso 2. En el cuadro de búsqueda de la parte superior derecha, escriba "vsix" y seleccione el proyecto Visual C. **VSIX**. Escriba "HelloWorld" para el **Nombre** en la parte inferior del cuadro de diálogo y seleccione **Aceptar**.

![nuevo proyecto](media/hello-world-new-project.png)

Ahora debería ver la página Introducción y algunos recursos de ejemplo.

Si necesita dejar este tutorial y volver a él, puede encontrar su nuevo proyecto HelloWorld en la página de **inicio** en la sección **Reciente.**

::: moniker-end

::: moniker range=">=vs-2019"

Paso 1. En el menú **Archivo**, seleccione **Nuevo** > **Proyecto**. Busque "vsix" y seleccione el **proyecto VSIX** de Visual C. y, a continuación, **Siguiente**.

Paso 2. Escriba "HelloWorld" para el nombre del **proyecto** y seleccione **Crear**.

![nuevo proyecto](media/hello-world-new-project-2019.png)

Ahora debería ver el proyecto HelloWorld en el Explorador de **soluciones.**

::: moniker-end

## <a name="add-a-custom-command"></a>Agregar un comando personalizado

Paso 1. Si selecciona el archivo de manifiesto *.vsixmanifest,* puede ver qué opciones se pueden cambiar, como la descripción, el autor y la versión.

Paso 2. Haga clic con el botón derecho en el proyecto (no en la solución). En el menú contextual, seleccione **Agregar**y, a continuación, **Nuevo elemento**.

Paso 3. Seleccione la sección **Extensibilidad** y, a continuación, elija **Comando**.

Paso 4. En el campo **Nombre** de la parte inferior, escriba un nombre de archivo como *Command.cs*.

![comando personalizado](media/hello-world-vsix-command.png)

El nuevo archivo de comandos está visible en el Explorador de **soluciones.** En el nodo **Recursos,** encontrará otros archivos relacionados con el comando. Por ejemplo, si desea modificar la imagen, el archivo PNG está aquí.

## <a name="modify-the-source-code"></a>Modificar el código fuente

En este punto, el comando y el texto del botón se generan automáticamente y no son muy interesantes. Puede modificar el archivo VSCT y el archivo CS si desea realizar cambios.

* El archivo VSCT es donde puede cambiar el nombre de los comandos, así como definir dónde van en el sistema de comandos de Visual Studio. A medida que explora el archivo VSCT, observará comentarios que explican lo que controla cada sección del código VSCT.

* El archivo CS es donde puede definir acciones, como el controlador de clics.

::: moniker range="vs-2017"

Paso 1. En **el Explorador**de soluciones , busque el archivo VSCT para el nuevo comando. En este caso, se llamará *CommandPackage.vsct*.

![paquete de comandos vsct](media/hello-world-command-package-vsct.png)

::: moniker-end

::: moniker range=">=vs-2019"

Paso 1. En **el Explorador**de soluciones , busque el archivo VSCT para el paquete VS de extensión. En este caso, se llamará *HelloWorldPackage.vsct*.

::: moniker-end

Paso 2. Cambie `ButtonText` el `Say Hello World!`parámetro a .

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

Paso 3. Vuelva al **Explorador de** soluciones y busque el archivo *Command.cs.* En `Execute` el método, `message` cambie `string.Format(..)` `Hello World!`la cadena de a .

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

Paso 1. Presione **F5** para ejecutar el comando **Iniciar depuración.** Este comando compila el proyecto e inicia el depurador, lanzando una nueva instancia de Visual Studio denominada **Instancia experimental**.

::: moniker range="vs-2017"

Verá las palabras **Instancia experimental** en la barra de título de Visual Studio.

![barra de título de instancia experimental](media/hello-world-exp-instance.png)

::: moniker-end

Paso 2. En el menú **Herramientas** de la **Instancia Experimental**, haga clic en Say **Hello World!**.

![resultado final](media/hello-world-final-result.png)

Debería ver la salida de su nuevo comando personalizado, en este caso el cuadro de diálogo en el centro de la pantalla que le da el **Hello World!** de la directiva).

## <a name="next-steps"></a>Pasos siguientes

Ahora que conoce los conceptos básicos de trabajar con la extensibilidad de Visual Studio, aquí es donde puede obtener más información:

* [Comience a desarrollar extensiones](starting-to-develop-visual-studio-extensions.md) de Visual Studio- Ejemplos, tutoriales. y la publicación de su extensión
* [Novedades del SDK de Visual Studio 2017:](what-s-new-in-the-visual-studio-2017-sdk.md) nuevas características de extensibilidad en Visual Studio 2017
* [Novedades del SDK de Visual Studio 2019:](whats-new-visual-studio-2019-sdk.md) nuevas características de extensibilidad en Visual Studio 2019
* Dentro del SDK de [Visual Studio:](internals/inside-the-visual-studio-sdk.md) aprenda los detalles de la extensibilidad de Visual Studio
