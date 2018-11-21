---
title: Depurar en tiempo de diseño - Visual Studio | Microsoft Docs
ms.custom: ''
ms.date: 02/21/2018
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
ms.openlocfilehash: 452b4045357db12c4b4cff1a5b6e27035cf85d82
ms.sourcegitcommit: a7de99f36e9ead7ea9e9bac23c88d05ddfc38b00
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/20/2018
ms.locfileid: "52257204"
---
# <a name="debug-at-design-time-in-visual-studio-c-c-visual-basic-f"></a>Depurar en tiempo de diseño en Visual Studio (C#, C++, Visual Basic, F#)

En algunos escenarios, es posible que desee depurar código en el diseño de tiempo en lugar de mientras se ejecuta la aplicación. Puede hacerlo mediante el **inmediato** ventana. Si desea depurar el código XAML que interactúa con otro código, como el código de enlace de datos, puede usar **depurar** > **asociar al proceso** hacer eso.
  
### <a name="debug-at-design-time-using-the-immediate-window"></a>Depurar en tiempo de diseño mediante la ventana Inmediato  

Puede usar Visual Studio **inmediato** ventana para ejecutar una función o subrutina mientras la aplicación no se está ejecutando. Si la función o subrutina contiene un punto de interrupción, Visual Studio interrumpirá la ejecución en el punto adecuado. A continuación puede utilizar las ventanas del depurador para examinar el estado del programa. Esta característica se denomina depuración en tiempo de diseño.  

El ejemplo siguiente es en Visual Basic. El uso de la **inmediato** ventana en tiempo de diseño también se admite en C#, C++, y F# aplicaciones.
  
1.  Pegue el siguiente código en una aplicación de consola de Visual Basic:  
  
    ```vb  
    Module Module1  
  
        Sub Main()  
            MySub()  
        End Sub  
  
        Function MyFunction() As Decimal  
            Static i As Integer  
            i = i + 1  
            Dim s As String  
  
            s = "Add Breakpoint here"  
            Return 4  
        End Function  
  
        Sub MySub()  
            MyFunction()  
        End Sub  
    End Module  
    ```  
  
2.  Establezca un punto de interrupción en la línea `s="Add BreakPoint Here"`.  
  
3.  Abra el **inmediato** ventana (**depurar** > **Windows** > **inmediato**) y escriba lo siguiente en el ventana: `?MyFunction<enter>`  
  
4.  Compruebe que se ha alcanzado el punto de interrupción, y que la pila de llamadas es exacta.  
  
5.  En el **depurar** menú, haga clic en **continuar**y compruebe que está todavía en modo de diseño.  
  
6.  Escriba lo siguiente en el **inmediato** ventana: `?MyFunction<enter>`  
  
7.  Escriba lo siguiente en el **inmediato** ventana: `?MySub<enter>`  
  
8.  Compruebe que el punto de interrupción y examinar el valor de la variable estática `i` en el **variables locales** ventana. Debería tener el valor de 3.  
  
9. Compruebe que la pila de llamadas es exacta.  
  
10. En el **depurar** menú, haga clic en **continuar**y compruebe que está todavía en modo de diseño.  

## <a name="debug-at-design-time-from-the-xaml-designer"></a>Depurar en tiempo de diseño desde el Diseñador XAML

Puede ser útil depurar el código subyacente desde el Diseñador XAML en algunos escenarios de enlace de datos declarativo.

1. En el proyecto, agregue una nueva página XAML, como *temp.xaml*. Deje en blanco la nueva página XAML. 

1. Compile la solución.

1. Abra *temp.xaml*, que carga el diseñador (*UwpSurface.exe* en una aplicación UWP o *XDesProc.exe*) por lo que pueden asociarse a ella en pasos posteriores. 

1. Abra una nueva instancia de Visual Studio. En la nueva instancia, abra el **asociar al proceso** cuadro de diálogo (**depurar** > **asociar al proceso**), establezca el **adjuntar a** campo para el tipo de código correcta, como **Managed Code (CoreCLR)** o el tipo de código correcto según la versión. NET. Seleccione el proceso correcto del Diseñador de la lista y elija **adjuntar**.

    Para UWP, los proyectos destinados a compilación 16299 o versiones posteriores, es el proceso del diseñador *UwpSurface.exe*. Para WPF o versiones de UWP anteriores a 16299, es el proceso del diseñador *XDesProc.exe*.

1. Mientras se asocia al proceso, cambie a su proyecto, abra el código subyacente en el que desee depurar y establecer un punto de interrupción.

1. Por último, abra la página que contiene el código XAML que incluye el enlace de datos.

    Por ejemplo, podría establecer un punto de interrupción en el código del convertidor de tipo para el XAML siguiente, que enlaza un control TextBlock en tiempo de diseño.

    ```xaml
    <TextBlock Text="{Binding title, ConverterParameter=lower, Converter={StaticResource StringFormatConverter}, Mode=TwoWay}"  />
    ```
   Cuando se carga la página, el punto de interrupción.
  
## <a name="see-also"></a>Vea también  
 [Seguridad del depurador](../debugger/debugger-security.md)   
 [Conceptos básicos del depurador](../debugger/getting-started-with-the-debugger.md)
