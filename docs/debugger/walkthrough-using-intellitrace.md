---
title: Visualización de eventos con IntelliTrace | Microsoft Docs
description: Aprenda a usar IntelliTrace en Visual Studio Enterprise para recopilar datos sobre eventos específicos, categorías de eventos y llamadas a funciones individuales.
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: e1c9c91a-0009-4c4e-9b4f-c9ab3a6022a7
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6fef839b5473881450581db77a885da158e67bbc
ms.sourcegitcommit: 105e7b5a486262bc92939980383ceee068098a11
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/30/2020
ms.locfileid: "97815755"
---
# <a name="view-events-with-intellitrace-in-visual-studio-enterprise-c-visual-basic"></a>Visualización de eventos con IntelliTrace en Visual Studio Enterprise (C#, Visual Basic)

Puede usar IntelliTrace para recopilar información sobre determinados eventos, categorías de eventos o llamadas a funciones individuales. En los siguientes procedimientos se muestra cómo hacerlo.

Puede usar IntelliTrace en Visual Studio Enterprise, pero no en las ediciones Professional o Community.

## <a name="configure-intellitrace"></a><a name="GettingStarted"></a> Configuración de IntelliTrace

Puede intentar depurar con solo los eventos de IntelliTrace. Los eventos de IntelliTrace son eventos del depurador, excepciones, eventos de .NET Framework y otros eventos del sistema. Antes de iniciar la depuración debe activar o desactivar eventos específicos para controlar los eventos que IntelliTrace registra. Para más información, consulte [Características de IntelliTrace](../debugger/intellitrace-features.md).

- Active el evento de IntelliTrace para el acceso de archivo. Vaya a la página **Herramientas > Opciones > IntelliTrace > Eventos de IntelliTrace** y expanda la categoría **Archivo**. Compruebe la categoría de eventos **Archivo** . Esto hace que se comprueben todos los eventos de archivo (acceso, cierre y eliminación).

## <a name="create-your-app"></a>Creación de una aplicación

1. Cree una aplicación de consola de C#. En el archivo Program.cs, agregue la siguiente declaración de `using` :

    ```csharp
    using System.IO;
    ```

2. Cree un <xref:System.IO.FileStream> en el método Principal, lea de él, ciérrelo y elimine el archivo. Agregue otra línea solo para tener un sitio donde establecer un punto de interrupción:

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

3. Establecer un punto de interrupción en `Console.WriteLine("done");`

## <a name="start-debugging-and-view-intellitrace-events"></a>Inicio de la depuración y visualización de eventos de IntelliTrace

1. Inicie la depuración como de costumbre. (Presione **F5** o haga clic en **Depurar / Iniciar depuración**.)

    > [!TIP]
    > Mantenga abiertas las ventanas **Locales** y **Automático** mientras depura para ver y registrar los valores en estas ventanas.

2. La ejecución se detiene en el punto de interrupción. Si no ve la ventana **Herramientas de diagnóstico**, haga clic en **Depurar > Ventanas > Eventos de IntelliTrace**.

    En la ventana **Herramientas de diagnóstico** , busque la pestaña **Eventos** (verá 3 pestañas: **Eventos**, **Uso de memoria** y **Uso de CPU**). La pestaña **Eventos** muestra una lista cronológica que termina con el último evento antes de que el depurador interrumpiera la ejecución. Debería ver un evento denominado **Acceso WordSearchInputs.txt**.

    La siguiente captura de pantalla es de Visual Studio 2015 Update 1.

    ![Captura de pantalla de la ventana de código de Visual Studio. La ejecución está detenida en un punto de interrupción y la pestaña Eventos de la ventana Herramientas de diagnóstico muestra los eventos.](../debugger/media/intellitrace-update1.png)

3. Selecciónelo para expandir los detalles.

    La siguiente captura de pantalla es de Visual Studio 2015 Update 1.

    ![Captura de pantalla de la pestaña Eventos de la ventana Herramientas de diagnóstico de Visual Studio. Un evento está seleccionado y expandido para mostrar sus detalles.](../debugger/media/intellitraceupdate1-singleevent.png)

    Puede elegir el vínculo de la ruta de acceso para abrirlo. Si la ruta de acceso completa no está disponible, aparece el cuadro de diálogo **Abrir archivo** .

    Haga clic en **Activar depuración histórica**, que establece el contexto del depurador en la hora en que se recopiló el evento seleccionado y muestra datos históricos sobre **Pila de llamadas**, **Locales** y las demás ventanas que participan en el depurador. Si el código fuente está disponible, Visual Studio mueve el puntero al código correspondiente en la ventana de código fuente para que pueda examinarlo.

    La siguiente captura de pantalla es de Visual Studio 2015 Update 1.

    ![Captura de pantalla de la ventana de código de Visual Studio. La ejecución está detenida en un punto de interrupción, hay un evento seleccionado y la línea de código correspondiente está resaltada.](../debugger/media/historicaldebugging-update1.png)

4. Si no encontró el error, intente examinar otros eventos que conduzcan al error. También puede hacer que IntelliTrace registre la información de llamadas de forma que pueda examinar las llamadas a función una por una.

## <a name="next-steps"></a>Pasos siguientes

Puede usar algunas de las características avanzadas de IntelliTrace con depuración histórica:

- Para más información, consulte [Inspeccionar los estados anteriores de las aplicaciones con IntelliTrace](../debugger/view-historical-application-state.md).
- Para aprender a inspeccionar variables y navegar por el código, consulte [Inspeccionar la aplicación con depuración histórica](../debugger/historical-debugging-inspect-app.md).
