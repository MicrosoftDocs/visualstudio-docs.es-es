---
title: "Recopilar datos referentes a la asignaci&#243;n y duraci&#243;n de memoria de .NET | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "método de generación de perfiles de memoria de .NET"
  - "herramientas de generación de perfiles, método de memoria .NET"
ms.assetid: 62a6dd5f-db66-4456-9d57-f8913dbfe4d5
caps.latest.revision: 18
caps.handback.revision: 18
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Recopilar datos referentes a la asignaci&#243;n y duraci&#243;n de memoria de .NET
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Las herramientas de generación de perfiles de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] admiten la recolección de datos de asignación de memoria y de duración de objetos de .NET, lo que ayuda a detectar los problemas relacionados con el rendimiento en la aplicación.  
  
-   Entre los datos acerca de la asignación de memoria de .NET se incluyen el tamaño y el número de objetos de memoria de .NET Framework asignados.  
  
-   Entre los datos de duración de objetos se incluyen el tamaño y el número de objetos de memoria de .NET Framework que se reclamaron en las tres generaciones de la recolección de elementos no utilizados.  
  
 **Requisitos**  
  
-   [!INCLUDE[vsUltLong](../code-quality/includes/vsultlong_md.md)], [!INCLUDE[vsPreLong](../code-quality/includes/vsprelong_md.md)], [!INCLUDE[vsPro](../code-quality/includes/vspro_md.md)]  
  
> [!NOTE]
>  Las características de seguridad mejoradas en Windows 8 y Windows Server 2012 requirieron cambios significativos en la forma en que el generador de perfiles de Visual Studio recopila datos en estas plataformas.  Las aplicaciones de la Tienda Windows también requieren nuevas técnicas de recolección.  Vea [Generar perfiles de aplicaciones de Windows 8 y Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).  
  
 Los datos se pueden recopilar con el método de muestreo o de instrumentación de generación de perfiles.  
  
-   Cuando se usa el método de muestreo, el generador de perfiles realiza el seguimiento de todos los objetos y las asignaciones de memoria de .NET que genera el proceso iniciado o adjunto.  
  
-   Cuando se usa el método de instrumental, el generador de perfiles solamente realiza el seguimiento de los objetos y las asignaciones de memoria de .NET que generan los módulos instrumentados.  
  
> [!IMPORTANT]
>  Cuando se recopilan datos de memoria de .NET \(asignaciones, duraciones de objeto o ambos\) mediante el método de muestreo, se omiten todos los eventos de muestreo especificados por el usuario y se utilizan los eventos de asignación de memoria apropiados para recopilar datos.  
  
 Si habilita la generación de perfiles de la asignación de memoria de .NET, también habilita la vista Asignación.  Si habilita la generación de perfiles de los datos de duración de .NET, también habilita la vista Duración de los objetos.  Para obtener más información, vea [Asignaciones \(Vista\)](../profiling/dotnet-memory-allocations-view.md) y [Vista Duración del objeto](../profiling/object-lifetime-view.md).  
  
 Para obtener información sobre cómo recopilar datos de memoria de .NET mediante las herramientas de línea de comandos de las herramientas de generación de perfiles, vea Usar métodos de memoria de .NET para recopilar datos de asignación de memoria y duración de objetos en [Usar los métodos de generación de perfiles desde la línea de comandos](../profiling/using-profiling-methods-to-collect-performance-data-from-the-command-line.md).  
  
### Para recopilar datos de memoria de .NET  
  
1.  En el **Explorador de rendimiento**, haga clic con el botón secundario del mouse en la sesión de rendimiento y, a continuación, haga clic en **Propiedades**.  
  
2.  En el cuadro de diálogo de *Performance Session***Páginas de propiedades** , haga clic en la pestaña de **General** , y active la casilla de **Recopilar información de asignación de objetos .NET** .  
  
3.  Para recopilar datos de duración de objetos de .NET, active la casilla **Recopilar también la información de duración de objetos .NET**.  
  
## Tareas comunes  
 Puede especificar opciones adicionales en el cuadro de diálogo de *Performance Session***Páginas de propiedades** de la sesión de rendimiento.  Para abrir este cuadro de diálogo:  
  
-   En el **Explorador de rendimiento**, haga clic con el botón secundario en el nombre de la sesión de rendimiento y, a continuación, haga clic en **Propiedades**.  
  
 Las tareas de la tabla siguiente describen opciones que puede especificar en el cuadro de diálogo de *Performance Session***Páginas de propiedades** al recopilar datos de memoria de .NET.  
  
