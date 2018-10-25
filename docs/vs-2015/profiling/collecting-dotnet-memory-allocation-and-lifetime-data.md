---
title: Recopilar datos de referentes a la asignación y duración de memoria de .NET | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- .NET memory profiling method
- Profiling Tools,.NET memory method
ms.assetid: 62a6dd5f-db66-4456-9d57-f8913dbfe4d5
caps.latest.revision: 23
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5e0bda22a63b5286db9336bc0924ce11bc05e2bc
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49844580"
---
# <a name="collecting-net-memory-allocation-and-lifetime-data"></a>Recopilar datos referentes a la asignación y duración de memoria de .NET
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Las herramientas de generación de perfiles [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] admiten la recopilación de datos de duración de objetos y de asignación de memoria de .NET, lo cual lo ayuda a detectar problemas de rendimiento relacionados con la memoria de la aplicación.  
  
- Los datos sobre la asignación de memoria de .NET incluyen el tamaño y el número de los objetos de memoria de .NET Framework que se asignaron.  
  
- Los datos de duración de objetos incluyen el tamaño y el número de los objetos de memoria de .NET Framework que se recuperaron en las tres generaciones de recolección de elementos no utilizados.  
  
  **Requisitos**  
  
- [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)], [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)], [!INCLUDE[vsPro](../includes/vspro-md.md)]  
  
> [!NOTE]
>  Las características de seguridad mejoradas en Windows 8 y Windows Server 2012 requirieron cambios significativos en la forma en que el generador de perfiles de Visual Studio recopila datos en estas plataformas. Las aplicaciones de la Tienda Windows también requieren nuevas técnicas de recolección. Consulte [Herramientas de rendimiento en aplicaciones de Windows 8 y Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).  
  
 Puede recopilar datos mediante el método de muestreo o de generación de perfiles de instrumentación.  
  
-   Cuando utiliza el método de muestreo, el generador de perfiles realiza el seguimiento de todas las asignaciones de memoria de .NET y de los objetos generados por el proceso que se ha iniciado o se ha adjuntado.  
  
-   Cuando utiliza el método de instrumentación, el generador de perfiles realiza el seguimiento solo de las asignaciones de memoria de .NET y de los objetos generados por los módulos instrumentados.  
  
> [!IMPORTANT]
>  Cuando recopila datos de memoria de .NET (asignaciones, duraciones de objeto o ambos) mediante el método de muestreo, se omiten todos los eventos de muestreo especificados por el usuario y se utilizan los eventos de asignación de memoria apropiados para recopilar datos.  
  
 Si habilita la generación de perfiles de asignación de memoria de .NET, también habilita la vista Asignación. Si habilita la generación de perfiles de datos de duración de .NET, también habilita la vista Duración de objetos. Para obtener más información, consulte [Vista Asignación](../profiling/dotnet-memory-allocations-view.md) y [Vista Duración de objetos](../profiling/object-lifetime-view.md).  
  
 Para obtener información sobre cómo recopilar datos de memoria de .NET mediante las herramientas de la línea de comandos de las herramientas de generación de perfiles, consulte Utilizar métodos de memoria de .NET para recopilar datos de asignación de memoria y de duración de objetos en [Uso de métodos de generación de perfiles desde la línea de comandos](../profiling/using-profiling-methods-to-collect-performance-data-from-the-command-line.md).  
  
### <a name="to-collect-net-memory-data"></a>Para recopilar datos de memoria de .NET  
  
1.  En el **Explorador de rendimiento**, haga clic con el botón derecho del mouse en la sesión de rendimiento y, después, haga clic en **Propiedades**.  
  
2.  En el cuadro de diálogo _Páginas de propiedades de_**sesión de rendimiento**, haga clic en la pestaña **General** y seleccione la casilla **Recopilar información de asignación de objetos .NET**.  
  
3.  Para recopilar datos de duración de objetos .NET, seleccione la casilla **Recopilar también la información de duración de los objetos .NET**.  
  
## <a name="common-tasks"></a>Tareas comunes  
 Puede especificar opciones adicionales en el cuadro de diálogo _Páginas de propiedades de_**sesión de rendimiento** de la sesión de rendimiento. Para abrir este cuadro de diálogo:  
  
- En el **Explorador de rendimiento**, haga clic con el botón secundario del mouse en el nombre de la sesión y, a continuación, haga clic en **Propiedades**.  
  
  Las tareas de la tabla siguiente describen las opciones que puede especificar en el cuadro de diálogo _Páginas de propiedades de_**sesión de rendimiento** cuando recopile datos de memoria de .NET.  
  
