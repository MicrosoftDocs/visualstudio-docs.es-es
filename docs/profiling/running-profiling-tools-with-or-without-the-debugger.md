---
title: Ejecución de herramientas de generación de perfiles con o sin el depurador | Microsoft Docs
ms.date: 5/26/2020
ms.topic: conceptual
ms.assetid: 3fcdccad-c1bd-4c67-bcec-bf33a8fb5d63
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4b3d50f8fcad0294adec032322229e9dd6cedac2
ms.sourcegitcommit: 8e5b0106061bb43247373df33d0850ae68457f5e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/18/2020
ms.locfileid: "88508085"
---
# <a name="run-profiling-tools-with-or-without-the-debugger"></a>Ejecutar herramientas de generación de perfiles con o sin el depurador

Visual Studio ofrece varias herramientas de generación de perfiles y medición del rendimiento. Algunas herramientas, como Uso de CPU y Uso de memoria, pueden ejecutarse con o sin el depurador, y en las configuraciones de compilación de depuración o de versión. Las herramientas del Generador de perfiles de rendimiento, como Escala de tiempo de la aplicación, pueden ejecutarse en compilaciones de depuración o de versión. Las herramientas integradas del depurador, como la ventana Herramientas de diagnóstico y la pestaña Eventos solo se ejecutan durante las sesiones de depuración.

>[!NOTE]
>Puede usar las herramientas de rendimiento sin depurador con Windows 7 y versiones posteriores. Se necesita Windows 8 o versiones posteriores para ejecutar las herramientas de generación de perfiles integradas del depurador.

El Generador de perfiles de rendimiento sin depurador y las Herramientas de diagnóstico integradas en el depurador proporcionan información y experiencias diferentes. Las herramientas integradas del depurador muestran los puntos de interrupción y los valores de variable. Las herramientas sin depurador ofrecen resultados más cercanos a la experiencia del usuario final.

Para ayudarlo a decidir qué herramientas y resultados debe utilizar, tenga en cuenta lo siguiente:

- Los problemas de rendimiento externo, como problemas de la capacidad de respuesta de la red o de E/S de archivos, no se diferenciarán demasiado en las herramientas con o sin depurador.
- En el caso de problemas causados por llamadas con gran consumo de CPU, puede haber diferencias de rendimiento considerables entre las compilaciones de versión y de depuración. Compruebe si el problema existe en las compilaciones de versión.
- Si el problema se produce solo durante las compilaciones de depuración, probablemente no necesitará ejecutar las herramientas sin depurador. En el caso de problemas de compilaciones de versión, deberá decidir si las herramientas del depurador le ayudarán en la investigación.
- Las compilaciones de versión proporcionan optimizaciones como la inclusión de llamadas a funciones y constantes, la eliminación de rutas de acceso a código sin usar y el almacenamiento de variables de manera que no las pueda usar el depurador. Los números de rendimiento de las herramientas integradas del depurador son menos precisos, porque las compilaciones de depuración carecen de estas optimizaciones.
- El propio depurador cambia los tiempos de rendimiento, ya que realiza operaciones de depurador necesarias como interceptar excepciones y modular eventos de carga.
- Los números de rendimiento de la compilación de versión de las herramientas del Generador de perfiles de rendimiento son más precisos y exactos. Los resultados de la herramienta integrada del depurador son más útiles si se comparan con otras medidas relacionadas con la depuración.

## <a name="collect-profiling-data-while-debugging"></a><a name="BKMK_Quick_start__Collect_diagnostic_data"></a> Recopilar datos de generación de perfiles durante la depuración

Al comenzar la depuración en Visual Studio seleccionando **Depurar** > **Iniciar depuración** o presionando **F5**, la ventana **Herramientas de diagnóstico** aparece de forma predeterminada. Para abrirla manualmente, seleccione **Depurar** > **Ventanas** > **Mostrar herramientas de diagnóstico**. En la ventana **Herramientas de diagnóstico** se muestra información sobre el uso de CPU, la memoria de proceso y los eventos.

![Instantánea de la ventana Herramientas de diagnóstico](../profiling/media/diagnostictoolswindow.png "Ventana Herramientas de diagnóstico")

- Use el icono **Configuración** en la barra de herramientas para seleccionar si quiere ver el **Uso de memoria**, el **Análisis de UI**, y el **Uso de CPU**.

