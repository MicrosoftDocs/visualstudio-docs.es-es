---
title: 'Tutorial: Depuración de código de C# y C++ (modo mixto)'
description: Aprenda a depurar una DLL nativa desde una aplicación .NET Core o .NET Framework con la depuración en modo mixto
ms.custom: seodec18
ms.date: 11/02/2018
ms.topic: tutorial
dev_langs:
- CSharp
- C++
helpviewer_keywords:
- mixed mode debugging
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
- cplusplus
ms.openlocfilehash: d1fefda9d8d639bf8d360bbd6b869b75b7dae903
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62847915"
---
# <a name="tutorial-debug-c-and-c-in-the-same-debugging-session"></a>Tutorial: Depuración de C# y C++ en la misma sesión de depuración

Visual Studio permite habilitar más de un tipo de depurador en una sesión de depuración, lo que se denomina depuración en modo mixto. En este tutorial, se ofrece información para depurar código administrado y nativo en una única sesión de depuración.

En él se muestra cómo depurar código nativo desde una aplicación administrada, además de cómo [depurar código administrado desde una aplicación nativa](../debugger/how-to-debug-in-mixed-mode.md). El depurador también admite otros tipos de depuración en modo mixto, como la depuración de [Python y código nativo](../python/debugging-mixed-mode-c-cpp-python-in-visual-studio.md), y el empleo del depurador de scripts en tipos de aplicaciones como ASP.NET.

En este tutorial va a:

> [!div class="checklist"]
> * Crear una DLL nativa simple
> * Crear una aplicación .NET Core o .NET Framework sencilla para llamar a la DLL
> * Configurar la depuración en modo mixto
> * Iniciar el depurador
> * Alcanzar un punto de interrupción en la aplicación administrada
> * Depurar paso a paso por instrucciones del código nativo

## <a name="prerequisites"></a>Requisitos previos

Debe tener instalado Visual Studio con las cargas de trabajo siguientes:
- **Desarrollo para el escritorio con C++**
- **Desarrollo de escritorio de .NET** o **Desarrollo multiplataforma de .NET Core**, en función del tipo de aplicación que quiera crear.

