---
title: Depurar en tiempo de diseño | Microsoft Docs
ms.custom: seodec18
ms.date: 11/21/2018
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- VB
helpviewer_keywords:
- debugging [Visual Studio], design-time
- breakpoints, design-time debugging
- Immediate window, design-time debugging
- design-time debugging
ms.assetid: 35bfdd2c-6f60-4be1-ba9d-55fce70ee4d8
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 86e6aa0da41a16445b3e3328a1ee0bc84063dd52
ms.sourcegitcommit: 35bebf794f528d73d82602e096fd97d7b8f82c25
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 12/18/2018
ms.locfileid: "53561728"
---
# <a name="debug-at-design-time-in-visual-studio-c-c-visual-basic-f"></a>Depurar en tiempo de diseño en Visual Studio (C#, C++, Visual Basic, F#)

Para depurar el código en tiempo de diseño en lugar de una aplicación mientras se está ejecutando, puede usar el **inmediato** ventana. 

Para depurar el código XAML detrás de una aplicación desde el Diseñador XAML, como el código de enlace de datos, puede usar **depurar** > **asociar al proceso**.
  
## <a name="use-the-immediate-window"></a>Utilice la ventana Inmediato  

Puede usar Visual Studio **inmediato** ventana para ejecutar una función o subrutina sin ejecutar la aplicación. Si la función o subrutina contiene un punto de interrupción, Visual Studio se interrumpirá en el punto de interrupción. A continuación puede utilizar las ventanas del depurador para examinar el estado del programa. Esta característica se denomina *depuración en tiempo de diseño.*  

El ejemplo siguiente es en Visual Basic. También puede usar el **inmediato** ventana en tiempo de diseño en C#, F#y las aplicaciones de C++.

1. Pegue el código siguiente en una aplicación de consola de Visual Basic en blanco:  
   
   ```vb  
   Module Module1
   
       Sub Main()
           MySub()
       End Sub
   
       Function MyFunction() As Decimal
           Static i As Integer
           i = i + 1
           Return i
       End Function
   
       Sub MySub()
           MyFunction()
   
       End Sub
   End Module
   ```  
   
1. Establezca un punto de interrupción en la línea **End Function**.  
   
1. Abra el **inmediato** ventana seleccionando **depurar** > **Windows** > **inmediato**. Tipo `?MyFunction` en la ventana y, a continuación, presione **ENTRAR**.   
   
   El punto de interrupción es el posicionamiento y el valor de **MyFunction** en el **variables locales** ventana es **1**. Puede examinar la pila de llamadas y otras ventanas de depuración mientras la aplicación está en modo de interrupción. 
   
1. Seleccione **continuar** en la barra de herramientas de Visual Studio. La aplicación finaliza, y **1** se devuelve en el **inmediato** ventana. Asegúrese de que sigue estando en modo de diseño.  
   
1. Tipo `?MyFunction` en el **inmediato** ventana nuevo y presione **ENTRAR**. El punto de interrupción es el posicionamiento y el valor de **MyFunction** en el **variables locales** ventana es **2**. 
   
1. Sin seleccionar **continuar**, tipo `?MySub()` en el **inmediato** ventana y, a continuación, presione **ENTRAR**. El punto de interrupción es el posicionamiento y el valor de **MyFunction** en el **variables locales** ventana es **3**. Puede examinar el estado de la aplicación mientras la aplicación está en modo de interrupción. 
   
1. Seleccione **continuar**. El punto de interrupción es el posicionamiento de nuevo y el valor de **MyFunction** en el **variables locales** ventana ahora es **2**. El **inmediato** ventana devuelve **expresión se ha evaluado y no tiene ningún valor**.
   
1. Seleccione **continuar** nuevo. La aplicación finaliza, y **2** se devuelve en el **inmediato** ventana. Asegúrese de que está todavía en modo de diseño.
   
1. Para borrar el contenido de la **inmediato** ventana, el botón secundario en la ventana y seleccione **Borrar todo**. 

## <a name="attach-to-an-app-from-the-xaml-designer"></a>Asociar a una aplicación desde el Diseñador XAML

En algunos escenarios de enlace de datos declarativo, lo puede ayudar a depurar el código subyacente en el Diseñador XAML.

1. En el proyecto de Visual Studio, agregue una nueva página XAML, como *temp.xaml*. Deje en blanco la nueva página XAML. 
   
1. Compile la solución.
   
1. Abra *temp.xaml*, que carga el Diseñador XAML, *XDesProc.exe*, o *UwpSurface.exe* en una aplicación para UWP. 
   
1. Abra una nueva instancia de Visual Studio. En la nueva instancia, seleccione **depurar** > **asociar al proceso**. 
   
1. En el **asociar al proceso** cuadro de diálogo, seleccione el diseñador procesar desde el **procesos disponibles** lista.
   
   Para UWP, los proyectos destinados a Windows compilación 16299 o versiones posteriores, es el proceso del diseñador *UwpSurface.exe*. WPF o UWP en las versiones anteriores a 16299, es el proceso del diseñador *XDesProc.exe*.
   
1. Asegúrese de que el **adjuntar a** campo se establece en el tipo de código correcto para la versión de .NET como **Managed Code (CoreCLR)**. 
   
1. Seleccione **adjuntar**.
   
1. Mientras se asocia al proceso, cambie a la otra instancia de Visual Studio y establecer puntos de interrupción donde desea depurar el código subyacente de la aplicación.
   
   Por ejemplo, podría establecer un punto de interrupción en el código del convertidor de tipo para el XAML siguiente, que enlaza un control TextBlock en tiempo de diseño.
   
    ```xaml
    <TextBlock Text="{Binding title, ConverterParameter=lower, Converter={StaticResource StringFormatConverter}, Mode=TwoWay}"  />
    ```
   Cuando se carga la página, el punto de interrupción.
  
## <a name="see-also"></a>Vea también  
 [En primer lugar, examine el depurador](../debugger/debugger-feature-tour.md) [seguridad del depurador](../debugger/debugger-security.md)   