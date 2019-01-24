---
title: Ver los eventos de IntelliTrace | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: e1c9c91a-0009-4c4e-9b4f-c9ab3a6022a7
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 86410567a194753db2001fbd5fba870bb89d7930
ms.sourcegitcommit: 01185dadd2fa1f9a040d2a366869f1a5e1d18e0f
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 01/11/2019
ms.locfileid: "54227998"
---
# <a name="view-events-with-intellitrace-in-visual-studio-enterprise-c-visual-basic"></a>Ver los eventos con IntelliTrace en Visual Studio Enterprise (C#, Visual Basic)

Puede usar IntelliTrace para recopilar información sobre determinados eventos, categorías de eventos o llamadas a funciones individuales. En los siguientes procedimientos se muestra cómo hacerlo.  
  
Puede usar IntelliTrace en Visual Studio Enterprise, pero no en las ediciones Professional o Community.  
  
##  <a name="GettingStarted"></a> Configurar IntelliTrace  

 Puede intentar depurar con solo los eventos de IntelliTrace. Los eventos de IntelliTrace son eventos del depurador, excepciones, eventos de .NET Framework y otros eventos del sistema. Antes de iniciar la depuración debe activar o desactivar eventos específicos para controlar los eventos que IntelliTrace registra. Para obtener más información, consulte [las características de IntelliTrace](../debugger/intellitrace-features.md).  
  
 - Active el evento de IntelliTrace para el acceso de archivo. Vaya a la página **Herramientas > Opciones > IntelliTrace > Eventos de IntelliTrace** y expanda la categoría **Archivo**. Compruebe la categoría de eventos **Archivo** . Esto hace que se comprueben todos los eventos de archivo (acceso, cierre y eliminación).

## <a name="create-your-app"></a>Creación de una aplicación
  
1.  Cree una aplicación de consola de C#. En el archivo Program.cs, agregue la siguiente declaración de `using` :  
  
    ```csharp  
    using System.IO;  
    ```  
  
2.  Cree un <xref:System.IO.FileStream> en el método Principal, lea de él, ciérrelo y elimine el archivo. Agregue otra línea solo para tener un sitio donde establecer un punto de interrupción:  
  
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
  
3.  Establecer un punto de interrupción en `Console.WriteLine("done");`  

## <a name="start-debugging-and-view-intellitrace-events"></a>Inicie la depuración y ver los eventos de IntelliTrace
  
1.  Inicie la depuración como de costumbre. Presione **F5** o haga clic en **Depurar > Iniciar depuración**.  
  
    > [!TIP]
    >  Mantenga abiertas las ventanas **Locales** y **Automático** mientras depura para ver y registrar los valores en estas ventanas.  
  
2.  La ejecución se detiene en el punto de interrupción. Si no ve la ventana **Herramientas de diagnóstico**, haga clic en **Depurar > Ventanas > Eventos de IntelliTrace**.  
  
     En la ventana **Herramientas de diagnóstico** , busque la pestaña **Eventos** (verá 3 pestañas: **Eventos**, **Uso de memoria**y **Uso de CPU**). La pestaña **Eventos** muestra una lista cronológica que termina con el último evento antes de que el depurador interrumpiera la ejecución. Debería ver un evento denominado **Acceso WordSearchInputs.txt**.  
  
     La siguiente captura de pantalla es de Visual Studio 2015 Update 1.  
  
     ![IntelliTrace&#45;Update1](../debugger/media/intellitrace-update1.png "IntelliTrace-Update1")  
  
3.  Selecciónelo para expandir los detalles.  
  
     La siguiente captura de pantalla es de Visual Studio 2015 Update 1.  
  
     ![IntelliTraceUpdate1&#45;SingleEvent](../debugger/media/intellitraceupdate1-singleevent.png "IntelliTraceUpdate1-SingleEvent")  
  
     Puede elegir el vínculo de la ruta de acceso para abrirlo. Si la ruta de acceso completa no está disponible, aparece el cuadro de diálogo **Abrir archivo** .  
  
     Haga clic en **Activar depuración histórica**, que establece el contexto del depurador en la hora en que se recopiló el evento seleccionado y muestra datos históricos sobre **Pila de llamadas**, **Locales** y las demás ventanas que participan en el depurador. Si el código fuente está disponible, Visual Studio mueve el puntero al código correspondiente en la ventana de código fuente para que pueda examinarlo.  
  
     La siguiente captura de pantalla es de Visual Studio 2015 Update 1.  
  
     ![HistoricalDebugging&#45;Update1](../debugger/media/historicaldebugging-update1.png "HistoricalDebugging-Update1")  
  
4.  Si no encontró el error, intente examinar otros eventos que conduzcan al error. También puede hacer que IntelliTrace registre la información de llamadas de forma que pueda examinar las llamadas a función una por una. 
  
## <a name="next-steps"></a>Pasos siguientes

Puede usar algunas de las características avanzadas de IntelliTrace con depuración histórica:

 - Para ver las instantáneas, vea [inspeccionar el estado anterior de aplicación con IntelliTrace](../debugger/view-historical-application-state.md)
 - Para obtener información sobre cómo inspeccionar variables y navegar por el código, consulte [inspeccionar la aplicación con depuración histórica](../debugger/historical-debugging-inspect-app.md)