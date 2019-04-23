---
title: 'Tutorial: Introducción a Visual Basic'
description: Aprenda a crear aplicaciones de consola de Visual Basic en Visual Studio mediante un procedimiento paso a paso.
ms.custom: seodec18, get-started
ms.date: 03/23/2019
ms.technology: vs-ide-general
ms.prod: visual-studio-windows
ms.topic: tutorial
ms.devlang: vb
author: TerryGLee
ms.author: tglee
manager: jillfra
dev_langs:
- vb
ms.workload:
- multiple
ms.openlocfilehash: f394ea2775eede3424e4d6995a8e2065c5d986ef
ms.sourcegitcommit: 509fc3a324b7748f96a072d0023572f8a645bffc
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/02/2019
ms.locfileid: "58857598"
---
# <a name="tutorial-get-started-with-visual-basic-in-visual-studio"></a>Tutorial: Introducción a Visual Basic en Visual Studio

En este tutorial para Visual Basic (VB), podrá usar Visual Studio para crear y ejecutar algunas aplicaciones de consola diferentes y explorar algunas características del [entorno de desarrollo integrado (IDE)](visual-studio-ide.md) de Visual Studio mientras lo hace.

::: moniker range="vs-2017"

Si todavía no ha instalado Visual Studio, vaya a la página de [descargas de Visual Studio](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) para instalarlo de forma gratuita.

::: moniker-end

::: moniker range="vs-2019"

Si todavía no ha instalado Visual Studio, vaya a la página de [descargas de Visual Studio](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) para instalarlo de forma gratuita.

::: moniker-end

## <a name="create-a-project"></a>Crear un proyecto

En primer lugar, se creará un proyecto de aplicación de Visual Basic. En el tipo de proyecto se incluyen todos los archivos de plantilla que vamos a necesitar, sin necesidad de agregar nada más.

::: moniker range="vs-2017"

1. Abra Visual Studio 2017.

2. En la barra de menús superior, elija **Archivo** > **Nuevo** > **Proyecto**.

3. En el panel de la izquierda del cuadro de diálogo **Nuevo proyecto**, expanda **Visual Basic** y seleccione **.NET Core**. En el panel central, elija **Aplicación de consola (.NET Core)**. Después, asigne el nombre *HelloWorld* al archivo.

   ![Plantilla de proyecto Aplicación de consola (.NET Core) en el cuadro de diálogo Nuevo proyecto en el IDE de Visual Studio](media/new-project-vb-dotnetcore-whatisyourname-console-app.png)

### <a name="add-a-workload-optional"></a>Agregar una carga de trabajo (opcional)

Si no ve la plantilla de proyecto **Aplicación de consola (.NET Core)**, puede obtenerla si agrega la carga de trabajo **Desarrollo multiplataforma de .NET Core**. Puede agregar esta carga de trabajo de una de las dos formas siguientes, según las actualizaciones de Visual Studio 2017 que estén instaladas en el equipo.

#### <a name="option-1-use-the-new-project-dialog-box"></a>Opción 1: Uso del cuadro de diálogo Nuevo proyecto

1. Haga clic en el vínculo **Abrir el instalador de Visual Studio** en el panel de la izquierda del cuadro de diálogo **Nuevo proyecto**.

   ![Clic en el vínculo Abrir el instalador de Visual Studio del cuadro de diálogo Nuevo proyecto](../media/vs-open-visual-studio-installer-generic.png)

1. Se iniciará el Instalador de Visual Studio. Elija la carga de trabajo **Desarrollo multiplataforma de .NET Core** y, después, elija **Modificar**.

   ![Carga de trabajo Desarrollo multiplataforma de .NET Core en el instalador de Visual Studio](../media/tutorial-aspnet-workload.png)

#### <a name="option-2-use-the-tools-menu-bar"></a>Opción 2: Uso de la barra del menú Herramientas

1. Cancele para salir del cuadro de diálogo **Nuevo proyecto** y, en la barra de menús superior, seleccione **Herramientas**>**Obtener herramientas y características...**

1. Se iniciará el Instalador de Visual Studio. Elija la carga de trabajo **Desarrollo multiplataforma de .NET Core** y, después, elija **Modificar**.

::: moniker-end

::: moniker range="vs-2019"

> [!NOTE]
> Algunas de las capturas de pantalla de este tutorial usan el tema oscuro. Si no está usando el tema oscuro pero le gustaría hacerlo, vea la página [Guía de inicio rápido: personalizar el IDE y el editor de Visual Studio](../../ide/quickstart-personalize-the-ide.md) para obtener información sobre cómo hacerlo.

1. Abra Visual Studio 2019.

1. En la ventana de inicio, elija **Crear un proyecto nuevo**.

   ![Visualización de la ventana "Crear un proyecto"](../../get-started/media/vs-2019/create-new-project-dark-theme.png)

