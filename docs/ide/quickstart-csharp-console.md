---
title: Uso de Visual Studio para crear la primera aplicación de consola de C#
titleSuffix: ''
description: Obtenga información sobre cómo crear una aplicación de consola Hola mundo sencilla en Visual Studio con C#, paso a paso.
ms.date: 09/21/2018
ms.prod: visual-studio-dev15
ms.custom: seodec18
ms.topic: quickstart
ms.devlang: vb
author: TerryGLee
ms.author: tglee
manager: douge
dev_langs:
- CSharp
ms.workload:
- multiple
ms.openlocfilehash: 2b36051f3a316f2b00ebdd08110f22346a910512
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/02/2019
ms.locfileid: "53853923"
---
# <a name="quickstart-use-visual-studio-to-create-your-first-c-console-app"></a>Inicio rápido: Uso de Visual Studio para crear la primera aplicación de consola de C#

En esta introducción al entorno de desarrollo integrado (IDE) de Visual Studio, de entre 5 y 10 minutos, creará una aplicación de C# sencilla que se ejecuta en la consola.

Si todavía no ha instalado Visual Studio, vaya a la página de [descargas de Visual Studio](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017) para instalarlo de forma gratuita.

## <a name="create-a-project"></a>Crear un proyecto

En primer lugar, se creará un proyecto de aplicación C#. En el tipo de proyecto se incluyen todos los archivos de plantilla que vamos a necesitar, sin necesidad de agregar nada más.

1. Abra Visual Studio 2017.

2. En la barra de menús superior, seleccione **Archivo** > **Nuevo** > **Proyecto**.

3. En el cuadro de diálogo **Nuevo proyecto** del panel de la izquierda, expanda **C#** y seleccione **.NET Core**. En el panel central, elija **Aplicación de consola (.NET Core)**. Luego, asigne el nombre *HelloWorld* al proyecto.

   ![Plantilla de proyecto Aplicación de consola (.NET Core) en el cuadro de diálogo Nuevo proyecto en el IDE de Visual Studio](../ide/media/new-project-csharp-dotnetcore-helloworld-console-app.png)

     Si no ve la plantilla de proyecto **Aplicación de consola (.NET Core)**, elija en el vínculo **Abrir el instalador de Visual Studio** en el panel izquierdo del cuadro de diálogo **Nuevo proyecto**.

   ![Elija el vínculo Abrir el Instalador de Visual Studio del cuadro de diálogo Nuevo proyecto](../ide/media/csharp-open-visual-studio-installer-hello-world.png)

     Se iniciará el Instalador de Visual Studio. Elija la carga de trabajo **Desarrollo multiplataforma de .NET Core** y, después, elija **Modificar**.

     ![Carga de trabajo de desarrollo multiplataforma de .NET Core en el Instalador de Visual Studio](../ide/media/dot-net-core-xplat-dev-workload.png)

## <a name="create-the-application"></a>Crear la aplicación

Tras seleccionar la plantilla de proyecto de C# y asignar un nombre al proyecto, Visual Studio crea automáticamente una sencilla aplicación llamada "Hola mundo". 

(Para hacerlo, llama al método <xref:System.Console.WriteLine%2A> para mostrar la cadena literal "Hola mundo" en la ventana de la consola).

   ![Visualización del código de Hello World predeterminado de la plantilla](../ide/media/csharp-console-helloworld-template.png)

Si presiona **F5**, puede ejecutar el programa en modo de depuración. Sin embargo, la ventana de la consola solo se ve durante un momento antes de cerrarse.

(Esto ocurre porque el método `Main` finaliza en cuanto se ejecuta su única instrucción, con lo cual la aplicación termina).

### <a name="add-some-code"></a>Agregar algo de código

Vamos a agregar algo de código para pausar la aplicación para que no se cierre la ventana de consola hasta que presione **ENTRAR**.

1. Agregue el código siguiente inmediatamente después de llamar al método <xref:System.Console.WriteLine%2A>:

   ```csharp
   Console.ReadLine();
   ```

1. Compruebe que tiene un aspecto similar a este en el editor de código:

   ![Agregar código para pausar la aplicación Hola mundo](../ide/media/csharp-console-helloworld-add-code.png)

## <a name="run-the-application"></a>Ejecutar la aplicación

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
