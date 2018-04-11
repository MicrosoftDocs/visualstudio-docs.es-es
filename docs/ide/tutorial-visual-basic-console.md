---
title: Introducción a Visual Basic en Visual Studio | Microsoft Docs
ms.custom: ''
ms.date: 12/08/2017
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-acquisition
ms.tgt_pltfrm: ''
ms.topic: tutorial
ms.devlang: vb
author: TerryGLee
ms.author: tglee
manager: douge
dev_langs:
- vb
ms.workload:
- multiple
ms.openlocfilehash: e1818c12090737511b6460145b994bf58e6ad9ab
ms.sourcegitcommit: a0a49cceb0fdc1465ddf76d131c6575018b628b8
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/05/2018
---
# <a name="getting-started-with-visual-basic-in-visual-studio"></a>Introducción a Visual Basic en Visual Studio
En este tutorial para Visual Basic (VB), podrá usar Visual Studio para crear y ejecutar algunas aplicaciones de consola diferentes y explorar algunas características del [entorno de desarrollo integrado (IDE)](visual-studio-ide.md) de Visual Studio mientras lo hace.

Si todavía no ha instalado Visual Studio, vaya a la página de [descargas de Visual Studio](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs) para instalarlo de forma gratuita.

## <a name="before-you-begin"></a>Antes de empezar
Esta es una sección rápida de P+F para presentar algunos conceptos clave.
### <a name="what-is-visual-basic"></a>¿Qué es Visual Basic?
Visual Basic es un lenguaje de programación con seguridad de tipos diseñado para ser fácil de aprender. Se deriva de BASIC, que significa "Código simbólico de instrucciones de propósito general para principiantes".
### <a name="what-is-visual-studio"></a>¿Qué es Visual Studio?
Visual Studio es un conjunto de desarrollo integrado de herramientas de productividad para desarrolladores. Considérelo como un programa que se puede usar para crear programas y aplicaciones.  
### <a name="what-is-a-console-app"></a>¿Qué es una aplicación de consola?
Una aplicación de consola toma la entrada y muestra la salida en una ventana de línea de comandos, también conocida como consola.
### <a name="what-is-net-core"></a>¿Qué es .NET Core?
.NET core es el siguiente paso evolutivo de .NET Framework. Donde .NET Framework permitía compartir código entre lenguajes de programación, .NET Core agrega la capacidad de compartir código entre plataformas. Y todavía mejor, es de código abierto. (.NET Framework y .NET Core incluyen bibliotecas de funciones predeterminadas, así como un Common Language Runtime (CLR), que actúa como una máquina virtual en el que se ejecuta el código).

## <a name="start-developing"></a>Empezar a desarrollar
¿Listo para empezar a desarrollar? Vamos allá.

### <a name="create-a-project"></a>Crear un proyecto
En primer lugar, se creará un proyecto de aplicación de Visual Basic. En el tipo de proyecto se incluyen todos los archivos de plantilla que vamos a necesitar, sin necesidad de agregar nada más.

1. Abra Visual Studio 2017.

2. En la barra de menús superior, seleccione **Archivo** > **Nuevo** > **Proyecto...**

3. En el panel de la izquierda del cuadro de diálogo **Nuevo proyecto**, expanda **Visual Basic** y seleccione **.NET Core**. En el panel central, elija **Aplicación de consola (.NET Core)**. Después, asigne el nombre *HelloWorld* al archivo.  

   ![Plantilla de proyecto Aplicación de consola (.NET Core) en el cuadro de diálogo Nuevo proyecto en el IDE de Visual Studio](../ide/media/new-project-vb-dotnetcore-whatisyourname-console-app.png)

#### <a name="add-a-workgroup-optional"></a>Agregar un grupo de trabajo (opcional)
Si no ve la plantilla de proyecto **Aplicación de consola (.NET Core)**, puede obtenerla si agrega la carga de trabajo **Desarrollo multiplataforma de .NET Core**. Puede agregar esta carga de trabajo de una de las dos formas siguientes, según las actualizaciones de Visual Studio 2017 que estén instaladas en el equipo.

##### <a name="option-1-use-the-new-project-dialog-box"></a>Opción 1: Usar el cuadro de diálogo Nuevo proyecto
1. Haga clic en el vínculo **Abrir el instalador de Visual Studio** en el panel de la izquierda del cuadro de diálogo **Nuevo proyecto**.

  ![Clic en el vínculo Abrir el instalador de Visual Studio del cuadro de diálogo Nuevo proyecto](../ide/media/vs-open-visual-studio-installer-generic.png)

