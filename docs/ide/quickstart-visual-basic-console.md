---
title: 'Inicio rápido: Crear la primera aplicación de consola en Visual Studio con Visual Basic | Microsoft Docs'
ms.custom: ''
ms.date: 12/10/2017
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-acquisition
ms.tgt_pltfrm: ''
ms.topic: quickstart
ms.devlang: vb
author: TerryGLee
ms.author: tglee
manager: ghogen
dev_langs:
- vb
ms.workload:
- multiple
ms.openlocfilehash: a531582b2474305d7c286f936e29a7bc9804d7bf
ms.sourcegitcommit: e01ccb5ca4504a327d54f33589911f5d8be9c35c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/15/2018
---
# <a name="quickstart-create-your-first-console-app-in-visual-studio-with-visual-basic"></a>Inicio rápido: Crear la primera aplicación de consola en Visual Studio con Visual Basic
En esta introducción al entorno de desarrollo integrado (IDE) de Visual Studio, de entre 5 y 10 minutos, creará una sencilla aplicación de Visual Basic que se ejecuta en la consola.

Si todavía no ha instalado Visual Studio, vaya a la página de [descargas de Visual Studio](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs) para instalarlo de forma gratuita.

## <a name="create-a-project"></a>Crear un proyecto
En primer lugar, crearemos un proyecto de aplicación de Visual Basic. En el tipo de proyecto se incluyen todos los archivos de plantilla que vamos a necesitar, sin necesidad de agregar nada más.

1. Abra Visual Studio 2017.

2. En la barra de menús superior, seleccione **Archivo** > **Nuevo** > **Proyecto...**

3. En el panel de la izquierda del cuadro de diálogo **Nuevo proyecto**, expanda **Visual Basic** y seleccione **.NET Core**. En el panel central, elija **Aplicación de consola (.NET Core)**. Luego, asigne el nombre *HelloWorld* al proyecto.

   ![Plantilla de proyecto Aplicación de consola (.NET Core) en el cuadro de diálogo Nuevo proyecto en el IDE de Visual Studio](../ide/media/new-project-vb-dotnetcore-helloworld-console-app.png)

     Si no ve la plantilla de proyecto **Aplicación de consola (.NET Core)**, haga clic en el vínculo **Abrir el instalador de Visual Studio** en el panel izquierdo del cuadro de diálogo **Nuevo proyecto**.

   ![Clic en el vínculo Abrir el instalador de Visual Studio del cuadro de diálogo Nuevo proyecto](../ide/media/vb-open-visual-studio-installer-hello-world.png)

     Se iniciará el Instalador de Visual Studio. Elija la carga de trabajo **Desarrollo multiplataforma de .NET Core** y, después, elija **Modificar**.

     ![Carga de trabajo de desarrollo multiplataforma de .NET Core en el Instalador de Visual Studio](../ide/media/dot-net-core-xplat-dev-workload.png)

## <a name="create-the-application"></a>Crear la aplicación
Tras seleccionar la plantilla de proyecto de Visual Basic y asignar un nombre al proyecto, Visual Studio crea automáticamente una sencilla aplicación llamada "Hello World". Llama al método <xref:System.Console.WriteLine%2A> para mostrar la cadena literal "Hola mundo" en la ventana de la consola.

![Visualización del código de Hello World predeterminado de la plantilla](../ide/media/vb-console-helloworld-template.png)

Si hace clic en el botón **HelloWorld** en el IDE, puede ejecutar el programa en modo de depuración.

  ![Clic en el botón Hello World para ejecutar el programa en modo de depuración](../ide/media/vb-console-hello-world-button.png)

Al hacerlo, la ventana de consola se mostrará un momento antes de cerrarse. Esto ocurre porque el método `Main` finaliza en cuanto se ejecuta su única instrucción, con lo cual la aplicación termina.

### <a name="add-some-code"></a>Agregar algo de código
Vamos a agregar código para pausar la aplicación y solicitar una entrada de usuario.

1. Agregue el código siguiente inmediatamente después de llamar al método <xref:System.Console.WriteLine%2A>:

   ```vb
   Console.Write("Press any key to continue...")
   Console.ReadKey(true)
   ```
   Esto hace que el programa se quede en pausa hasta que se presione una tecla.

2. En la barra de menús, seleccione **Compilar** > **Compilar solución**.

   De esta forma, el programa se compila en un lenguaje intermedio (IL) que se convierte en código binario mediante un compilador Just-In-Time (JIT).

## <a name="run-the-application"></a>Ejecutar la aplicación
1. Haga clic en el botón **HelloWorld** de la barra de herramientas.

   ![Clic en el botón Hello World para ejecutar el programa desde la barra de herramientas](../ide/media/vb-console-hello-world-button.png)

2. Presione cualquier tecla para cerrar la ventana de consola.

   ![Ventana de consola que muestra "Hello World" y "Press any key to continue"](../ide/media/vb-console-hello-world-press-any-key.png)

## <a name="next-steps"></a>Pasos siguientes
¡Enhorabuena por completar este tutorial de inicio rápido! Esperamos que haya aprendido un poco sobre Visual Basic y el IDE de Visual Studio. Para obtener más información, continúe con el tutorial siguiente.

> [!div class="nextstepaction"]
> [Introducción a Visual Basic en Visual Studio](tutorial-visual-basic-console.md)
