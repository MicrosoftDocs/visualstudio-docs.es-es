---
title: 'Preparación de la depuración: Proyectos de consola | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- debugging [Visual Studio], console applications
- debugging console applications
- console applications, debugging
ms.assetid: 9641f1d9-2d5a-48b1-8731-6525e8f67892
caps.latest.revision: 29
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d268495f21ca9b4869d4c084d3fd6982d842e6c7
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49825923"
---
# <a name="debugging-preparation-console-projects"></a>Preparación de la depuración: proyectos de consola
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Preparar la depuración de un proyecto de consola es similar a preparar la depuración de un proyecto para Windows, con algunas consideraciones adicionales. Para obtener más información, consulte [aplicaciones de Windows Forms](../debugger/debugging-preparation-windows-forms-applications.md), y [preparar la depuración: aplicaciones de Windows Forms (. NET)](http://msdn.microsoft.com/en-us/a8bc54de-41a3-464d-9a12-db9bdcbc1ad5). Debido a la similitud de todas las aplicaciones de consola, este tema cubre los tipos de proyecto siguientes:  
  
- Aplicación de consola de C#  
  
- Aplicación de consola de Visual Basic  
  
- Aplicación de consola de C++ (.NET)  
  
- Aplicación de consola de C++ (Win32)  
  
  Es posible que necesite especificar argumentos de línea de comandos para la aplicación de consola. Para obtener más información, consulte [configuración del proyecto para una configuración de depuración de C++](../debugger/project-settings-for-a-cpp-debug-configuration.md), [configuración del proyecto para una configuración de depuración de Visual Basic](../debugger/project-settings-for-a-visual-basic-debug-configuration.md), o [configuración del proyecto para configuraciones de depuración de C# ](../debugger/project-settings-for-csharp-debug-configurations.md).  
  
  Al igual que todas las propiedades del proyecto, estos argumentos se conservan entre sesiones de depuración y entre sesiones de Visual Studio. Por lo tanto, si la aplicación de consola es una que ya ha depurado anteriormente, recuerde que puede haber argumentos de sesiones anteriores escritos en el  **\<proyecto > páginas de propiedades** cuadro de diálogo.  
  
  Una aplicación de consola utiliza la **consola** ventana para aceptar la entrada y mostrar mensajes de salida. Para escribir en el **consola** ventana, la aplicación debe utilizar el **consola** objeto en lugar del objeto Debug. Para escribir en el **salida de Visual Studio** ventana, utilice el objeto de depuración, como de costumbre. Asegúrese de que conoce la ubicación en la que la aplicación escribe los datos; de lo contrario, podría buscar mensajes en el lugar incorrecto. Para obtener más información, consulte [clase Console](https://msdn.microsoft.com/library/system.console.aspx), [clase Debug](https://msdn.microsoft.com/library/system.diagnostics.debug.aspx), y [ventana de salida](../ide/reference/output-window.md).  
  
## <a name="starting-the-application"></a>Iniciar la aplicación  
 Cuando se inician algunas aplicaciones de consola, se ejecutan hasta su finalización y después salen. Este comportamiento podría no proporcionar suficiente tiempo para interrumpir la ejecución y la depuración. Para poder depurar una aplicación, utilice uno de los siguientes procedimientos para iniciar la aplicación:  
  
- Se inicia la aplicación y se ejecuta hasta que alcanza el punto de interrupción.  
  
- Se inicia la aplicación y se interrumpe inmediatamente en la primera línea de código fuente.  
  
- En una ventana de código fuente, haga clic en una línea y seleccione **ejecutar hasta el cursor**.  
  
   Se inicia la aplicación y se ejecuta hasta la línea seleccionada, o hasta un punto de interrupción, si se alcanza el punto de interrupción antes que la línea.  
  
  Al depurar una aplicación de consola, tal vez desee iniciar la aplicación desde el símbolo del sistema en vez de hacerlo desde Visual Studio. En ese caso, puede iniciar la aplicación desde el símbolo del sistema y asociar a la misma el depurador de Visual Studio. Para obtener más información, consulte [adjuntar a procesos en ejecución](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md).  
  
  Cuando se inicia una aplicación de consola desde Visual Studio, el **consola** ventana a veces aparece detrás de la ventana de Visual Studio. Si intenta iniciar la aplicación de consola desde Visual Studio pero no ocurre nada, intente mover la ventana de Visual Studio.  
  
## <a name="see-also"></a>Vea también  
 [Depuración de código nativo](../debugger/debugging-native-code.md)   
 [Depurar código administrado](../debugger/debugging-managed-code.md)   
 [Tipos de proyecto de Visual C++](../debugger/debugging-preparation-visual-cpp-project-types.md)   
 [Tipos de proyectos de C#, F# y Visual Basic](../debugger/debugging-preparation-csharp-f-hash-and-visual-basic-project-types.md)   
 [Configuración del proyecto para una configuración de depuración de C++](../debugger/project-settings-for-a-cpp-debug-configuration.md)   
 [Seguridad del depurador](../debugger/debugger-security.md)



