---
title: Depurar en tiempo de diseño - Visual Studio | Documentos de Microsoft
ms.custom: ''
ms.date: 02/21/2018
ms.technology:
- vs-ide-debug
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
ms.openlocfilehash: a2e907cff461852d09e7b5b00482d2bdf42c0340
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="debug-at-design-time-in-visual-studio"></a>Depurar en tiempo de diseño en Visual Studio

En algunos escenarios, puede que desee depurar el código de diseño de tiempo en lugar de mientras se ejecuta la aplicación. Puede hacerlo mediante el **inmediato** ventana. Si desea depurar el código XAML que interactúa con otro código, como el código de enlace de datos, puede usar **depurar** > **adjuntar al proceso** para hacerlo.
  
### <a name="debug-at-design-time-using-the-immediate-window"></a>Depurar en tiempo de diseño mediante la ventana Inmediato.  

Puede usar Visual Studio **inmediato** ventana para ejecutar una función o subrutina mientras la aplicación no se está ejecutando. Si la función o subrutina contiene un punto de interrupción, Visual Studio interrumpirá la ejecución en el punto adecuado. A continuación puede utilizar las ventanas del depurador para examinar el estado del programa. Esta característica se denomina depuración en tiempo de diseño.  

El ejemplo siguiente es en Visual Basic, pero la **inmediato** ventana también se admite en aplicaciones de C# y C++.
  
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
  
3.  Abra la **inmediato** ventana (**depurar** > **Windows** > **inmediato**) y escriba lo siguiente en el ventana: `?MyFunction<enter>`  
  
4.  Compruebe que se ha alcanzado el punto de interrupción, y que la pila de llamadas es exacta.  
  
5.  En el **depurar** menú, haga clic en **continuar**y compruebe que todavía está en modo de diseño.  
  
6.  Escriba lo siguiente en el **inmediato** ventana: `?MyFunction<enter>`  
  
7.  Escriba lo siguiente en el **inmediato** ventana: `?MySub<enter>`  
  
8.  Compruebe que el punto de interrupción y examinar el valor de la variable estática `i` en el **locales** ventana. Debería tener el valor de 3.  
  
9. Compruebe que la pila de llamadas es exacta.  
  
10. En el **depurar** menú, haga clic en **continuar**y compruebe que todavía está en modo de diseño.  

## <a name="debug-at-design-time-from-the-xaml-designer"></a>Depurar en tiempo de diseño desde el Diseñador XAML

Puede resultar útil depurar el código subyacente en el Diseñador XAML en algunos escenarios de enlace de datos declarativo.

1. En el proyecto, agregue una nueva página XAML, como *temp.xaml*. Deje en blanco la nueva página XAML. 

1. Compile la solución.

1. Abra *temp.xaml*, que carga el diseñador (*UwpSurface.exe* en una aplicación UWP o *XDesProc.exe*) por lo que pueden asociarse a ella en pasos posteriores. 

1. Abra una nueva instancia de Visual Studio. En la nueva instancia, abra el **adjuntar al proceso** cuadro de diálogo (**depurar** > **adjuntar al proceso**), establezca el **adjuntar a** campo al tipo de código es correcta, como **código administrado (CoreCLR)** o el tipo de código correcto en función de la versión. NET. Seleccione el proceso de diseñador correcto en la lista y elija **adjuntar**.

    Para UWP proyectos destinados a generan 16299 o versiones posteriores, el proceso de diseñador es *UwpSurface.exe*. Con WPF ni las versiones de UWP anteriores a 16299, es el proceso de diseñador *XDesProc.exe*.

1. Mientras se asocia al proceso, cambie a su proyecto, abra el código subyacente que va a depurar y establezca un punto de interrupción.

1. Por último, abra la página que contiene el código XAML que incluye el enlace de datos.

    Por ejemplo, podría establecer un punto de interrupción en el código del convertidor de tipo para el código XAML siguiente, que enlaza un control TextBlock en tiempo de diseño.

    ```xaml
    <TextBlock Text="{Binding title, ConverterParameter=lower, Converter={StaticResource StringFormatConverter}, Mode=TwoWay}"  />
    ```
   Cuando se carga la página, se visita el punto de interrupción.
  
## <a name="see-also"></a>Vea también  
 [Seguridad del depurador](../debugger/debugger-security.md)   
 [Conceptos básicos del depurador](../debugger/debugger-basics.md)
