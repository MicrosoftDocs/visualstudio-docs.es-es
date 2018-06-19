---
title: Hola a todos | Documentos de Microsoft
ms.custom: ''
ms.date: 07/10/2017
ms.topic: conceptual
ms.assetid: f74e1ad1-1ee5-4360-9bd5-d82467b884ca
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 7c531d8acddfebcd2656d6dca05b95244f54ec01
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
ms.locfileid: "31134813"
---
# <a name="creating-your-first-extension-hello-world"></a>Crear la primera extensión: Hola a todos

En este ejemplo Hello World se explica cómo crear la primera extensión para Visual Studio. Este tutorial le mostrará cómo agregar un nuevo comando a Visual Studio.

En el proceso, obtendrá información sobre cómo:

* **[Crear un proyecto de extensibilidad](#create-an-extensibility-project)**
* **[Agregar un comando personalizado](#add-a-custom-command)**
* **[Modificar el código fuente](#modify-the-source-code)**
* **[Ejecútelo](#run-it)**

Para este ejemplo, va a usar Visual C# para agregar que un botón de menú personalizado denominado "Ejemplo Hello World!" es similar a esto:

![comando de Hello world](media/hello-world-say-hello-world.png)

## <a name="prerequisites"></a>Requisitos previos

Antes de empezar, asegúrese de que ha instalado el **desarrollo de extensión de Visual Studio** carga de trabajo que incluye la plantilla VSIX podrá necesita y código de ejemplo.

Nota: Puede usar cualquier versión de Visual Studio (Community, Professional o Enterprise) para crear un proyecto de extensibilidad de Visual Studio.

## <a name="create-an-extensibility-project"></a>Crear un proyecto de extensibilidad

Paso 1. Desde el **archivo** menú, haga clic en **nuevo proyecto**. En la parte inferior de la pantalla, puede escribir el nombre del proyecto.

Paso 2. Desde el **plantillas** menú, haga clic en **Visual C#**, haga clic en **extensibilidad**y, a continuación, haga clic en **proyecto VSIX**.

![nuevo proyecto](media/hello-world-new-project.png)

Ahora debería ver la página de introducción y algunos recursos de ejemplo.

Si tiene que dejar este tutorial y volver a él, puede encontrar el nuevo proyecto HelloWorld en la **página de inicio** en el **recientes** sección.

## <a name="add-a-custom-command"></a>Agregar un comando personalizado

Paso 1. Si selecciona el manifiesto, puede ver qué opciones son modificables, versión, descripción, metadatos y instancia.

Paso 2. Haga clic en el proyecto (no la solución). En el menú contextual, haga clic en **agregar**y, a continuación, haga clic en **Control de usuario**.

Paso 3. Vuelva a la **extensibilidad** sección y, a continuación, haga clic en **comando personalizado**.

Paso 4. En el **nombre** en la parte inferior, a continuación, asígnele un nombre, por ejemplo Command.cs.

![comando personalizado](media/hello-world-custom-command.png)

Nuevo comando, se mostrarán en el **el Explorador de soluciones** en el **recursos** bifurcación. Este es también donde encontrará otros archivos relacionados con el comando, como los archivos PNG e ICO si desea modificar la imagen.

## <a name="modify-the-source-code"></a>Modificar el código fuente

En este momento, el botón que se va a agregar es bastante genérico. Tendrá que modificar los archivos VSCT y CS si desea realizar cambios.

* El archivo VSCT es donde se puede cambiar el nombre de los comandos, así como definir donde salen en el sistema de comandos de Visual Studio. Explorar el archivo VSCT, observará mucho código comentado que explica qué cada sección de controles de código.

* El archivo CS es donde puede definir las acciones, como el controlador de clic.

Paso 1. En **el Explorador de soluciones**, busque el archivo VSCT para el nuevo comando. En este caso, se le llamará CommandPackage.vsct.

![comando paquete vsct](media/hello-world-command-package-vsct.png)

Paso 2. Cambiar el `ButtonText` parámetro "Decir Hola a todos!"

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

Paso 3. Vuelva a **el Explorador de soluciones** y busque el archivo Command.cs. Cambiar la cadena de `message` para el comando `string.Format(..)` a "¡Hello World!"

```csharp
  ...
  private void MenuItemCallback(object sender, EventArgs e)
  {
    string message = "Hello World!";
    string title = "Command1";

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

Ahora puede ejecutar el código fuente en la instancia Experimental de Studio Visual.

Paso 1. Haga clic en **iniciar** en la barra de herramientas. Se generará el proyecto e iniciar el depurador, iniciar una nueva instancia de Visual Studio denominada el **instancia Experimental**.

Verá las palabras "Instancia Experimental" en la barra de título de Visual Studio.

![barra de título de la instancia experimental](media/hello-world-exp-instance.png)

Paso 2. En el **herramientas** menú de la **instancia Experimental**, haga clic en **decir Hola a todos!**.

![resultado final](media/hello-world-final-result.png)

Debería ver el resultado en el comando personalizado nuevo, en este caso, el cuadro de diálogo en el centro de la pantalla que le ofrece la "¡Hello World!" .

## <a name="next-steps"></a>Pasos siguientes

Ahora que conoce los conceptos básicos sobre cómo trabajar con la extensibilidad de Visual Studio, aquí es donde puede obtener más información:

* [Empezar a desarrollar extensiones de Visual Studio](starting-to-develop-visual-studio-extensions.md) -ejemplos, tutoriales. y publicar la extensión.
* [What's New en el SDK de Visual Studio de 2017](what-s-new-in-the-visual-studio-2017-sdk.md) -nuevas características de extensibilidad de Visual Studio de 2017
* [Dentro de Visual Studio SDK](internals/inside-the-visual-studio-sdk.md) -Obtenga información acerca de los detalles de extensibilidad de Visual Studio