|Tarea|Contenido relacionado|  
|----------|---------------------|  
|En la página **General** , especifique los detalles de nomenclatura del archivo de datos de generación de perfiles generado (.vsp).|-   [Recopilar datos de duración y de asignación de memoria de .NET](../profiling/collecting-dotnet-memory-allocation-and-lifetime-data.md)<br />-   [Cómo: Establecer opciones de nombre de archivo de datos de rendimiento](../profiling/how-to-set-performance-data-file-name-options.md)|  
|En la página **Iniciar**, elija la aplicación que quiere iniciar si tiene varios proyectos .exe en la solución de código.|-   [Recopilar datos de interacción de capas](../profiling/collecting-tier-interaction-data.md)|  
|En la página **Interacción de capas** , agregue los datos de la llamada ADO.NET a la ejecución de la generación de perfiles.|-   [Recopilar datos de interacción de capas](../profiling/collecting-tier-interaction-data.md)|  
|En la página **Eventos de Windows**, especifique uno o varios eventos de seguimiento de eventos para Windows (ETW) para recopilar con los datos de muestreo.|-   [Cómo: Recopilar datos de seguimiento de eventos para Windows (ETW)](../profiling/how-to-collect-event-tracing-for-windows-etw-data.md)|  
|En la página **Contadores de Windows** , especifique uno o varios contadores de rendimiento de sistema operativo para agregar a los datos de generación de perfiles como marcas.|-   [Cómo: recopilar datos de contadores de Windows](../profiling/how-to-collect-windows-counter-data.md)|  
|En la página **Avanzado**, especifique la versión del runtime de .NET Framework de la cual quiere generar el perfil si los módulos de aplicación utilizan varias versiones. De forma predeterminada, se genera el perfil de la primera versión cargada.|-   [Cómo: Especificar el runtime de .NET Framework](../profiling/how-to-specify-the-dotnet-framework-runtime.md)|  
  
## <a name="instrumentation-tasks"></a>Tareas de instrumentación  
 Las tareas de la tabla siguiente son opciones del cuadro de diálogo **Páginas de propiedades** que son específicas de la generación de perfiles con el método de instrumentación.  
  
|Tarea|Contenido relacionado|  
|----------|---------------------|  
|En la página **Binarios** , especifique una ubicación para las copias instrumentadas de los módulos. De forma predeterminada, los binarios originales se mueven a una carpeta de copia de seguridad.|-   [Cómo: Cambiar la ubicación de binarios instrumentados](../profiling/how-to-relocate-instrumented-binaries.md)|  
|En la página **Instrumentación** , excluya las funciones pequeñas de la generación de perfiles para reducir la sobrecarga de generación de perfiles, el código JavaScript de perfiles en páginas web ASP.NET y especifique comandos para ejecutarse en el símbolo del sistema antes y después del proceso de instrumentación.|-   [Cómo: Excluir o incluir funciones cortas en la instrumentación](../profiling/how-to-exclude-or-include-short-functions-from-instrumentation.md)<br />-   [Cómo: Generar perfiles de código de JavaScript en páginas web](../profiling/how-to-profile-javascript-code-in-web-pages.md)<br />-   [Cómo: Especificar comandos anteriores y posteriores a la instrumentación](../profiling/how-to-specify-pre-and-post-instrument-commands.md)|  
|En la página **Contadores de CPU** , especifique uno o varios contadores de rendimiento de procesador para agregar a los datos de generación de perfiles.|-   [Cómo: Recopilar datos de contadores de CPU](../profiling/how-to-collect-cpu-counter-data.md)|  
|En la página **Avanzado**, especifique las opciones adicionales de VSInstr que quiera, como, por ejemplo, las opciones para incluir o excluir funciones específicas. Para obtener más información sobre las opciones de VSInstr, consulte [VSInstr](../profiling/vsinstr.md)|-   [Cómo: Especificar opciones de instrumentación adicionales](../profiling/how-to-specify-additional-instrumentation-options.md)<br />-   [Cómo: Limitar la instrumentación a funciones específicas](../profiling/how-to-limit-instrumentation-to-specific-functions.md)|  
  
## <a name="see-also"></a>Vea también  
 [Configurar sesiones de rendimiento](../profiling/configuring-performance-sessions.md)   
 [Cómo: Elegir métodos de colección](../profiling/how-to-choose-collection-methods.md)   
 [Propiedades de la sesión de rendimiento](../profiling/performance-session-properties.md)



