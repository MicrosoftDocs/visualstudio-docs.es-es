---
title: 'Tutorial: Depurar código administrado y nativo | Documentos de Microsoft'
description: Obtenga información acerca de cómo depurar un archivo DLL nativo desde una aplicación .NET Core o .NET Framework
ms.custom: ''
ms.date: 04/27/2018
ms.technology: vs-ide-debug
ms.topic: tutorial
dev_langs:
- CSharp
- C++
helpviewer_keywords:
- mixed mode debugging
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- dotnet
- cplusplus
ms.openlocfilehash: 548b86406ba36a6f46a2dfb3d4d894b5621c298c
ms.sourcegitcommit: d1824ab926ebbc4a8057163e0edeaf35cec57433
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/24/2018
---
# <a name="tutorial-debug-managed-and-native-code-in-visual-studio"></a>Tutorial: Depurar código nativo y administrado en Visual Studio

Visual Studio permite habilitar a más de un tipo de depurador durante la depuración, que se denomina depuración en modo mixto. En este tutorial, establezca las opciones para depurar código nativo y administrado en una sola sesión de depuración. Este tutorial muestra cómo depurar código nativo desde una aplicación administrada, pero también puede hacer lo contrario, y [depurar código administrado desde una aplicación nativa](../debugger/how-to-debug-in-mixed-mode.md). El depurador también admite otros tipos de depuración en modo mixto, por ejemplo la depuración [Python y código nativo](../python/debugging-mixed-mode-c-cpp-python-in-visual-studio.md) y utilizar el depurador de script en tipos de aplicaciones como ASP.NET.

En este tutorial va a:

> [!div class="checklist"]
> * Crear un archivo DLL nativo simple
> * Crear una aplicación sencilla de .NET Core o .NET Framework para llamar a la DLL
> * Iniciar el depurador
> * Alcanza un punto de interrupción en la aplicación administrada
> * Ir a código nativo

## <a name="prerequisites"></a>Requisitos previos

