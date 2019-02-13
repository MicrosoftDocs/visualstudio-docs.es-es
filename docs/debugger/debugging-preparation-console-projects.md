---
title: Prepararse para depurar proyectos de consola | Microsoft Docs
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
ms.openlocfilehash: 15ff4af24ac814dca73ee7032da2d66b29df641d
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 01/25/2019
ms.locfileid: "54972214"
---
# <a name="debugging-preparation-console-projects-c-c-visual-basic-f"></a>Preparación de la depuración: Proyectos de consola (C#, C++, Visual Basic, F#)

Preparar la depuración de un proyecto de consola es similar a preparar la depuración de un proyecto para Windows, con algunas consideraciones adicionales. Para obtener más información, consulte [aplicaciones de Windows Forms](../debugger/debugging-preparation-windows-forms-applications.md), y [preparar la depuración: Aplicaciones de Windows Forms (.NET)](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/sez9z95a(v=vs.100)) Debido a la similitud de todas las aplicaciones de consola, este tema cubre los tipos de proyecto siguientes:  
  
- C#, Visual Basic, y F# aplicación de consola  
  
- Aplicación de consola de C++ (.NET)  
  
- Aplicación de consola de C++ (Win32)  
  
  Es posible que necesite especificar argumentos de línea de comandos para la aplicación de consola. Para obtener más información, consulte [configuración del proyecto para una configuración de depuración de C++](../debugger/project-settings-for-a-cpp-debug-configuration.md), [configuración del proyecto para una configuración de depuración de Visual Basic](../debugger/project-settings-for-a-visual-basic-debug-configuration.md), o [configuración del proyecto para configuraciones de depuración de C# ](../debugger/project-settings-for-csharp-debug-configurations.md).  
  
  Al igual que todas las propiedades del proyecto, estos argumentos se conservan entre sesiones de depuración y entre sesiones de Visual Studio. Por lo tanto, si la aplicación de consola es una aplicación que ya ha depurado anteriormente, recuerde que puede haber argumentos de sesiones anteriores escritos en el cuadro de diálogo **\<Proyecto > Páginas de propiedades**.  
  
  Una aplicación de consola utiliza la ventana **Consola** para aceptar entradas y mostrar mensajes de salida. Para escribir en el **consola** ventana, la aplicación debe utilizar el **consola** objeto en lugar del objeto Debug. Para escribir en la ventana **Salida de Visual Studio**, utilice el objeto Debug de la manera habitual. Asegúrese de que conoce la ubicación en la que la aplicación escribe los datos; de lo contrario, podría buscar mensajes en el lugar incorrecto. Para obtener más información, vea [Console (clase)](/dotnet/api/system.console), [Debug (clase)](/dotnet/api/system.diagnostics.debug) y [Salida (Ventana)](../ide/reference/output-window.md).  
  
## <a name="starting-the-application"></a>Iniciar la aplicación  
 Cuando se inician algunas aplicaciones de consola, se ejecutan hasta su finalización y después salen. Este comportamiento podría no proporcionar suficiente tiempo para interrumpir la ejecución y la depuración. Para poder depurar una aplicación, utilice uno de los siguientes procedimientos para iniciar la aplicación:  
  
- Establezca un punto de interrupción en el código e iniciar la aplicación.
  
- Iniciar la aplicación mediante **F10** (**depurar** > **saltar**) o **F11** (**depurar**  >  **Paso a paso**) y, a continuación, navegar por el código con otras opciones como **para ejecutar hasta**.
  
- En el editor de código, haga clic en una línea y seleccione **ejecutar hasta el cursor**.  
  
  Al depurar una aplicación de consola, tal vez desee iniciar la aplicación desde el símbolo del sistema en vez de hacerlo desde Visual Studio. En ese caso, puede iniciar la aplicación desde el símbolo del sistema y asociar a la misma el depurador de Visual Studio. Para obtener más información, consulte [adjuntar a procesos en ejecución](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md).  
  
  Cuando inicia una aplicación de consola desde Visual Studio, la ventana **Consola** a veces aparece detrás de la ventana de Visual Studio. Si intenta iniciar la aplicación de consola desde Visual Studio pero no ocurre nada, intente mover la ventana de Visual Studio.  
  
## <a name="see-also"></a>Vea también  
 [Depuración de código nativo](../debugger/debugging-native-code.md)   
 [Depurar código administrado](../debugger/debugging-managed-code.md)   
 [Tipos de proyecto de Visual C++](../debugger/debugging-preparation-visual-cpp-project-types.md)   
 [Tipos de proyectos de C#, F# y Visual Basic](../debugger/debugging-preparation-csharp-f-hash-and-visual-basic-project-types.md)   
 [Configuración del proyecto para una configuración de depuración de C++](../debugger/project-settings-for-a-cpp-debug-configuration.md)   
 [Seguridad del depurador](../debugger/debugger-security.md)