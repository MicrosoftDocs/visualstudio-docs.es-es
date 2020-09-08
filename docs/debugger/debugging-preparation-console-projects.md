---
title: Preparación de la depuración de proyectos de consola | Microsoft Docs
ms.custom: seodec18
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging [Visual Studio], console applications
- debugging console applications
- console applications, debugging
ms.assetid: 9641f1d9-2d5a-48b1-8731-6525e8f67892
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e612228bf5440936c336d286962820a02d6bd071
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "75916275"
---
# <a name="debugging-preparation-console-projects-c-c-visual-basic-f"></a>Preparación de la depuración: Proyectos de consola (C#, C++, Visual Basic, F#)

La preparación de la depuración de un proyecto de consola es similar a la de la depuración de un proyecto para Windows, con algunas consideraciones adicionales, como la configuración de argumentos de la línea de comandos y la manera de poner en pausa la aplicación para depurarla. Para obtener más información, consulte [Aplicaciones de Windows Forms](../debugger/debugging-preparation-windows-forms-applications.md) y [Preparación de la depuración: aplicaciones de Windows Forms (.NET)](/previous-versions/visualstudio/visual-studio-2010/sez9z95a(v=vs.100)). Debido a la similitud de todas las aplicaciones de consola, este tema cubre los tipos de proyecto siguientes:

- Aplicación de consola de C#, Visual Basic y F#

- Aplicación de consola de C++ (.NET)

- Aplicación de consola de C++ (Win32)

  Una aplicación de consola utiliza la ventana **Consola** para aceptar entradas y mostrar mensajes de salida. Para escribir en la ventana **Consola**, la aplicación debe utilizar el objeto **Console** en lugar del objeto Debug. Para escribir en la ventana **Salida de Visual Studio**, utilice el objeto Debug de la manera habitual. Asegúrese de que conoce la ubicación en la que la aplicación escribe los datos; de lo contrario, podría buscar mensajes en el lugar incorrecto. Para obtener más información, vea [Console (clase)](/dotnet/api/system.console), [Debug (clase)](/dotnet/api/system.diagnostics.debug) y [Salida (Ventana)](../ide/reference/output-window.md).

## <a name="set-command-line-arguments"></a>Configuración de argumentos de la línea de comandos

Es posible que necesite especificar argumentos de línea de comandos para la aplicación de consola. Para obtener más información, consulte [Configuración del proyecto para una configuración de depuración de C++](../debugger/project-settings-for-a-cpp-debug-configuration.md), [Configuración del proyecto para una configuración de depuración de Visual Basic](../debugger/project-settings-for-a-visual-basic-debug-configuration.md) o [Configuración del proyecto para configuraciones de depuración de C#](../debugger/project-settings-for-csharp-debug-configurations.md).

Al igual que todas las propiedades del proyecto, estos argumentos se conservan entre sesiones de depuración y entre sesiones de Visual Studio. Por tanto, si la aplicación de consola es una aplicación que ya ha depurado antes, recuerde que puede haber argumentos de sesiones anteriores escritos en el cuadro de diálogo **Páginas de propiedades de \<Project>** .

## <a name="start-the-application"></a>Inicio de la aplicación

 Cuando se inician algunas aplicaciones de consola, se ejecutan hasta su finalización y después salen. Este comportamiento podría no proporcionar suficiente tiempo para interrumpir la ejecución y la depuración. Para poder depurar una aplicación, utilice uno de los siguientes procedimientos para iniciar la aplicación:

- Establezca un punto de interrupción en el código e inicie la aplicación.

- Inicie la aplicación con **F10** (**Depurar** > **Paso a paso por procedimientos**) o **F11** (**Depurar** > **Paso a paso por instrucciones**) y, a continuación, desplácese por el código mediante otras opciones, como **Ejecutar hasta clic**.

- En el editor de código, haga clic con el botón derecho en una línea y seleccione **Ejecutar hasta el cursor**.

  Al depurar una aplicación de consola, tal vez desee iniciar la aplicación desde el símbolo del sistema en vez de hacerlo desde Visual Studio. En ese caso, puede iniciar la aplicación desde el símbolo del sistema y asociar a la misma el depurador de Visual Studio. Para obtener más información, vea [Asociar con procesos en ejecución con el depurador de Visual Studio](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md).

  Cuando inicia una aplicación de consola desde Visual Studio, la ventana **Consola** a veces aparece detrás de la ventana de Visual Studio. Si intenta iniciar la aplicación de consola desde Visual Studio pero no ocurre nada, intente mover la ventana de Visual Studio.

## <a name="see-also"></a>Vea también
- [Depuración de código nativo](../debugger/debugging-native-code.md)
- [Depurar código administrado](../debugger/debugging-managed-code.md)
- [Preparación de la depuración de proyectos de C++](../debugger/debugging-preparation-visual-cpp-project-types.md)
- [Tipos de proyectos de C#, F# y Visual Basic](../debugger/debugging-preparation-csharp-f-hash-and-visual-basic-project-types.md)
- [Configuración del proyecto para una configuración de depuración de C++](../debugger/project-settings-for-a-cpp-debug-configuration.md)
- [Seguridad del depurador](../debugger/debugger-security.md)