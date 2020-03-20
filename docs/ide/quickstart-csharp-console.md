---
title: Uso de Visual Studio para crear la primera aplicación de consola de C#
titleSuffix: ''
description: Obtenga información sobre cómo crear una aplicación de consola Hola mundo sencilla en Visual Studio con C#, paso a paso.
ms.custom: seodec18
ms.date: 03/23/2019
ms.technology: vs-ide-general
ms.prod: visual-studio-windows
ms.topic: quickstart
ms.devlang: vb
author: ornellaalt
ms.author: ornella
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- multiple
ms.openlocfilehash: 20b2cf2bf12e9b24ca12d0a73b43e4a56e8246f4
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/20/2020
ms.locfileid: "77579492"
---
# <a name="quickstart-use-visual-studio-to-create-your-first-c-console-app"></a>Inicio rápido: Uso de Visual Studio para crear la primera aplicación de consola de C#

En esta introducción al entorno de desarrollo integrado (IDE) de Visual Studio, de entre 5 y 10 minutos, creará una aplicación de C# sencilla que se ejecuta en la consola.

::: moniker range="vs-2017"

Si todavía no ha instalado Visual Studio, vaya a la página de [descargas de Visual Studio](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) para instalarlo de forma gratuita.

::: moniker-end

::: moniker range="vs-2019"

