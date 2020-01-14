---
title: Depurar en tiempo de diseño | Microsoft Docs
ms.custom: ''
ms.date: 01/10/2019
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: beb16ae52f880e31bd19a185d47b13c02026752f
ms.sourcegitcommit: 939407118f978162a590379997cb33076c57a707
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/13/2020
ms.locfileid: "75916142"
---
# <a name="debug-at-design-time-in-visual-studio-c-ccli-visual-basic-f"></a>Depurar en tiempo de diseño enC#visual C++Studio (,/CLI F#, Visual Basic,)

Para depurar código en tiempo de diseño en lugar de mientras se ejecuta una aplicación, puede usar la ventana **inmediato** .

Para depurar código XAML detrás de una aplicación desde el diseñador XAML, como los escenarios de enlace de datos declarativos, puede usar **debug** > **asociar al proceso**.

## <a name="use-the-immediate-window"></a>Usar la ventana inmediato

Puede usar la ventana **inmediato** de Visual Studio para ejecutar una función o subrutina sin ejecutar la aplicación. Si la función o subrutina contiene un punto de interrupción, Visual Studio se interrumpirá en el punto de interrupción. A continuación puede utilizar las ventanas del depurador para examinar el estado del programa. Esta característica se denomina *depuración en tiempo de diseño.*

El siguiente ejemplo está en Visual Basic. También puede usar la ventana **inmediato** en tiempo de diseño en C#aplicaciones F#de, C++y/CLI.

1. Pegue el código siguiente en una aplicación de consola en Visual Basic en blanco:

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

1. Establezca un punto de interrupción en la **función de fin**de línea.

1. Abra la ventana **inmediato** seleccionando **depurar** > **Windows** > **inmediato**. Escriba `?MyFunction` en la ventana y, a continuación, presione **entrar**.

   Se alcanza el punto de interrupción y el valor de **myFunction** en la ventana **variables locales** es **1**. Puede examinar la pila de llamadas y otras ventanas de depuración mientras la aplicación está en modo de interrupción.

1. Seleccione **continuar** en la barra de herramientas de Visual Studio. La aplicación finaliza y se devuelve **1** en la ventana **inmediato** . Asegúrese de que todavía está en modo de diseño.

1. Vuelva a escribir `?MyFunction` en la ventana **inmediato** y presione **entrar**. Se alcanza el punto de interrupción y el valor de **myFunction** en la ventana **variables locales** es **2**.

1. Sin seleccionar **continuar**, escriba `?MySub()` en la ventana **inmediato** y presione **entrar**. Se alcanza el punto de interrupción y el valor de **myFunction** en la ventana **variables locales** es **3**. Puede examinar el estado de la aplicación mientras la aplicación está en modo de interrupción.

1. Selecciona **Continuar**. El punto de interrupción se vuelve a visitar y el valor de **myFunction** en la ventana **variables locales** es ahora **2**. La ventana **inmediato** devuelve una **expresión que se ha evaluado y no tiene ningún valor**.

1. Seleccione **continuar** de nuevo. La aplicación finaliza y se devuelve **2** en la ventana **inmediato** . Asegúrese de que todavía está en modo de diseño.

1. Para borrar el contenido de la ventana **inmediato** , haga clic con el botón derecho en la ventana y seleccione **Borrar todo**.

## <a name="debug-a-custom-xaml-control-at-design-time-by-attaching-to-xaml-designer"></a>Depurar un control XAML personalizado en tiempo de diseño adjuntando al diseñador XAML

1. Abra la solución o el proyecto en Visual Studio.

1. Compile la solución o el proyecto.

1. Abra la página XAML que contiene el control personalizado que desea depurar.

   En el caso de los proyectos de UWP que tengan como destino Windows Build 16299 o superior, este paso iniciará el proceso *UwpSurface. exe* . En el caso de las versiones de WPF o UWP anteriores a la compilación 16299 de Windows, este paso iniciará el proceso *XDesProc. exe* .

1. Abra una segunda instancia de Visual Studio. No abra una solución o proyecto en la segunda instancia.

1. En la segunda instancia de Visual Studio, abra el menú **depurar** y elija **asociar al proceso.** .

1. En función del tipo de proyecto (vea pasos anteriores), seleccione el proceso *UwpSurface. exe* o *XDesProc. exe* en la lista de procesos disponibles.

1. En el campo **asociar a** del cuadro de diálogo **asociar al proceso** , elija el tipo de código correcto para el control personalizado que desea depurar.

   Si el control personalizado se ha escrito en un lenguaje .NET, elija el tipo de código .NET adecuado, como **administrado (CoreCLR)** . Si el control personalizado se ha escrito en C++, elija **nativo**.

1. Adjunte la segunda instancia de Visual Studio haciendo clic en el botón **adjuntar** .

1. En la segunda instancia de Visual Studio, abra los archivos de código asociados al control personalizado que desea depurar. Asegúrese de abrir simplemente los archivos, no el proyecto o la solución completa.

1. Coloque los puntos de interrupción necesarios en los archivos abiertos previamente.

1. En la primera instancia de Visual Studio, cierre la página XAML que contiene el control personalizado que desea depurar (la misma página que abrió en pasos anteriores).

1. En la primera instancia de Visual Studio, abra la página XAML que cerró en el paso anterior. Esto hará que el depurador se detenga en el primer punto de interrupción establecido en la segunda instancia de Visual Studio.

1. Depure el código en la segunda instancia de Visual Studio.

## <a name="see-also"></a>Vea también
- [Primer vistazo al depurador](../debugger/debugger-feature-tour.md)
- [Seguridad del depurador](../debugger/debugger-security.md)