---
title: 'Tutorial: Depurar código administrado y nativo (modo mixto)'
description: Obtenga información sobre cómo depurar una DLL nativa desde una aplicación de .NET Core o .NET Framework con la depuración en modo mixto
ms.custom: ''
ms.date: 11/02/2018
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
ms.openlocfilehash: 121584611dcf0f25fa1f32a616253ecdecf04332
ms.sourcegitcommit: 0a8ac5f2a685270d9ca79bb39d26fd90099bfa29
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/09/2018
ms.locfileid: "51295766"
---
# <a name="tutorial-debug-managed-and-native-code-in-the-same-debugging-session"></a>Tutorial: Depurar código administrado y nativo en la misma sesión de depuración

Visual Studio le permite habilitar más de un tipo de depurador en una sesión de depuración, que se denomina depuración en modo mixto. En este tutorial, aprenderá a depurar código administrado y nativo en una única sesión de depuración. 

En este tutorial se muestra cómo depurar código nativo desde una aplicación administrada, pero también puede [depurar código administrado desde una aplicación nativa](../debugger/how-to-debug-in-mixed-mode.md). El depurador también admite otros tipos de depuración en modo mixto, como la depuración [Python y código nativo](../python/debugging-mixed-mode-c-cpp-python-in-visual-studio.md)y usar el depurador de script en tipos de aplicaciones como ASP.NET.

En este tutorial va a:

> [!div class="checklist"]
> * Crear un archivo DLL nativa simple
> * Crear una aplicación sencilla de .NET Core o .NET Framework para llamar a la DLL
> * Configurar la depuración en modo mixto
> * Iniciar el depurador
> * Alcanzar un punto de interrupción en la aplicación administrada
> * Ir al código nativo

## <a name="prerequisites"></a>Requisitos previos

Debe tener instalado Visual Studio, con las cargas de trabajo siguientes:
- **Desarrollo de escritorio con C++**
- Cualquier **desarrollo de escritorio de .NET** o **.NET Core, el desarrollo multiplataforma**, dependiendo de qué tipo de aplicación que desee crear.

Si no tiene Visual Studio, vaya a la [descargas de Visual Studio](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017) página para instalarlo de forma gratuita.

Si tiene instalado Visual Studio, pero no tiene las cargas de trabajo que necesita, seleccione **abrir Visual Studio Installer** en el panel izquierdo de Visual Studio **nuevo proyecto** cuadro de diálogo. En el instalador de Visual Studio, seleccione las cargas de trabajo que necesita y, a continuación, seleccione **modificar**.

## <a name="create-a-simple-native-dll"></a>Crear un archivo DLL nativa simple

**Para crear los archivos del proyecto de DLL:**

1. En Visual Studio, seleccione **archivo** > **New** > **proyecto**.

1. En el **nuevo proyecto** cuadro de diálogo **Visual C++**, seleccione **otros**y, a continuación, seleccione **proyecto vacío** en el panel central.

1. En el **nombre** , escriba **Mixed_Mode_Debugging**y, a continuación, seleccione **Aceptar**.

   Visual Studio crea el proyecto vacío y lo muestra en **el Explorador de soluciones**.

1. En **el Explorador de soluciones**, seleccione **archivos de código fuente**y, a continuación, seleccione **proyecto** > **Agregar nuevo elemento**. O bien, haga clic en **archivos de código fuente** y seleccione **agregar** > **nuevo elemento**. 

1. En el **nuevo elemento** cuadro de diálogo, seleccione **archivo C++ (.cpp)**. Tipo **Mixed_Mode.cpp** en el **nombre** campo y, a continuación, seleccione **agregar**.

    Visual Studio agrega el nuevo archivo de C++ para **el Explorador de soluciones**.

1. Copie el código siguiente en *Mixed_Mode.cpp*:

    ```cpp
    #include "Mixed_Mode.h"
    ```
1. En **el Explorador de soluciones**, seleccione **archivos de encabezado**y, a continuación, seleccione **proyecto** > **Agregar nuevo elemento**. O bien, haga clic en **archivos de encabezado** y seleccione **agregar** > **nuevo elemento**. 