Si no tiene Visual Studio, vaya a la página de  [descargas de Visual Studio](https://visualstudio.microsoft.com/downloads/)  para instalarlo de forma gratuita.

Si tiene Visual Studio instalado, pero no las cargas de trabajo que necesita, seleccione **Abrir el instalador de Visual Studio** en el panel izquierdo del cuadro de diálogo **Nuevo proyecto** de Visual Studio. En el Instalador de Visual Studio, seleccione las cargas de trabajo necesarias y luego **Modificar**.

## <a name="create-a-simple-native-dll"></a>Crear una DLL nativa simple

**Para crear los archivos del proyecto de DLL:**

1. Abra Visual Studio y cree un proyecto.

    ::: moniker range=">=vs-2019"
    Presione **Esc** para cerrar la ventana de inicio. Presione **Ctrl + Q** para abrir el cuadro de búsqueda, escriba **Proyecto vacío**, elija **Plantillas** y luego, **Create new Empty Project project** (Crear proyecto vacío) para C++. En el cuadro de diálogo que se abre, elija **Crear**. Luego, escriba un nombre como **Mixed_Mode_Debugging** y haga clic en **Crear**.
    ::: moniker-end
    ::: moniker range="vs-2017"
    En la barra de menús superior, seleccione **Archivo** > **Nuevo** > **Proyecto**. En el panel izquierdo del cuadro de diálogo **Nuevo proyecto**, en **Visual C++**, elija **Otros** y luego, en el panel central, **Proyecto vacío**. Luego, escriba un nombre como **Mixed_Mode_Debugging** y haga clic en **Aceptar**.
    ::: moniker-end

    Si no ve la plantilla de proyecto **Proyecto vacío**, vaya a **Herramientas** > **Obtener herramientas y características…** y se abrirá el instalador de Visual Studio. Se iniciará el Instalador de Visual Studio. Seleccione la carga de trabajo **Desarrollo para el escritorio con C++** y, luego, elija **Modificar**.

    Visual Studio crea el proyecto.

1. En el cuadro de diálogo **Nuevo proyecto**, en **Visual C++**, seleccione **Otro** y luego **Proyecto vacío** en el panel central.

1. En el campo **Nombre**, escriba **Mixed_Mode_Debugging** y seleccione **Aceptar**.

   Visual Studio crea el proyecto vacío y lo muestra en el **Explorador de soluciones**.

1. En el **Explorador de soluciones**, seleccione **Archivos de código fuente** y luego **Proyecto** > **Agregar nuevo elemento**. O bien, haga clic con el botón derecho en **Archivos de código fuente** y seleccione **Agregar** > **Nuevo elemento**.

1. En el cuadro de diálogo **Nuevo elemento**, seleccione **Archivo C++ (.cpp)**. En el campo **Nombre**, escriba **Mixed_Mode.cpp** y seleccione **Agregar**.

    Visual Studio agrega el nuevo archivo de C++ al **Explorador de soluciones**.

1. Copie el siguiente código en *Mixed_Mode.cpp*:

    ```cpp
    #include "Mixed_Mode.h"
    ```

1. En el **Explorador de soluciones**, seleccione **Archivos de encabezado** y luego **Proyecto** > **Agregar nuevo elemento**. O bien, haga clic con el botón derecho en **Archivos de encabezado** y seleccione **Agregar** > **Nuevo elemento**.

1. En el cuadro de diálogo **Nuevo elemento**, seleccione **Archivo de encabezado (.h)**. En el campo **Nombre**, escriba **Mixed_Mode.h** y seleccione **Agregar**.

   Visual Studio agrega el nuevo archivo de encabezado al **Explorador de soluciones**.

1. Copie el siguiente código en *Mixed_Mode.h*:

    ```cpp
    #ifndef MIXED_MODE_MULTIPLY_HPP
    #define MIXED_MODE_MULTIPLY_HPP

    extern "C"
    {
      __declspec(dllexport) int __stdcall mixed_mode_multiply(int a, int b) {
        return a * b;
      }
    }
    #endif
    ```

1. Seleccione **Archivo** > **Guardar todo** o presione **Ctrl**+**Mayús**+**S** para guardar los archivos.

**Para configurar y compilar el proyecto de DLL:**

1. En la barra de herramientas de Visual Studio, seleccione la opción **Depurar** y la plataforma **x86** o **x64**. Si la aplicación que realiza la llamada va a ser .NET Core, que siempre se ejecuta en modo de 64 bits, seleccione **x64** como plataforma.

1. En el **Explorador de soluciones**, seleccione el nodo del proyecto **Mixed_Mode_Debugging** y el icono **Propiedades** o haga clic con el botón derecho en el nodo del proyecto y seleccione **Propiedades**.

1. En la parte superior del panel **Propiedades**, asegúrese de que **Configuración** esté establecido en **Activo (Depurar)** y **Plataforma** sea la misma que la establecida en la barra de herramientas: **x64** o **Win32** para la plataforma x86.

   > [!IMPORTANT]
   > Si cambia la plataforma de **x86** a **x64** o viceversa, debe volver a configurar las propiedades de la nueva plataforma.

1. En **Propiedades de configuración**, en el panel izquierdo, seleccione **Enlazador** > **Avanzadas** y, en la lista desplegable situada junto a **Ningún punto de entrada**, seleccione **No**. Si ha tenido que cambiar a **No**, seleccione **Aplicar**.

1. En **Propiedades de configuración**, seleccione **General** y, en la lista desplegable situada junto a **Tipo de configuración**, seleccione **Biblioteca dinámica (.dll)**. Seleccione **Aplicar** y luego **Aceptar**.

   ![Cambio a una DLL nativa](../debugger/media/mixed-mode-set-as-native-dll.png)

1. Seleccione el proyecto en el **Explorador de soluciones** y luego **Compilar** > **Compilar solución**, presione **F7**, o haga clic con el botón derecho en el proyecto y seleccione **Compilar**.

   El proyecto se debe compilar sin errores.

## <a name="create-a-simple-managed-app-to-call-the-dll"></a>Crear una aplicación administrada simple para llamar a la DLL

1. Abra Visual Studio y cree un nuevo proyecto.

    ::: moniker range=">=vs-2019"
    Presione **Esc** para cerrar la ventana de inicio. Presione **Ctrl + Q** para abrir el cuadro de búsqueda, escriba **consola**, elija **Plantillas** y luego, **Create new Console App (.NET Framework) project** (Crear proyecto de aplicación de consola [.NET Framework]) para C#. En el cuadro de diálogo que se abre, elija **Crear**.

    Luego, escriba un nombre como **Mixed_Mode_Calling_App** y haga clic en **Crear**.
    ::: moniker-end
    ::: moniker range="vs-2017"
    En la barra de menús superior, seleccione **Archivo** > **Nuevo** > **Proyecto**. En el panel izquierdo del cuadro de diálogo **Nuevo proyecto**, en **Visual C#**, elija **Escritorio de Windows** y luego, en el panel central, **Aplicación de consola (.NET Framework)** o **Aplicación de consola (.NET Core)**.

    Luego, escriba un nombre como **Mixed_Mode_Calling_App** y haga clic en **Aceptar**.
    ::: moniker-end

    Si no ve la plantilla de proyecto **Aplicación de consola**, vaya a **Herramientas** > **Obtener herramientas y características…** y se abrirá el instalador de Visual Studio. Elija la carga de trabajo **Desarrollo de escritorio de .NET** y, luego, seleccione **Modificar**.

    > [!NOTE]
    > Aunque también podría agregar el nuevo proyecto administrado a la solución existente de C++, al crear una nueva solución se admiten más escenarios de depuración.

   Visual Studio crea el proyecto vacío y lo muestra en el **Explorador de soluciones**.

1. Reemplace todo el código de *Program.cs* por el siguiente:

    ```csharp
    using System;
    using System.Runtime.InteropServices;

    namespace Mixed_Mode_Calling_App
    {
        public class Program
        {
            // Replace the file path shown here with the
            // file path on your computer. For .NET Core, the typical (default) path
            // for a 64-bit DLL might look like this:
            // C:\Users\username\source\repos\Mixed_Mode_Debugging\x64\Debug\Mixed_Mode_Debugging.dll
            // Here, we show a typical path for a DLL targeting the **x86** option.
            [DllImport(@"C:\Users\username\source\repos\Mixed_Mode_Debugging\Debug\Mixed_Mode_Debugging.dll", EntryPoint =
            "mixed_mode_multiply", CallingConvention = CallingConvention.StdCall)]
            public static extern int Multiply(int x, int y);
            public static void Main(string[] args)
            {
                int result = Multiply(7, 7);
                Console.WriteLine("The answer is {0}", result);
                Console.ReadKey();
            }
        }
    }
    ```

1. En el nuevo código, reemplace la ruta de acceso de archivo de `[DllImport]` por la ruta de acceso de archivo de *Mixed_Mode_Debugging.dll* que acaba de crear. Vea el comentario del código para obtener sugerencias. Asegúrese de reemplazar el marcador de posición *username*.

1. Seleccione **Archivo** > **Guardar Program.cs** o presione **Ctrl**+**S** para guardar el archivo.

## <a name="configure-mixed-mode-debugging"></a>Configurar la depuración en modo mixto

### <a name="to-configure-mixed-mode-debugging-for-a-net-framework-app"></a>Para configurar la depuración en modo mixto para una aplicación .NET Framework

1. En el **Explorador de soluciones**, seleccione el nodo del proyecto **Mixed_Mode_Calling_App** y el icono **Propiedades** o haga clic con el botón derecho en el nodo del proyecto y seleccione **Propiedades**.

1. Seleccione **Depurar** en el panel izquierdo, active la casilla **Habilitar depuración de código nativo** y cierre la página de propiedades para guardar los cambios.

    ![Habilitación de la depuración en modo mixto](../debugger/media/mixed-mode-enable-native-code-debugging.png)

### <a name="to-configure-mixed-mode-debugging-for-a-net-core-app"></a>Para configurar la depuración en modo mixto para una aplicación .NET Core

En la mayoría de las versiones de Visual Studio a partir de Visual Studio 2017, debe usar el archivo *launchSettings.json* en lugar de las propiedades del proyecto para habilitar la depuración en modo mixto para el código nativo de una aplicación .NET Core. Para realizar un seguimiento de las actualizaciones de la interfaz de usuario de esta característica, vea este [problema de GitHub](https://github.com/dotnet/project-system/issues/1125).

1. En el **Explorador de soluciones**, expanda **Propiedades** y abra el archivo *launchSettings.json*.

   >[!NOTE]
   >De forma predeterminada, *launchSettings.json* está en *C:\Users\username\source\repos\Mixed_Mode_Calling_App\Properties*. Si *launchSettings.json* no existe, seleccione el proyecto **Mixed_Mode_Calling_App** en el **Explorador de soluciones** y luego seleccione el icono **Propiedades** o haga clic con el botón derecho en el proyecto y seleccione **Propiedades**. Realice un cambio temporal en la pestaña **Depurar** y compile el proyecto. Esto crea un archivo *launchSettings.json*. Revierta el cambio realizado en la pestaña **Depurar**.

1. En el archivo *lauchsettings.json*, agregue la siguiente línea:

    ```csharp
    "nativeDebugging": true
    ```

    El código completo tiene un aspecto similar al ejemplo siguiente:

    ```csharp
    {
      "profiles": {
        "Mixed_Mode_Calling_App": {
          "commandName": "Project",
          "nativeDebugging": true
        }
      }
    }
    ```

## <a name="set-a-breakpoint-and-start-debugging"></a>Establecer un punto de interrupción e iniciar la depuración

1. En el proyecto de C#, abra *Program.cs*. Para establecer un punto de interrupción en la siguiente línea de código, haga clic en el margen izquierdo, seleccione la línea y presione **F9**, o bien haga clic con el botón derecho en la línea y seleccione **Punto de interrupción** > **Insertar punto de interrupción**.

    ```csharp
    int result = Multiply(7, 7);
    ```

    En el margen izquierdo donde ha establecido el punto de interrupción aparece un círculo rojo.

1. Presione **F5**, seleccione la flecha verde de la barra de herramientas de Visual Studio, o seleccione **Depurar** > **Iniciar depuración** para iniciar la depuración.

   El depurador se detiene en el punto de interrupción establecido. Una flecha amarilla indica dónde se ha detenido el depurador.

## <a name="step-in-and-out-of-native-code"></a>Depurar paso a paso por instrucciones del código nativo

1. Mientras la depuración está detenida en la aplicación administrada, presione **F11**, o bien seleccione **Depurar** > **Depurar paso a paso por instrucciones**.

   Se abre el archivo de encabezado nativo *Mixed_Mode.h* y se ve la flecha amarilla donde se ha detenido el depurador.

   ![Depuración paso a paso por instrucciones del código nativo](../debugger/media/mixed-mode-step-into-native-code.png)

1. Ahora es posible establecer y alcanzar puntos de interrupción e inspeccionar variables en el código nativo o administrado.

   - Mantenga el puntero sobre las variables del código fuente para ver sus valores.

   - Examine las variables y sus valores en las ventanas **Automático** y **Locales**.

   - Mientras el depurador está detenido, también puede usar las ventanas **Inspección** y **Pila de llamadas**.

1. Presione **F11** de nuevo para que el depurador avance una línea.

1. Presione **Mayús**+**F11** o seleccione **Depurar** > **Paso a paso para salir** para seguir ejecutando y volver a detener en la aplicación administrada.

1. Presione **F5** o seleccione la flecha verde para seguir depurando la aplicación.

¡Enhorabuena! Ha completado el tutorial sobre la depuración en modo mixto.

## <a name="next-step"></a>Paso siguiente

En este tutorial, ha aprendido a depurar código nativo desde una aplicación administrada al habilitar la depuración en modo mixto. Para obtener información general sobre otras características del depurador, vea:

> [!div class="nextstepaction"]
> [Primer vistazo al depurador](../debugger/debugger-feature-tour.md)