2. Se iniciará el Instalador de Visual Studio. Elija la carga de trabajo **Desarrollo multiplataforma de .NET Core** y, después, elija **Modificar**.

   ![Carga de trabajo Desarrollo multiplataforma de .NET Core en el instalador de Visual Studio](../ide/media/dot-net-core-xplat-dev-workload.png)

##### <a name="option-2-use-the-tools-menu-bar"></a>Opción 2: Usar la barra del menú Herramientas
1. Cancele para salir del cuadro de diálogo **Nuevo proyecto** y, en la barra de menús superior, seleccione **Herramientas** > **Obtener herramientas y características...**.

2. Se iniciará el Instalador de Visual Studio. Elija la carga de trabajo **Desarrollo multiplataforma de .NET Core** y, después, elija **Modificar**.   

## <a name="create-a-what-is-your-name-application"></a>Crear una aplicación "¿Cómo te llamas?"
Vamos a crear una aplicación que le solicita el nombre y, después, lo muestra junto con la fecha y hora. Esta es la manera de hacerlo:

1. Si todavía no está abierto, abra el proyecto *WhatIsYourName*.

2. Escriba el código de Visual Basic siguiente inmediatamente después del corchete de apertura que sigue a la línea `Sub Main(args As String())` y antes de la línea `End Sub`:

     ```vb
     Console.WriteLine(vbCrLf + "What is your name? ")
     Dim name = Console.ReadLine()
     Dim currentDate = DateTime.Now
     Console.WriteLine($"{vbCrLf}Hello, {name}, on {currentDate:d} at {currentDate:t}")
     Console.Write(vbCrLf + "Press any key to exit... ")
     Console.ReadKey(True)
    ```

    Este código reemplaza las instrucciones <xref:System.Console.WriteLine%2A>, <xref:System.Console.Write%2A> y <xref:System.Console.ReadKey%2A> existentes.

 ![Ventana de código en la que se muestra el código de Cómo te llamas](../ide/media/vb-codewindow-what-name.png)

3. Cuando se abra la ventana de consola, escriba su nombre. La ventana de consola debe ser similar a la captura de pantalla siguiente:

   ![Ventana de consola en la que se muestra What Is Your Name (Cómo te llamas), la fecha y hora, y el mensaje Press any key to continue (Presione cualquier tecla para continuar)](../ide/media/vb-console-what-name.png)

5. Presione cualquier tecla para cerrar la ventana de consola.

## <a name="create-a-calculate-this-application"></a>Crear una aplicación "Calcular esto"
1. Abra Visual Studio 2017 y, después, en la barra de menús superior, seleccione **Archivo** > **Nuevo** > **Proyecto...**.

2. En el panel de la izquierda del cuadro de diálogo **Nuevo proyecto**, expanda **Visual Basic** y seleccione **.NET Core**. En el panel central, elija **Aplicación de consola (.NET Core)**. Después, asigne el nombre *CalculateThis* al archivo.  

3. Escriba el código siguiente entre las líneas `Module Program` y `End Module`:

   ```vb
   Public num1 As Integer
   Public num2 As Integer
   Public answer As Integer
   Sub Main()
       Console.WriteLine("Type a number and press Enter")
       num1 = Console.ReadLine()
       Console.WriteLine("Type another number to add to it and press Enter")
       num2 = Console.ReadLine()
       answer = num1 + num2
       Console.WriteLine("The answer is " & answer)
       Console.ReadLine()
   End Sub
   ```

  La ventana de código debería ser similar a la captura de pantalla siguiente:

   ![Ventana de código en la que se muestra el código de Calcular esto](../ide/media/vb-codewindow-calculate-this.png)

4. Haga clic en **CalculateThis** para ejecutar el programa. La ventana de consola debe ser similar a la captura de pantalla siguiente:       

    ![Ventana de consola en la que se muestra la aplicación CaluculateThis, que incluye mensajes sobre las acciones que se deben realizar.](../ide/media/vb-console-calculate-this.png)

## <a name="next-steps"></a>Pasos siguientes
Enhorabuena por completar este tutorial. Para obtener más información sobre Visual Basic y el IDE de Visual Studio, vea las páginas siguientes.

* [Guía de Visual Basic](/dotnet/visual-basic/index)
* [Novedades de Visual Basic](/dotnet/visual-basic/getting-started/whats-new)
* [Archivos de código de IntelliSense para Visual Basic](visual-basic-specific-intellisense.md)
* [Referencia del lenguaje Visual Basic](/dotnet/visual-basic/language-reference/index)
* Curso en vídeo [Aspectos básicos de Visual Basic para principiantes sin experiencia](https://mva.microsoft.com/en-us/training-courses/visual-basic-fundamentals-for-absolute-beginners-16507)