1. En el cuadro de búsqueda de la ventana **Crear un proyecto**, escriba *consola*. Seguidamente, elija **Visual Basic** en la lista de lenguajes y luego, **Windows** en la lista de plataformas. 

   Después de aplicar los filtros de lenguaje y plataforma, elija la plantilla **Aplicación de consola (.NET Core)** y luego, **Siguiente**.

   ![Elija la plantilla Visual Basic para la Aplicación de consola (.NET Framework).](./media/vs-2019/vb-create-new-project-search-console-net-core-filtered.png)

   > [!NOTE]
   > Si no ve la plantilla **Aplicación de consola (.NET Core)**, puede instalarla desde la ventana **Crear un proyecto**. En el mensaje **¿No encuentra lo que busca?**, elija el vínculo **Instalar más herramientas y características**.
   >
   > ![Vínculo "Instalar más herramientas y características" del mensaje "¿No encuentra lo que busca?" que aparece en la ventana "Crear proyecto"](../../get-started/media/vs-2019/not-finding-what-looking-for.png) 
   > 
   > Luego, en el Instalador de Visual Studio, elija la carga de trabajo **Desarrollo multiplataforma de .NET Core**.
   >
   > ![Carga de trabajo Desarrollo multiplataforma de .NET Core en el instalador de Visual Studio](../../get-started/media/dot-net-core-xplat-dev-workload.png)
   >
   > Después, elija el botón **Modificar** en el Instalador de Visual Studio. Es posible que se le pida que guarde su trabajo; si es así, hágalo. Seguidamente, elija **Continuar** para instalar la carga de trabajo. Luego, vuelva al paso 2 de este procedimiento "[Crear un proyecto](#create-a-project)".

1. En la ventana **Configurar el nuevo proyecto**, escriba *WhatIsYourName* en el cuadro **Nombre del proyecto**. Luego, elija **Crear**.

   ![En la ventana "Configurar el nuevo proyecto", asigne al proyecto el nombre "WhatIsYourName".](./media/vs-2019/vb-name-your-project-whatname.png)

   Visual Studio se abre en el nuevo proyecto.

::: moniker-end

## <a name="create-a-what-is-your-name-application"></a>Crear una aplicación "¿Cómo te llamas?"

Vamos a crear una aplicación que le solicita el nombre y, después, lo muestra junto con la fecha y hora. Esta es la manera de hacerlo:

 ::: moniker range="vs-2017"

1. Si todavía no está abierto, abra el proyecto *WhatIsYourName*.

1. Escriba el código de Visual Basic siguiente inmediatamente después del corchete de apertura que sigue a la línea `Sub Main(args As String())` y antes de la línea `End Sub`:

     ```vb
     Console.WriteLine(vbCrLf + "What is your name? ")
     Dim name = Console.ReadLine()
     Dim currentDate = DateTime.Now
     Console.WriteLine($"{vbCrLf}Hello, {name}, on {currentDate:d} at {currentDate:t}")
     Console.Write(vbCrLf + "Press any key to exit... ")
     Console.ReadKey(True)
    ```

    Este código reemplaza las instrucciones <xref:System.Console.WriteLine%2A>, <xref:System.Console.Write%2A> y <xref:System.Console.ReadKey%2A> existentes.

   ![Ventana de código en la que se muestra el código de Cómo te llamas](./media/vs-2019/vb-codewindow-what-name-dark.png)

1. Cuando se abra la ventana de consola, escriba su nombre. La ventana de consola debe ser similar a la captura de pantalla siguiente:

   ![Ventana de consola en la que se muestra What Is Your Name (Cómo te llamas), la fecha y hora, y el mensaje Press any key to continue (Presione cualquier tecla para continuar)](media/vb-console-what-name.png)

1. Presione cualquier tecla para cerrar la ventana de consola.

::: moniker-end

::: moniker range="vs-2019"

1. En el proyecto *WhatIsYourName*, escriba el código de Visual Basic siguiente inmediatamente después del corchete de apertura que sigue a la línea `Sub Main(args As String())` y antes de la línea `End Sub`:

     ```vb
     Console.WriteLine(vbCrLf + "What is your name? ")
     Dim name = Console.ReadLine()
     Dim currentDate = DateTime.Now
     Console.WriteLine($"{vbCrLf}Hello, {name}, on {currentDate:d} at {currentDate:t}")
     Console.Write(vbCrLf + "Press any key to exit... ")
     Console.ReadKey(True)
    ```

    Este código reemplaza las instrucciones <xref:System.Console.WriteLine%2A>, <xref:System.Console.Write%2A> y <xref:System.Console.ReadKey%2A> existentes.

   ![Ventana de código en la que se muestra el código de Cómo te llamas](./media/vs-2019/vb-codewindow-what-name-dark.png)