- Seleccione **Configuración** en la lista desplegable **Configuración** para abrir las **páginas de propiedades de las Herramientas de diagnóstico** con más opciones.

- Si ejecuta Visual Studio Enterprise, puede habilitar o deshabilitar IntelliTrace en **Herramientas** > **Opciones** > **IntelliTrace**.

La sesión de diagnóstico termina cuando se detiene la depuración.

### <a name="the-events-tab"></a>La pestaña Eventos

Durante una sesión de depuración, en la pestaña Eventos de la ventana Herramientas de diagnóstico se enumeran los eventos de diagnóstico que se producen. Los prefijos de categoría: *Punto de interrupción*, *Archivo* y otros, le permiten examinar rápidamente la lista en busca de una categoría u omitir las categorías que no le interesan.

Use la lista desplegable **Filtro** para filtrar los eventos dentro y fuera de la vista activando o desactivando categorías de eventos concretas.

![Captura de pantalla de filtro de eventos de diagnóstico](../profiling/media/diagnosticeventfilter.png "Filtro de eventos de diagnóstico")

Use el cuadro de búsqueda para encontrar una cadena concreta en la lista de eventos. Estos son los resultados de una búsqueda de la cadena *name* que coincide con cuatro eventos:

![Captura de pantalla de la búsqueda de eventos de diagnóstico](../profiling/media/diagnosticseventsearch.png "Búsqueda de eventos de diagnóstico")

Para más información, consulte [Búsqueda y filtrado de la pestaña Eventos de la ventana de herramientas de diagnóstico](https://devblogs.microsoft.com/devops/searching-and-filtering-the-events-tab-of-the-diagnostic-tools-window/).

## <a name="collect-profiling-data-without-debugging"></a>Recopilar datos de generación de perfiles sin depurar

Para recopilar datos de rendimiento sin depuración, puede ejecutar las herramientas del Generador de perfiles de rendimiento.

1. Con un proyecto abierto en Visual Studio, establezca la configuración de la solución en  **Versión** y seleccione  **Depurador local de Windows**  (o  **Máquina local**) como destino de la implementación.

1. Seleccione **Depurar** > **Generador de perfiles de rendimiento**, o bien presione **Alt**+**F2**.

1. En la página de inicio de las herramientas de diagnóstico, elija una o varias herramientas para ejecutar. Solo se muestran las herramientas que se pueden aplicar para el tipo de proyecto, el sistema operativo y el lenguaje de programación. Haga clic en **Mostrar todas las herramientas** para ver también herramientas que están deshabilitadas para esta sesión de diagnóstico.

   ![Captura de pantalla de las herramientas de diagnóstico](../profiling/media/diaghubsummarypage.png "DIAG_SelectTool")

1. Para iniciar la sesión de diagnóstico, haga clic en **Iniciar**.

   Mientras se ejecuta la sesión, algunas herramientas muestran gráficos de datos en tiempo real en la página de las herramientas de diagnóstico, así como controles para pausar y reanudar la recopilación de datos.

    ![Captura de pantalla de la recopilación de datos en el centro de Rendimiento y diagnósticos](../profiling/media/diaghubcollectdata.png "Centro de recopilación de datos")

1. Para finalizar la sesión de diagnóstico, haga clic en **Detener recopilación**.

   Los datos analizados se muestran en la página **Informe**.

Puede guardar los informes y abrirlos desde la lista **Sesiones abiertas recientemente** de la página de inicio de Herramientas de diagnóstico.

![Captura de pantalla de la lista Sesiones abiertas recientemente de Herramientas de diagnóstico](../profiling/media/diaghubopenexistingdiagsession.png "PDHUB_OpenExistingDiagSession")

## <a name="collect-profiling-data-from-the-command-line"></a>Recopilación de datos de generación de perfiles desde la línea de comandos

Para medir los datos de rendimiento desde la línea de comandos, puede usar VSDiagnostics.exe, que se incluye en Visual Studio o en las Herramientas remotas. Esta herramienta resulta útil para capturar seguimientos de rendimiento en sistemas en los que no está instalado Visual Studio, o para generar scripts de la colección de seguimientos de rendimiento. Para obtener instrucciones detalladas, vea [Medir el rendimiento de la aplicación desde la línea de comandos](../profiling/profile-apps-from-command-line.md).