|Tarea|Contenido relacionado|  
|-----------|---------------------------|  
|En la página **General**, especifique los detalles de nomenclatura del archivo de datos de generación de perfiles \(.vsp\) que se crea.|-   [Collecting .NET Memory Allocation and Lifetime Data](../profiling/collecting-dotnet-memory-allocation-and-lifetime-data.md)<br />-   [Cómo: Establecer opciones de nombre de archivo de datos de generación de perfiles](../profiling/how-to-set-performance-data-file-name-options.md)|  
|En la página **Iniciar**, elija la aplicación que se debe iniciar si existen varios proyectos .exe en la solución de código.|-   [Recopilar datos de interacción de capas](../profiling/collecting-tier-interaction-data.md)|  
|En la página **Interacciones de capas**, agregue los datos de llamada de ADO.NET a la ejecución de generación de perfiles.|-   [Recopilar datos de interacción de capas](../profiling/collecting-tier-interaction-data.md)|  
|En la página **Eventos de Windows**, especifique uno o más eventos ETW \(Seguimiento de eventos para Windows\) que se recopilarán con los datos de muestreo.|-   [Cómo: Recopilar datos de Seguimiento de eventos para Windows \(ETW\)](../Topic/How%20to:%20Collect%20Event%20Tracing%20for%20Windows%20\(ETW\)%20Data.md)|  
|En la página **Contadores de Windows**, especifique uno o más contadores de rendimiento del sistema operativo que se deben agregar como marcas a los datos de generación de perfiles.|-   [Cómo: Recopilar datos de contadores de Windows](../profiling/how-to-collect-windows-counter-data.md)|  
|En la página **Avanzadas**, especifique la versión del runtime de .NET Framework que se usará en la generación de perfiles si los módulos de aplicación usan varias versiones.  De forma predeterminada, se generan los perfiles de la primera versión cargada.|-   [Cómo: Especificar el runtime de .NET Framework para la generación de perfiles en escenarios en paralelo](../Topic/How%20to:%20Specify%20the%20.NET%20Framework%20Runtime.md)|  
  
## Tareas de instrumentación  
 Las tareas de la tabla siguiente son opciones del cuadro de diálogo **Páginas de propiedades** específicas de la generación de perfiles con el método de instrumentación.  
  
|Tarea|Contenido relacionado|  
|-----------|---------------------------|  
|En la página **Archivos binarios**, especifique una ubicación para las copias instrumentadas de los módulos.  De forma predeterminada, los archivos binarios originales se mueven a una carpeta de copia de seguridad.|-   [Cómo: Cambiar la ubicación de binarios instrumentados](../profiling/how-to-relocate-instrumented-binaries.md)|  
|En la página **Instrumentación**, excluya las funciones pequeñas de la generación de perfiles para reducir la sobrecarga de este proceso, genere los perfiles del código JavaScript en ASP.NET Web Pages y especifique comandos para ejecutarse en un símbolo del sistema antes y después del proceso de instrumentación.|-   [Cómo: Excluir o incluir funciones cortas en la instrumentación](../Topic/How%20to:%20Exclude%20or%20Include%20Short%20Functions%20from%20Instrumentation.md)<br />-   [Cómo: Generar perfiles de código de JavaScript \(ECMA\) en páginas web](../Topic/How%20to:%20Profile%20JavaScript%20Code%20in%20Web%20Pages.md)<br />-   [Cómo: Especificar comandos anteriores y posteriores a la instrumentación](../Topic/How%20to:%20Specify%20Pre-%20and%20Post-Instrument%20Commands.md)|  
|En la página **Contadores de CPU**, especifique uno o más contadores de rendimiento del procesador para agregarlos a los datos de generación de perfiles.|-   [Cómo: Recopilar datos de contadores de CPU](../profiling/how-to-collect-cpu-counter-data.md)|  
|En la página **Avanzadas**, especifique cualquier opción de VSInstr.exe adicional que desee, como las opciones para incluir o excluir funciones concretas.  Para obtener más información acerca de las opciones de VSInstr, vea [VSInstr](../profiling/vsinstr.md).|-   [Cómo: Especificar opciones de instrumentación adicional](../Topic/How%20to:%20Specify%20Additional%20Instrumentation%20Options.md)<br />-   [Cómo: Limitar la instrumentación a funciones específicas](../profiling/how-to-limit-instrumentation-to-specific-functions.md)|  
  
## Vea también  
 [Configurar sesiones de rendimiento](../profiling/configuring-performance-sessions.md)   
 [Cómo: Elegir métodos de recolección](../profiling/how-to-choose-collection-methods.md)   
 [Propiedades de las sesiones de rendimiento](../profiling/performance-session-properties.md)