Si todavía no ha instalado Visual Studio, vaya a la página de [descargas de Visual Studio](https://visualstudio.microsoft.com/downloads) para instalarlo de forma gratuita.

::: moniker-end

## <a name="create-a-project"></a>Crear un proyecto

En primer lugar, se creará un proyecto de aplicación C#. En el tipo de proyecto se incluyen todos los archivos de plantilla que vamos a necesitar, sin necesidad de agregar nada más.

::: moniker range="vs-2017"

1. Abra Visual Studio 2017.

2. En la barra de menús superior, elija **Archivo** > **Nuevo** > **Proyecto**.

3. En el cuadro de diálogo **Nuevo proyecto** del panel de la izquierda, expanda **C#** y seleccione **.NET Core**. En el panel central, elija **Aplicación de consola (.NET Core)**. Luego, asigne el nombre *HelloWorld* al proyecto.

   ![Plantilla de proyecto Aplicación de consola (.NET Core) en el cuadro de diálogo Nuevo proyecto en el IDE de Visual Studio](../ide/media/new-project-csharp-dotnetcore-helloworld-console-app.png)

     Si no ve la plantilla de proyecto **Aplicación de consola (.NET Core)**, elija en el vínculo **Abrir el instalador de Visual Studio** en el panel izquierdo del cuadro de diálogo **Nuevo proyecto**.

   ![Elija el vínculo Abrir el Instalador de Visual Studio del cuadro de diálogo Nuevo proyecto](../ide/media/csharp-open-visual-studio-installer-hello-world.png)

     Se iniciará el Instalador de Visual Studio. Elija la carga de trabajo **Desarrollo multiplataforma de .NET Core** y, después, elija **Modificar**.

     ![Carga de trabajo de desarrollo multiplataforma de .NET Core en el Instalador de Visual Studio](../ide/media/dot-net-core-xplat-dev-workload.png)

::: moniker-end

::: moniker range="vs-2019"

1. Abra Visual Studio 2019.

1. En la ventana de inicio, elija **Crear un proyecto nuevo**.

   ![Ventana "Crear un proyecto"](../get-started/media/vs-2019/create-new-project-dark-theme.png)

1. En el cuadro de búsqueda de la ventana **Crear un proyecto**, escriba *consola*. Seguidamente, elija **C#** en la lista de lenguajes y luego, **Windows** en la lista de plataformas. 

   Después de aplicar los filtros de lenguaje y plataforma, elija la plantilla **Aplicación de consola (.NET Core)** y luego, **Siguiente**.

   ![Elija la plantilla C# para Aplicación de consola (.NET Framework).](../get-started/csharp/media/vs-2019/csharp-create-new-project-search-console-net-core-filtered.png)

   > [!NOTE]
   > Si no ve la plantilla **Aplicación de consola (.NET Core)**, puede instalarla desde la ventana **Crear un proyecto**. En el mensaje **¿No encuentra lo que busca?**, elija el vínculo **Instalar más herramientas y características**.
   >
   > ![Vínculo "Instalar más herramientas y características" del mensaje "¿No encuentra lo que busca?" que aparece en la ventana "Crear proyecto"](../get-started/media/vs-2019/not-finding-what-looking-for.png) 
   > 
   > Luego, en el Instalador de Visual Studio, elija la carga de trabajo **Desarrollo multiplataforma de .NET Core**.
   >
   > ![Carga de trabajo de desarrollo multiplataforma de .NET Core en el Instalador de Visual Studio](./media/dot-net-core-xplat-dev-workload.png)
   >
   > Después, elija el botón **Modificar** en el Instalador de Visual Studio. Es posible que se le pida que guarde su trabajo; si es así, hágalo. Seguidamente, elija **Continuar** para instalar la carga de trabajo. Luego, vuelva al paso 2 de este procedimiento "[Crear un proyecto](#create-a-project)".

1. En la ventana **Configurar el nuevo proyecto**, escriba *HelloWorld* en el cuadro **Nombre del proyecto**. Luego, elija **Crear**.

   ![En la ventana "Configurar el nuevo proyecto", asigne al proyecto el nombre "HelloWorld"](../get-started/csharp/media/vs-2019/csharp-name-your-helloworld-project.png)

   Visual Studio se abre en el nuevo proyecto.
   
::: moniker-end

## <a name="create-the-application"></a>Creación de la aplicación

::: moniker range="vs-2017"

Tras seleccionar la plantilla de proyecto de C# y asignar un nombre al proyecto, Visual Studio crea automáticamente una sencilla aplicación llamada "Hola mundo".

::: moniker-end

::: moniker range="vs-2019"

Visual Studio incluye código predeterminado de "Hola mundo" en el proyecto.

::: moniker-end

(Para ello, llama al método <xref:System.Console.WriteLine%2A> que muestra la cadena literal "Hola mundo" en la ventana de la consola).

   ![Visualización del código de Hello World predeterminado de la plantilla](../ide/media/csharp-console-helloworld-template.png)

Si presiona **F5**, puede ejecutar el programa en modo de depuración. Sin embargo, la ventana de la consola solo se ve durante un momento antes de cerrarse.

(Este comportamiento se debe a que el método `Main` finaliza en cuanto se ejecuta su única instrucción, con lo cual la aplicación termina).

### <a name="add-some-code"></a>Agregar algo de código

Vamos a agregar algo de código para pausar la aplicación para que no se cierre la ventana de consola hasta que presione **ENTRAR**.

1. Agregue el código siguiente inmediatamente después de llamar al método <xref:System.Console.WriteLine%2A>:

   ```csharp
   Console.ReadLine();
   ```

1. Compruebe que tiene un aspecto similar a este en el editor de código:

   ![Agregar código para pausar la aplicación Hola mundo](../ide/media/csharp-console-helloworld-add-code.png)

## <a name="run-the-application"></a>Ejecución de la aplicación

1. Elija el botón **HelloWorld** de la barra de herramientas para ejecutar la aplicación en el modo de depuración. (O puede presionar **F5**.)

   ![Elección del botón HelloWorld para ejecutar la aplicación desde la barra de herramientas](../ide/media/csharp-console-hello-world-button.png)

1. Vea la aplicación en la ventana de la consola.

   ![Ventana de la consola que muestra Hola mundo](../ide/media/csharp-console-hello-world.png)

### <a name="close-the-application"></a>Cierre de la aplicación

1. Presione **ENTRAR** para cerrar la ventana de la consola.

1. Cierre el panel **Salida** en Visual Studio.

   ![Cierre del panel Salida en Visual Studio](../ide/media/csharp-hello-world-close-output-pane.png)

1. Cierre Visual Studio.

## <a name="next-steps"></a>Pasos siguientes

¡Enhorabuena por completar este tutorial de inicio rápido! Esperamos que haya aprendido un poco sobre el IDE de Visual Studio y C#. Para más información, continúe con los tutoriales siguientes.

> [!div class="nextstepaction"]
> [Introducción a la aplicación de consola de C# en Visual Studio](../get-started/csharp/tutorial-console.md)
