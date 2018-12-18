---
title: 'Tutorial: Usar IntelliTrace | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e1c9c91a-0009-4c4e-9b4f-c9ab3a6022a7
caps.latest.revision: 10
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: cc1e2b40e16a14da505243aeb11542df3adfb18d
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/16/2018
ms.locfileid: "51781314"
---
# <a name="walkthrough-using-intellitrace"></a>Tutorial: Uso de IntelliTrace
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Puede usar IntelliTrace para recopilar información sobre determinados eventos, categorías de eventos o llamadas a funciones individuales. En los siguientes procedimientos se muestra cómo hacerlo.  
  
 Puede usar IntelliTrace en Visual Studio Enterprise (pero no en las ediciones Professional o Community).  
  
##  <a name="GettingStarted"></a> Uso de IntelliTrace solo con eventos  
 Puede intentar depurar con solo los eventos de IntelliTrace. Los eventos de IntelliTrace son eventos del depurador, excepciones, eventos de .NET Framework y otros eventos del sistema. Antes de iniciar la depuración debe activar o desactivar eventos específicos para controlar los eventos que IntelliTrace registra. Para obtener más información, consulte [las características de IntelliTrace](../debugger/intellitrace-features.md).  
  
 Los pasos siguientes muestran cómo depurar solo con eventos de IntelliTrace:  
  
1.  Active el evento de IntelliTrace para el acceso de archivo. Vaya a la página **Herramientas / Opciones / IntelliTrace / Eventos de IntelliTrace** y expanda la categoría **Archivo** . Compruebe la categoría de eventos **Archivo** . Esto hace que se comprueben todos los eventos de archivo (acceso, cierre y eliminación).  
  
2.  Cree una aplicación de consola de C#. En el archivo Program.cs, agregue la siguiente declaración de `using`:  
  
    ```csharp  
    using System.IO;  
    ```  
  
3.  Cree un <xref:System.IO.FileStream> en el método Principal, lea de él, ciérrelo y elimine el archivo. Agregue otra línea solo para tener un sitio donde establecer un punto de interrupción:  
  
    ```csharp  
    static void Main(string[] args)  
    {  
        FileStream fs = File.Create("WordSearchInputs.txt");  
        fs.ReadByte();  
        fs.Close();  
        File.Delete("WordSearchInputs.txt");  
  
        Console.WriteLine("done");  
    }  
    ```  
  
4.  Establecer un punto de interrupción en `Console.WriteLine("done");`  
  
5.  Inicie la depuración como de costumbre. (Presione **F5** o haga clic en **Depurar / Iniciar depuración**.  
  
    > [!TIP]
    >  Mantenga abiertas las ventanas **Locales** y **Automático** mientras depura para ver y registrar los valores en estas ventanas.  
  
6.  La ejecución se detiene en el punto de interrupción. Si no ve la ventana **Herramientas de diagnóstico** , haga clic en **Depurar / Ventanas / Eventos de IntelliTrace**.  
  
     En la ventana **Herramientas de diagnóstico** , busque la pestaña **Eventos** (verá 3 pestañas: **Eventos**, **Uso de memoria**y **Uso de CPU**). La pestaña **Eventos** muestra una lista cronológica que termina con el último evento antes de que el depurador interrumpiera la ejecución. Debería ver un evento denominado **Acceso WordSearchInputs.txt**.  
  
     La siguiente captura de pantalla es de Visual Studio 2015 Update 1.  
  
     ![IntelliTrace&#45;Update1](../debugger/media/intellitrace-update1.png "Update1 de IntelliTrace")  
  
7.  Selecciónelo para expandir los detalles.  
  
     La siguiente captura de pantalla es de Visual Studio 2015 Update 1.  
  
     ![IntelliTraceUpdate1&#45;SingleEvent](../debugger/media/intellitraceupdate1-singleevent.png "IntelliTraceUpdate1 SingleEvent")  
  
     Puede elegir el vínculo de la ruta de acceso para abrirlo. Si la ruta de acceso completa no está disponible, aparece el cuadro de diálogo **Abrir archivo** .  
  
     Haga clic en **Activar depuración histórica**, que establece el contexto del depurador en la hora en que se recopiló el evento seleccionado y muestra datos históricos sobre **Pila de llamadas**, **Locales** y las demás ventanas que participan en el depurador. Si el código fuente está disponible, Visual Studio mueve el puntero al código correspondiente en la ventana de código fuente para que pueda examinarlo.  
  
     La siguiente captura de pantalla es de Visual Studio 2015 Update 1.  
  
     ![HistoricalDebugging&#45;Update1](../debugger/media/historicaldebugging-update1.png "HistoricalDebugging Update1")  
  
8.  Si no encontró el error, intente examinar otros eventos que conduzcan al error. También puede hacer que IntelliTrace registre la información de llamadas de forma que pueda examinar las llamadas a función una por una.  
  
## <a name="using-intellitrace-with-events-and-function-calls"></a>Uso de IntelliTrace solo con eventos y llamadas de función  
 IntelliTrace puede registrar las llamadas de función, además de los eventos. Esto le permite ver el historial de la pila de llamadas y retroceder o avanzar a través de las llamadas de código. IntelliTrace registra los datos como nombres de función, puntos de entrada y salida de la función, y ciertos valores de parámetros y valores devueltos. Consulte [las características de IntelliTrace](../debugger/intellitrace-features.md).  
  
1.  Active la colección de llamadas. (En **Herramientas / Opciones / IntelliTrace / General**, elija **Eventos de IntelliTrace e información de llamadas**. IntelliTrace comenzará a recopilar esta información cuando se inicie la siguiente sesión de depuración.  
  
    > [!TIP]
    >  Esto puede ralentizar la aplicación y aumentar el tamaño de los archivos de registro de IntelliTrace (archivos .iTrace) que guarde en el disco. Para obtener la mayoría de los datos de llamadas, pero minimizar los efectos, registre solo los datos de los módulos que le interesen. Para cambiar el tamaño máximo de los archivos .iTrace, vaya a **Herramientas / Opciones / IntelliTrace / Avanzadas**y especifique la cantidad máxima de espacio en disco. El valor predeterminado es 250 MB.  
  
2.  Empiece a depurar la aplicación de consola de C# creada en la sección anterior. La ejecución se detiene en el punto de interrupción. Si no ve la ventana **Herramientas de diagnóstico** , haga clic en **Depurar / Ventanas / Eventos de IntelliTrace**.  
  
3.  Cambie a la pestaña **Llamadas** .  
  
     Ahora puede ver las llamadas de función de su aplicación, empezando por la llamada raíz (en la solución actual, el punto de entrada Principal) y terminando con el punto en que se interrumpió la ejecución.  
  
     Seleccione una de las llamadas de función y haga doble clic en ella. Debería ver los puntos de entrada y salida de función, así como las llamadas que la llamada actual realizó a otras funciones y los eventos de IntelliTrace generados por la llamada. Si no tiene la depuración histórica activada, esta acción la activa. Para obtener más información sobre la depuración histórica, vea [Historical Debugging](../debugger/historical-debugging.md).  
  
    > [!NOTE]
    >  Algunas llamadas pueden mostrarse atenuadas. Se debe a que IntelliTrace no registró datos de los módulos correspondientes. Para ver estos datos, haga que IntelliTrace recopile datos de esos módulos. Para obtener información sobre cómo especificar módulos, consulte [las características de IntelliTrace](../debugger/intellitrace-features.md).  
  
## <a name="next-steps"></a>Pasos siguientes