1. Cuando se abra la ventana de consola, escriba su nombre. La ventana de consola debe ser similar a la captura de pantalla siguiente:

   ![Ventana de consola en la que se muestra What Is Your Name (Cómo te llamas), la fecha y hora, y el mensaje Press any key to continue (Presione cualquier tecla para continuar)](media/vb-console-what-name.png)

1. Presione cualquier tecla para cerrar la ventana de consola.

 ::: moniker-end

## <a name="create-a-calculate-this-application"></a>Crear una aplicación "Calcular esto"

::: moniker range="vs-2017"

1. Abra Visual Studio 2017 y, en la barra de menús superior, seleccione **Archivo**>**Nuevo**>**Proyecto**.

1. En el panel de la izquierda del cuadro de diálogo **Nuevo proyecto**, expanda **Visual Basic** y seleccione **.NET Core**. En el panel central, elija **Aplicación de consola (.NET Core)**. Después, asigne el nombre *CalculateThis* al archivo.

1. Escriba el código siguiente entre las líneas `Module Program` y `End Module`:

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

   ![Ventana de código en la que se muestra el código de CalculateThis](media/vb-codewindow-calculate-this.png)

1. Haga clic en **CalculateThis** para ejecutar el programa. La ventana de consola debe ser similar a la captura de pantalla siguiente:

    ![Ventana de consola en la que se muestra la aplicación CalculateThis, que incluye mensajes sobre las acciones que se deben realizar.](media/vb-console-calculate-this.png)

::: moniker-end 

::: moniker range="vs-2019"

1. En la ventana de inicio, elija **Crear un proyecto nuevo**. 

1. En el cuadro de búsqueda de la ventana **Crear un proyecto**, escriba *consola*. Seguidamente, elija **Visual Basic** en la lista de lenguajes y luego, **Windows** en la lista de plataformas. 

1. Después de aplicar los filtros de lenguaje y plataforma, elija la plantilla **Aplicación de consola (.NET Core)** y luego, **Siguiente**.

   Luego, en la ventana **Configurar el nuevo proyecto**, escriba *WhatIsYourName* en el cuadro **Nombre del proyecto**. Seguidamente, elija **Crear**.

1. Escriba el código siguiente entre las líneas `Module Program` y `End Module`:

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

   ![Ventana de código en la que se muestra el código de CalculateThis](media/vb-codewindow-calculate-this.png)

1. Haga clic en **CalculateThis** para ejecutar el programa. La ventana de consola debe ser similar a la captura de pantalla siguiente:

    ![Ventana de consola en la que se muestra la aplicación CalculateThis, que incluye mensajes sobre las acciones que se deben realizar.](media/vb-console-calculate-this.png)

::: moniker-end

## <a name="quick-answers-faq"></a>Respuestas rápidas a preguntas frecuentes

Esta es una sección rápida de P+F para destacar algunos conceptos clave.

### <a name="what-is-visual-basic"></a>¿Qué es Visual Basic?

Visual Basic es un lenguaje de programación con seguridad de tipos diseñado para ser fácil de aprender. Se deriva de BASIC, que significa "Código simbólico de instrucciones de propósito general para principiantes".

### <a name="what-is-visual-studio"></a>¿Qué es Visual Studio?

Visual Studio es un conjunto de desarrollo integrado de herramientas de productividad para desarrolladores. Considérelo como un programa que se puede usar para crear programas y aplicaciones.

### <a name="what-is-a-console-app"></a>¿Qué es una aplicación de consola?

Una aplicación de consola toma la entrada y muestra la salida en una ventana de línea de comandos, también conocida como consola.

### <a name="what-is-net-core"></a>¿Qué es .NET Core?

.NET core es el siguiente paso evolutivo de .NET Framework. Donde .NET Framework permitía compartir código entre lenguajes de programación, .NET Core agrega la capacidad de compartir código entre plataformas. Y todavía mejor, es de código abierto. (.NET Framework y .NET Core incluyen bibliotecas de funciones predeterminadas, así como un Common Language Runtime (CLR), que actúa como una máquina virtual en el que se ejecuta el código).

## <a name="next-steps"></a>Pasos siguientes

Enhorabuena por completar este tutorial. Para más información, continúe con el tutorial siguiente.

> [!div class="nextstepaction"]
> [Creación de una biblioteca con Visual Basic y el SDK de .NET Core en Visual Studio](/dotnet/core/tutorials/vb-library-with-visual-studio)

## <a name="see-also"></a>Vea también

* [Tutoriales sobre el lenguaje Visual Basic](/dotnet/visual-basic/walkthroughs)
* [Referencia del lenguaje Visual Basic](/dotnet/visual-basic/language-reference/index)
* [Archivos de código de IntelliSense para Visual Basic](../../ide/visual-basic-specific-intellisense.md)