* Debe tener instalado Visual Studio y la **el desarrollo de escritorio con C++** carga de trabajo.

    Si todavía no tiene instalado Visual Studio, puede descargarlo de forma gratuita en [esta página](http://www.visualstudio.com).

    Si necesita instalar la carga de trabajo pero ya tiene Visual Studio, haga clic en el vínculo **Abrir el instalador de Visual Studio** en el panel izquierdo del cuadro de diálogo **Nuevo proyecto**. Se iniciará el Instalador de Visual Studio. Elija la carga de trabajo **Desarrollo de Node.js** y, después, haga clic en **Modificar**.

* También debe haber el **desarrollo de escritorio de .NET** carga de trabajo o la **.NET Core cross desarrollo multiplataforma** instalado la carga de trabajo, según el tipo de aplicación a la que desea crear.

## <a name="create-a-simple-native-dll"></a>Crear un archivo DLL nativo simple

1. En Visual Studio, elija **archivo** > **New** > **proyecto**.

1. En el **nuevo proyecto** diálogo cuadro, elija **Visual C++**, **General** desde la sección de plantillas instaladas y, a continuación, en el panel central, seleccione **proyecto vacío** .

1. En el **nombre** , escriba **depuración de modo mixto** y haga clic en **Aceptar**.

    Visual Studio crea el proyecto vacío, que aparece en el Explorador de soluciones en el panel derecho.

1. En el Explorador de soluciones, haga clic en el **archivos de código fuente** nodo en C++ de proyecto y, a continuación, elija **agregar** > **nuevo elemento**y, a continuación, seleccione **C++ archivo (.cpp)**. Asigne al archivo el nombre **Mixed Mode.cpp**y elija **agregar**.

    Visual Studio agrega el nuevo archivo de C++.

1. Copie el código siguiente en *Mode.cpp Mixed*:

    ```cpp
    #include "Mixed_Mode.h"
    ```
1. En el Explorador de soluciones, haga clic en el **archivos de encabezado** nodo en C++ de proyecto y, a continuación, elija **agregar** > **nuevo elemento**y, a continuación, seleccione  **Archivo de encabezado (. h)**. Asigne al archivo el nombre **Mixed Mode.h**y elija **agregar**.

    Visual Studio agrega el nuevo archivo de encabezado.

1. Copie el código siguiente en *Mode.h Mixed*:

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

1. En la barra de herramientas de depuración, seleccione un **depurar** configuración y **cualquier CPU** como la plataforma, o, para .NET Core, seleccione **x64** como la plataforma.

    > [!NOTE]
    > En .NET Core, elija **x64** como la plataforma. .NET core siempre se ejecuta en modo de 64 bits para que esto es necesario.

1. En el Explorador de soluciones, haga clic en el nodo del proyecto (**depuración de modo mixto**) y elija **propiedades**.

1. En el **propiedades** página, elija **propiedades de configuración** > **vinculador** > **avanzadas**, y a continuación, en la **ningún punto de entrada** lista desplegable, seleccione **NO**. A continuación, aplicar la configuración.

1. En el **propiedades** página, elija **propiedades de configuración** > **General**y, a continuación, seleccione **biblioteca dinámica (.dll)** desde el **tipo de configuración** campo. A continuación, aplicar la configuración.

    ![Cambiar a un archivo DLL nativo](../debugger/media/mixed-mode-set-as-native-dll.png)

1. Haga clic en el proyecto y elija **depurar** > **generar**.

    El proyecto se debe compilar sin errores.

## <a name="create-a-simple-net-framework-or-net-core-app-to-call-the-dll"></a>Crear una aplicación de .NET Framework o .NET Core sencilla para llamar a la DLL

1. En Visual Studio, elija **archivo** > **New** > **proyecto**.

1. Elija una plantilla para el código de aplicación.

    Para .NET Framework, en el **nuevo proyecto** diálogo cuadro, elija **Visual C#**, **escritorio clásico de Windows** desde la sección de plantillas instaladas y, a continuación, en el panel central Seleccione **aplicación de consola (.NET Framework)**.

    Para .NET Core, en la **nuevo proyecto** diálogo cuadro, elija **Visual C#**, **.NET Core** desde la sección de plantillas instaladas y, a continuación, en el panel central, seleccione  **(.NET Core) de la aplicación de consola**.

1. En el **nombre** , escriba **Mixed_Mode_Calling_App** y haga clic en **Aceptar**.

    Visual Studio crea el proyecto de consola, que aparece en el Explorador de soluciones en el panel derecho.

1. En *Program.cs*, reemplace el código predeterminado por el código siguiente:

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
            // C:\Users\username\source\repos\Mixed-Mode-Debugging\x64\Debug\Mixed-Mode-Debugging.dll
            // Here, we show a typical path for a DLL targeting the **Any CPU** option.
            [DllImport(@"C:\Users\username\source\repos\Mixed-Mode-Debugging\Debug\Mixed-Mode-Debugging.dll", EntryPoint =
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

## <a name="configure-mixed-mode-debugging-net-framework"></a>Configurar la depuración (.NET Framework) en modo mixto

1. En el Explorador de soluciones, haga clic en los recursos administrados **Mixed_Mode_Calling_App** del proyecto y elija **establecer como proyecto de inicio**.

1. Haga clic en los recursos administrados **Mixed_Mode_Calling_App** del proyecto y, a continuación, elija **propiedades**y, a continuación, elija **depurar** en el panel izquierdo. Seleccione **habilitar la depuración de código nativo**y, a continuación, cierre la página de propiedades para guardar los cambios.

    ![Habilitar la depuración en modo mixto](../debugger/media/mixed-mode-enable-native-code-debugging.png)

## <a name="configure-mixed-mode-debugging-net-core"></a>Configurar la depuración (.NET Core) en modo mixto

En la mayoría de las versiones de Visual Studio de 2017, debe habilitar la depuración en modo mixto de código nativo en una aplicación de .NET Core con el *launchSettings.json* de archivos en lugar de la **propiedades** página. Para realizar el seguimiento de las actualizaciones de la interfaz de usuario para esta característica, consulte esta [problema de GitHub](https://github.com/dotnet/project-system/issues/1125).

1. Abra la *launchSettings.json* un archivo en el *propiedades* carpeta. De forma predeterminada, puede encontrar el archivo en esta ubicación.

    *C:\Users\<nombre de usuario > \source\repos\Mixed_Mode_Calling_App\Properties*

    Si el archivo no está presente, abra las propiedades del proyecto (haga clic en los recursos administrados **Mixed_Mode_Calling_App** de proyecto en el Explorador de soluciones y seleccione **propiedades**). Realiza un cambio temporal en el **depurar** pestaña y compilar el proyecto. Revertir los cambios realizados.

1. En el *lauchsettings.json* de archivos, agregue la siguiente propiedad:

    ```
    "nativeDebugging": true
    ```
    
    Por lo tanto, por ejemplo, el archivo podría ser similar al siguiente:
    
    ```
    {
      "profiles": {
        "Mixed_Mode_Calling_App": {
          "commandName": "Project",
          "nativeDebugging": true
        }
      }
    }
    ```

## <a name="set-a-breakpoint-and-start-the-debugger"></a>Establecer un punto de interrupción e iniciar el depurador

1. En el proyecto de C#, abra *Program.cs* y establecer un punto de interrupción en la siguiente línea de código, haga clic en el margen izquierdo:

    ```csharp
    int result = Multiply(7, 7);
    ```

    Aparece un círculo rojo en el margen izquierdo para indicar que ha establecido el punto de interrupción.

1. Presione **F5** (**depurar** > **Iniciar depuración**) para iniciar el depurador.

    El depurador se detiene en el punto de interrupción que estableció. Una flecha amarilla indica que el depurador esté pausado.

## <a name="step-into-native-code"></a>Ir a código nativo

1. Mientras está en pausa en la aplicación administrada, presione **F11** (**depurar** > **paso a paso**).

    Se abre el archivo de encabezado con el código nativo y verá la flecha amarilla que el depurador se detuvo.

    ![Ir a código nativo](../debugger/media/mixed-mode-step-into-native-code.png)

    Ahora, lo puede hacer cosas como conjunto y establecer puntos de interrupción e inspeccionar variables.

1. Mantenga el mouse sobre las variables para ver su valor.

1. Mire el **automático** y **locales** windows para ver la variable y sus valores.

    Mientras está en pausa en el depurador, puede usar otras características del depurador como el **inspección** ventana y **pila de llamadas** ventana.

1. Presione **F11** nuevo para hacer avanzar la línea de depurador uno.

1. Presione **MAYÚS + F11** (**depurar** > **paso a paso fuera**) para continuar con la ejecución de la aplicación y vuelva a poner en pausa en la aplicación administrada.

1. Presione **F5** para continuar la aplicación.

    ¡Enhorabuena! Ha completado el tutorial de depuración en modo mixto.

## <a name="next-steps"></a>Pasos siguientes

En este tutorial, aprendió a habilitar la depuración en modo mixto para depurar código nativo desde una aplicación administrada. Para obtener información general de otras características del depurador, vea el artículo siguiente:

> [!div class="nextstepaction"]
> [Primer vistazo al depurador](../debugger/debugger-feature-tour.md)