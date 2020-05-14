---
title: Depuración en tiempo de diseño | Microsoft Docs
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
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/13/2020
ms.locfileid: "75916142"
---
# <a name="debug-at-design-time-in-visual-studio-c-ccli-visual-basic-f"></a>Depuración en tiempo de diseño en Visual Studio (C#, C++/CLI, Visual Basic, F#)

Para depurar código en tiempo de diseño y no mientras se ejecuta una aplicación, puede usar la ventana **Inmediato**.

Para depurar código XAML subyacente de una aplicación desde el diseñador XAML, como los escenarios de enlace de datos declarativos, puede usar **Depurar** > **Asociar al proceso**.

## <a name="use-the-immediate-window"></a>Uso de la ventana Inmediato

Puede utilizar la ventana **Inmediato** de Visual Studio para ejecutar una función o subrutina sin ejecutar la aplicación. Si la función o subrutina contiene un punto de interrupción, Visual Studio interrumpirá la ejecución en él. A continuación puede utilizar las ventanas del depurador para examinar el estado del programa. Esta característica se denomina *depuración en tiempo de diseño.*

El ejemplo siguiente se desarrolla en Visual Basic. También puede usar la ventana **Inmediato** en tiempo de diseño en aplicación de C#, F#, y C++/CLI.

1. Pegue el siguiente código en una aplicación de consola de Visual Basic en blanco:

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

1. Abra la ventana **Inmediato** seleccionando **Depurar** > **Ventanas** > **Inmediato**. Escriba `?MyFunction` en la ventana y luego presione **Entrar**.

   Se alcanza el punto de interrupción y el valor de **MyFunction** en la ventana **Variables locales** es **1**. Puede examinar la pila de llamadas y otras ventanas de depuración mientras la aplicación está en modo de interrupción.

1. Seleccione **Continuar** en la barra de herramientas de Visual Studio. La aplicación finaliza y se devuelve **1** en la ventana **Inmediato**. Asegúrese de que todavía está en modo de diseño.

1. Escriba `?MyFunction` de nuevo en la ventana **Inmediato** y luego presione **Entrar**. Se alcanza el punto de interrupción y el valor de **MyFunction** en la ventana **Variables locales** es **2**.

1. Sin seleccionar **Continuar**, escriba `?MySub()` en la ventana **Inmediato** y luego presione **Entrar**. Se alcanza el punto de interrupción y el valor de **MyFunction** en la ventana **Variables locales** es **3**. Puede examinar el estado de la aplicación mientras la aplicación está en modo de interrupción.

1. Seleccione **Continuar**. Se alcanza de nuevo el punto de interrupción y el valor de **MyFunction** en la ventana **Variables locales** es ahora **2**. La ventana **Inmediato** devuelve **Se ha evaluado la expresión y no tiene ningún valor**.

1. Seleccione **Continuar** de nuevo. La aplicación finaliza y se devuelve **2** en la ventana **Inmediato**. Asegúrese de que todavía está en modo de diseño.

1. Para borrar el contenido de la ventana **Inmediato**, haga clic con el botón derecho en la ventana y seleccione **Borrar todo**.

## <a name="debug-a-custom-xaml-control-at-design-time-by-attaching-to-xaml-designer"></a>Depuración de un control XAML personalizado en tiempo de diseño asociándolo al diseñador XAML

1. Abra su solución o proyecto en Visual Studio.

1. Compile la solución o el proyecto.

1. Abra la página XAML que contiene el control personalizado que quiere depurar.

   En el caso de los proyectos de UWP que tengan como destino la compilación 16299 o posterior de Windows, este paso iniciará el proceso *UwpSurface.exe*. En el caso de las versiones de WPF o UWP anteriores a la compilación 16299 de Windows, este paso iniciará el proceso *XDesProc.exe*.

1. Abra una segunda instancia de Visual Studio. No abra una solución ni un proyecto en la segunda instancia.

1. En la segunda instancia de Visual Studio, abra el menú **Depurar** y elija **Asociar al proceso...** .

1. En función del tipo de proyecto (vea los pasos anteriores), seleccione el proceso *UwpSurface.exe* o *XDesProc.exe* de la lista de procesos disponibles.

1. En el campo **Asociar a** del cuadro de diálogo **Asociar al proceso**, elija el tipo de código correcto para el control personalizado que quiere depurar.

   Si el control personalizado se ha escrito en un lenguaje .NET, elija el tipo de código .NET adecuado como, por ejemplo, **Administrado (CoreCLR)** . Si el control personalizado se ha escrito en C++, elija **Nativo**.

1. Asocie la segunda instancia de Visual Studio haciendo clic en el botón **Asociar**.

1. En la segunda instancia de Visual Studio, abra los archivos de código asociados al control personalizado que quiere depurar. Asegúrese de abrir tan solo los archivos, no el proyecto ni la solución completos.

1. Coloque los puntos de interrupción necesarios en los archivos abiertos anteriormente.

1. En la primera instancia de Visual Studio, cierre la página XAML que contiene el control personalizado que quiere depurar (la misma página que abrió en pasos anteriores).

1. En la primera instancia de Visual Studio, abra la página XAML que cerró en el paso anterior. Esto hará que el depurador se detenga en el primer punto de interrupción establecido en la segunda instancia de Visual Studio.

1. Depure el código en la segunda instancia de Visual Studio.

## <a name="see-also"></a>Vea también
- [Primer vistazo al depurador](../debugger/debugger-feature-tour.md)
- [Seguridad del depurador](../debugger/debugger-security.md)