1. En el **nuevo elemento** cuadro de diálogo, seleccione **archivo de encabezado (. h)**. Tipo **Mixed_Mode.h** en el **nombre** campo y, a continuación, seleccione **agregar**.

   Visual Studio agrega el nuevo archivo de encabezado para **el Explorador de soluciones**.

1. Copie el código siguiente en *Mixed_Mode.h*:

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

1. Seleccione **archivo** > **guardar todo** o presione **Ctrl**+**MAYÚS**+**S**  para guardar los archivos.

**Para configurar y compilar el proyecto DLL:**

1. En la barra de herramientas de Visual Studio, seleccione **depurar** configuración y **x86** o **x64** plataforma. Si la aplicación que realiza la llamada se va a .NET Core, que siempre se ejecuta en modo de 64 bits, seleccione **x64** como la plataforma.

1. En **el Explorador de soluciones**, seleccione el **Mixed_Mode_Debugging** nodo del proyecto y seleccione el **propiedades** icono, o haga clic en el nodo del proyecto y seleccione **Propiedades**.

1. En la parte superior de la **propiedades** panel, asegúrese de que el **configuración** está establecido en **Active (Debug)** y **plataforma** es igual que lo que establecer en la barra de herramientas: **x64**, o **Win32** para x86 plataforma. 

   > [!IMPORTANT]
   > Si cambia la plataforma de **x86** a **x64** o viceversa, debe volver a configurar las propiedades de la nueva plataforma. 

1. En **propiedades de configuración** en el panel izquierdo, seleccione **vinculador** > **avanzadas**y en la lista desplegable junto a **ningún punto de entrada**, seleccione **No**. Si tuviera que cambiar a **No**, seleccione **aplicar**.

1. En **propiedades de configuración**, seleccione **General**y en la lista desplegable junto a **configuración tipo**, seleccione **biblioteca dinámica (.dll)**. Seleccione **aplicar**y, a continuación, seleccione **Aceptar**.

   ![Cambiar a un archivo DLL nativo](../debugger/media/mixed-mode-set-as-native-dll.png)

1. Seleccione el proyecto en **el Explorador de soluciones** y, a continuación, seleccione **compilar** > **compilar solución**, presione **F7**, o haga clic en el proyecto y seleccione **compilar**.

   El proyecto se debe compilar sin errores.

## <a name="create-a-simple-managed-app-to-call-the-dll"></a>Crear una aplicación administrada simple para llamar a la DLL

1. En Visual Studio, elija **archivo** > **New** > **proyecto**.

   > [!NOTE]
   > Aunque también podría agregar el nuevo proyecto administrado a la solución existente de C++, crear una nueva solución es compatible con más escenarios de depuración.

1. En el **nuevo proyecto** cuadro de diálogo, seleccione **Visual C#** y en el panel central:

   - Para una aplicación de .NET Framework, seleccione **aplicación de consola (.NET Framework)**.
   
   - Para una aplicación .NET Core, seleccione **aplicación de consola (.NET Core)**.

1. En el **nombre** , escriba **Mixed_Mode_Calling_App**y, a continuación, seleccione **Aceptar**.

   Visual Studio crea el proyecto vacío y lo muestra en **el Explorador de soluciones**.

1. Reemplace todo el código en *Program.cs* con el código siguiente:

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

1. En el nuevo código, reemplace la ruta de acceso en `[DllImport]` con la ruta de acceso a la *Mixed_Mode_Debugging.dll* que acaba de crear. Vea el comentario de código para las sugerencias. No olvide reemplazar el *username* marcador de posición.

1. Seleccione **archivo** > **guardar Program.cs** o presione **Ctrl**+**S** para guardar el archivo.

## <a name="configure-mixed-mode-debugging"></a>Configurar la depuración en modo mixto 

### <a name="to-configure-mixed-mode-debugging-for-a-net-framework-app"></a>Para configurar la depuración en modo mixto para una aplicación de .NET Framework 

1. En **el Explorador de soluciones**, seleccione el **Mixed_Mode_Calling_App** nodo del proyecto y seleccione el **propiedades** icono, o haga clic en el nodo del proyecto y seleccione **Propiedades**.

