---
title: Depuración de un volcado de memoria administrada con analizadores de diagnóstico de .NET | Microsoft Docs
description: Obtenga información sobre cómo usar los analizadores de diagnóstico de .NET en Visual Studio para analizar un volcado de memoria administrada.
ms.custom: SEO-VS-2021
ms.date: 04/21/2021
ms.topic: how-to
dev_langs:
- CSharp
- VB
helpviewer_keywords:
- analyzers
- dump debugging
- debugging managed memory dump
- debugging [Visual Studio]
author: poppastring
ms.author: madownie
manager: andster
monikerRange: '>= vs-2019'
ms.workload:
- multiple
ms.openlocfilehash: 083095ad534aa6b9131ba103178313cb1cdc4b7c
ms.sourcegitcommit: 925db7adb9cb554b081c7e727d09680d4863feed
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/24/2021
ms.locfileid: "107953082"
---
# <a name="how-to-debug-a-managed-memory-dump-with-net-diagnostic-analyzers"></a>Depuración de un volcado de memoria administrada con analizadores de diagnóstico de .NET



En este tutorial, aprenderá lo siguiente:

> [!div class="checklist"]
> * Abrir un volcado de memoria
> * Seleccionar y ejecutar analizadores en el volcado
> * Revisar los resultados de los analizadores
> * Navegar al código problemático


En el ejemplo descrito en este artículo, el problema es que la aplicación no responde a las solicitudes de forma oportuna. 


## <a name="opening-a-memory-dump-in-visual-studio"></a>Apertura de un volcado de memoria en Visual Studio

1. Abra el volcado de memoria en Visual Studio mediante el comando de menú **Archivo > Abrir > Archivo** y seleccione el volcado de memoria.

1. Observe en la página de resumen del volcado de memoria una nueva **acción** denominada **Run Diagnostics Analysis** (Ejecutar análisis de diagnóstico).

   ![Acción: Análisis de diagnóstico](../debugger/media/diagnostic-analyzer-dump-summary-actions.png)

1. Seleccione esta acción para iniciar el depurador y abrir la nueva página **Diagnostic Analysis** (Análisis de diagnóstico) con una lista de opciones de analizador disponibles, organizadas según el síntoma subyacente.


## <a name="select-and-execute-analyzers-against-the-dump"></a>Selección y ejecución de analizadores en el volcado

Para investigar estos síntomas, las mejores opciones están disponibles en **Process Responsiveness** (Capacidad de respuesta del proceso), ya que coincide mejor con el problema de este ejemplo.

   ![Selección de analizadores de diagnóstico](../debugger/media/diagnostic-analyzer-diagnostics-analysis-window.png)

1. Haga clic en el botón **Analyze** (Analizar) para iniciar el proceso de investigación. 

1. El analizador presentará resultados basados en la combinación de información de proceso y datos de CLR capturados en el volcado de memoria.
 
## <a name="review-the-results-of-the-analyzers"></a>Revisión de los resultados de los analizadores

1. En este caso, el analizador ha encontrado dos errores. Seleccione el resultado del analizador para ver el **resumen de análisis** y la **corrección** sugerida.

   ![Resultados de los analizadores de diagnóstico](../debugger/media/diagnostic-analyzer-diagnostics-analysis-results.png)

1. En el **resumen de análisis** se indica que "El grupo de subprocesos de CLR está experimentando un colapso&quot;. Esta información sugiere que CLR ha usado actualmente todos los subprocesos del grupo de subprocesos disponibles, lo que significa que el servicio no puede responder a ninguna solicitud nueva hasta que se libere un subproceso.

    > [!NOTE] 
    > La **corrección** en este caso es &quot;Do not synchronously wait on Monitors, Events, Task, or any other objects that may block your thread. See if you can update the method to be asynchronous.&quot; (No esperar sincrónicamente en monitores, eventos, tareas o cualquier otro objeto que pueda bloquear el subproceso. Vea si puede actualizar el método para que sea asincrónico").

## <a name="navigating-to-the-problematic-code"></a>Navegación al código problemático

Mi siguiente trabajo es buscar ese código problemático.

1. Al hacer clic en el vínculo **Mostrar pila de llamadas**, Visual Studio cambiará inmediatamente a los subprocesos que presentan este comportamiento.

1. En la ventana **Pila de llamadas** se mostrarán los métodos que pueden distinguir rápidamente entre mi código (SyncOverAsyncExmple. *) y el código de Framework (System.* ).

   ![Vínculo de los analizadores de diagnóstico a la pila de llamadas](../debugger/media/diagnostic-analyzer-call-stack.png)

1. Cada marco de pila de llamadas corresponde a un método y, al hacer doble clic en los marcos de pila, Visual Studio navegará hasta el código que remitió directamente a este escenario en este subproceso.

1. En este ejemplo, no hay símbolos ni código, pero en la página **Símbolos no cargados** puede seleccionar la opción **[Descompilar código fuente](../debugger/decompilation.md)** .

   ![Descompilación](../debugger/media/diagnostic-analyzer-decompilation.png)

1. En el origen descompilado siguiente, es evidente que una tarea asincrónica (ConsumeThreadPoolThread) llama a una función de bloqueo sincrónica.

    > [!NOTE]  
    > El método "DoSomething()" que contiene un método WaitHandle.WaitOne, que bloquea el subproceso del grupo de subprocesos actual hasta que recibe una señal.

   Para mejorar la capacidad de respuesta de las aplicaciones, es importante quitar el código sincrónico de bloqueo de todos los contextos asincrónicos.

   ![Análisis del código descompilado](../debugger/media/diagnostic-analyzer-decompiled-code.png)


## <a name="see-also"></a>Consulte también

* [Uso de archivos de volcado de memoria en el depurador](../debugger/using-dump-files.md)
* [Generación de código fuente a partir de ensamblados .NET durante la depuración](../debugger/decompilation.md)
* [Especificación de archivos de código fuente y símbolos (.pdb)](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)
