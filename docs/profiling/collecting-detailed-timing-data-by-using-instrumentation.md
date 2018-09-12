---
title: Recopilar datos de control de tiempo detallados mediante la instrumentación | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- Profiling Tools,instrumentation method
- instrumentation profiling method
ms.assetid: e9deb370-c459-45ac-84d3-14d646590d05
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: a86b74787a574a1ad54b228c117f6cb598f1eb2b
ms.sourcegitcommit: 6944ceb7193d410a2a913ecee6f40c6e87e8a54b
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/05/2018
ms.locfileid: "43775170"
---
# <a name="collect-detailed-timing-data-by-using-instrumentation"></a>Recopilar datos de control de tiempo detallados mediante la instrumentación
El método de instrumentación de herramientas de generación de perfiles [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] inserta código de generación de perfiles en una copia de un módulo. El código registra cada entrada, salida y llamada de función a las funciones del módulo durante una ejecución de la generación de perfiles. El método de instrumentación es útil para recopilar información de tiempo detallada sobre una sección del código y para entender el impacto de las operaciones de entrada y salida en el rendimiento de la aplicación.  
  
 Puede especificar el método de instrumentación utilizando uno de los procedimientos siguientes:  
  
-   En la primera página del Asistente para generación de perfiles, seleccione **Instrumentación**.  
  
-   En la barra de herramientas **Explorador de rendimiento** , en la lista **Método** , haga clic en **Instrumentación**.  
  
-   En la página **General** del cuadro de diálogo de propiedades de la sesión de rendimiento, seleccione **Instrumentación**.  
  
## <a name="common-tasks"></a>Tareas comunes
 Puede especificar opciones adicionales en el cuadro de diálogo _Páginas de propiedades de_**sesión de rendimiento** de la sesión de rendimiento. Para abrir este cuadro de diálogo:  
  
-   En el **Explorador de rendimiento**, haga clic con el botón secundario del mouse en el nombre de la sesión y, a continuación, haga clic en **Propiedades**.  
  
 Las tareas de la tabla siguiente describen las opciones que puede especificar en el cuadro de diálogo _Páginas de propiedades de_**sesión de rendimiento** cuando genere perfiles usando el método de instrumentación.  
  
|Tarea|Contenido relacionado|  
|----------|---------------------|  
|En la página **General** , agregue los datos de duración y asignación de memoria .NET y especifique los detalles de nomenclatura del archivo de datos de generación de perfiles generado (.vsp).|-   [Recopilación de datos referentes a la asignación y duración de memoria de .NET](../profiling/collecting-dotnet-memory-allocation-and-lifetime-data.md)<br />-   [Cómo: establecer opciones de nombre de archivo de datos de rendimiento](../profiling/how-to-set-performance-data-file-name-options.md)|  
|En la página **Iniciar** , si tiene varios proyectos .exe en su solución, especifique el inicio de la aplicación, así como el orden de inicio.|-   [Cómo: Especificar el binario de inicio](../profiling/how-to-specify-the-binary-to-start.md)|  
|En la página **Binarios** , especifique una ubicación para las copias instrumentadas de los módulos. De forma predeterminada, los binarios originales se mueven a una carpeta de copia de seguridad.|-   [Cómo: Cambiar la ubicación de binarios instrumentados](../profiling/how-to-relocate-instrumented-binaries.md)|  
|En la página **Interacción de capas** , agregue los datos de la llamada ADO.NET a la ejecución de la generación de perfiles.|-   [Recopilación de datos de interacción de capas](../profiling/collecting-tier-interaction-data.md)|  
|En la página **Instrumentación** , excluya las funciones pequeñas de la generación de perfiles para reducir la sobrecarga de generación de perfiles, el código JavaScript de perfiles en páginas web ASP.NET y especifique comandos para ejecutarse en el símbolo del sistema antes y después del proceso de instrumentación.|-   [Cómo: Excluir o incluir funciones cortas en la instrumentación](../profiling/how-to-exclude-or-include-short-functions-from-instrumentation.md)<br />-   [Cómo: Generar perfiles de código de JavaScript en páginas web](../profiling/how-to-profile-javascript-code-in-web-pages.md)<br />-   [Cómo: Especificar comandos anteriores y posteriores a la instrumentación](../profiling/how-to-specify-pre-and-post-instrument-commands.md)|  
|En la página **Contadores de CPU** , especifique uno o varios contadores de rendimiento de procesador para agregar a los datos de generación de perfiles.|-   [Cómo: Recopilar datos de contadores de CPU](../profiling/how-to-collect-cpu-counter-data.md)|  
|En la página **Eventos de Windows** , seleccione uno o varios eventos de seguimiento de eventos para Windows (ETW) para recopilar con los datos de muestreo.|-   [Cómo: Recopilar datos de Seguimiento de eventos para Windows (ETW)](../profiling/how-to-collect-event-tracing-for-windows-etw-data.md)|  
|En la página **Contadores de Windows** , especifique uno o varios contadores de rendimiento de sistema operativo para agregar a los datos de generación de perfiles como marcas.|-   [Cómo: Recopilar datos de contadores de Windows](../profiling/how-to-collect-windows-counter-data.md)|  
|En la página **Avanzadas** , especifique las opciones adicionales que se van a pasar al programa de instrumentación VSInstr como, por ejemplo, las opciones para incluir o excluir funciones específicas.|-   [Cómo: Especificar opciones de instrumentación adicionales](../profiling/how-to-specify-additional-instrumentation-options.md)<br />-   [Cómo: Limitar la instrumentación a funciones específicas](../profiling/how-to-limit-instrumentation-to-specific-functions.md)<br />-   [VSInstr](../profiling/vsinstr.md)|