1. Seleccione **depurar** en el panel izquierdo, seleccione el **Habilitar depuración de código nativo** casilla de verificación y, a continuación, cierre la página de propiedades para guardar los cambios.

    ![Habilitar la depuración en modo mixto](../debugger/media/mixed-mode-enable-native-code-debugging.png)

### <a name="to-configure-mixed-mode-debugging-for-a-net-core-app"></a>Para configurar la depuración en modo mixto para una aplicación .NET Core 

En la mayoría de las versiones de Visual Studio 2017, debe usar el *launchSettings.json* archivo en lugar de las propiedades del proyecto para habilitar la depuración en modo mixto para código nativo en una aplicación .NET Core. Para realizar un seguimiento de las actualizaciones de la interfaz de usuario para esta característica, consulte este [problema de GitHub](https://github.com/dotnet/project-system/issues/1125).

1. En **el Explorador de soluciones**, expanda **propiedades**y abra el *launchSettings.json* archivo. 

   >[!NOTE]
   >De forma predeterminada, *launchSettings.json* en *C:\Users\username\source\repos\Mixed_Mode_Calling_App\Properties*. Si *launchSettings.json* no existe, seleccione la **Mixed_Mode_Calling_App** proyecto **el Explorador de soluciones** y, a continuación, seleccione el **propiedades** icono, o haga clic en el proyecto y seleccione **propiedades**. Realice un cambio temporal en el **depurar** pestaña y compile el proyecto. Esto creará un *launchSettings.json* archivo. Revertir los cambios realizados en el **depurar** ficha.

1. En el *lauchsettings.json* , agregue la siguiente línea:

    ```csharp
    "nativeDebugging": true
    ```

    El archivo completo tendrá un aspecto similar al ejemplo siguiente:

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

## <a name="set-a-breakpoint-and-start-debugging"></a>Establezca un punto de interrupción e iniciar la depuración

1. En el C# proyecto, abra *Program.cs*. Establecer un punto de interrupción en la siguiente línea de código haciendo clic en el margen izquierdo, seleccione la línea y presionando **F9**, o haciendo clic en la línea y seleccionar **punto de interrupción**  >  **Insertar punto de interrupción**.

    ```csharp
    int result = Multiply(7, 7);
    ```

    Aparece un círculo rojo en el margen izquierdo donde estableció el punto de interrupción.

1. Presione **F5**, seleccione la flecha verde en la barra de herramientas de Visual Studio, o **depurar** > **Iniciar depuración** para iniciar la depuración.

   El depurador se detiene en el punto de interrupción que estableció. Una flecha amarilla indica que el depurador está pausado actualmente.

## <a name="step-in-and-out-of-native-code"></a>Paso de entrada y salida de código nativo

1. Mientras la depuración está en pausa en la aplicación administrada, presione **F11**, o bien seleccione **depurar** > **paso a paso**.

   El *Mixed_Mode.h* abre el archivo de encabezado nativo, y ver la flecha amarilla en el depurador está en pausa.

   ![Ir a código nativo](../debugger/media/mixed-mode-step-into-native-code.png)

1. Ahora, puede establecer y alcanzar puntos de interrupción e inspeccionar variables en el código nativo o administrado.

   - Mantenga el mouse sobre las variables en el código fuente para ver sus valores.

   - Examine la variable y sus valores en el **automático** y **variables locales** windows.

   - Mientras está en pausa en el depurador, también puede usar el **inspección** windows y la **pila de llamadas** ventana.

1. Presione **F11** nuevo para hacer avanzar la línea de un depurador.

1. Presione **MAYÚS**+**F11** o seleccione **depurar** > **paso a paso fuera** para continuar la ejecución y hacer una pausa en el aplicación administrada.

1. Presione **F5** o seleccione la flecha verde para continuar con la depuración de la aplicación.

¡Enhorabuena! Ha completado el tutorial sobre la depuración en modo mixto.

## <a name="next-step"></a>Paso siguiente

En este tutorial, ha aprendido a depurar código nativo desde una aplicación administrada al habilitar la depuración en modo mixto. Para obtener información general de otras características del depurador, vea:

> [!div class="nextstepaction"]
> [Primer vistazo al depurador](../debugger/debugger-feature-tour.md)
