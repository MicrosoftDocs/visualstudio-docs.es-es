---
title: "Recopilar estad&#237;sticas de rendimiento mediante el muestreo | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Herramientas de generación de perfiles, muestreo"
  - "método de generación de perfiles mediante muestreo"
ms.assetid: 8e36361b-bb3d-40c6-b286-0e68c0ecb915
caps.latest.revision: 21
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 21
---
# Recopilar estad&#237;sticas de rendimiento mediante el muestreo
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

De forma predeterminada, el método de muestreo de las herramientas de generación de perfiles de [!INCLUDE[vsPreShort](../code-quality/includes/vspreshort_md.md)] recopila información de generación de perfiles cada 10.000.000 ciclos de procesador \(aproximadamente cada centésima de segundo en un equipo de 1 GHz\).  Este método es útil para buscar problemas de utilización del procesador y es el método sugerido para iniciar la mayoría de las investigaciones de rendimiento.  
  
 **Requisitos**  
  
-   [!INCLUDE[vsUltLong](../code-quality/includes/vsultlong_md.md)], [!INCLUDE[vsPreLong](../code-quality/includes/vsprelong_md.md)], [!INCLUDE[vsPro](../code-quality/includes/vspro_md.md)]  
  
> [!NOTE]
>  Las características de seguridad mejoradas en Windows 8 y Windows Server 2012 requirieron cambios significativos en la forma en que el generador de perfiles de Visual Studio recopila datos en estas plataformas.  Las aplicaciones de la Tienda Windows también requieren nuevas técnicas de recolección.  Vea [Generar perfiles de aplicaciones de Windows 8 y Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).  
  
 Puede especificar el método de muestreo utilizando uno de los procedimientos siguientes:  
  
-   En la primera página del Asistente para generación de perfiles, haga clic en **Muestreo de la CPU \(recomendado\)**.  
  
-   En la barra de herramientas del **Explorador de rendimiento**, en la lista **Método**, haga clic en **Muestreo**.  
  
-   En la página **general** del cuadro de diálogo de propiedades de la sesión de rendimiento, haga clic en **Muestreo**.  
  
## Tareas comunes  
 Puede especificar opciones adicionales en el cuadro de diálogo de *Performance Session***Páginas de propiedades** de la sesión de rendimiento.  Para abrir este cuadro de diálogo:  
  
-   En el **Explorador de rendimiento**, haga clic con el botón secundario en el nombre de la sesión de rendimiento y, a continuación, haga clic en **Propiedades**.  
  
 Las tareas de la tabla siguiente describen opciones que puede especificar en el cuadro de diálogo de *Performance Session***Páginas de propiedades** cuando genere perfiles utilizando el método de muestreo.  
  
|Tarea|Contenido relacionado|  
|-----------|---------------------------|  
|En la página **General**, agregue colecciones de datos de asignación de memoria y de duración de .NET Framework y especifique los detalles de nomenclatura para el archivo de datos de generación de perfiles que se crea \(.vsp\).|-   [Recopilar datos referentes a la asignación y duración de memoria de .NET](../profiling/collecting-dotnet-memory-allocation-and-lifetime-data.md)<br />-   [Cómo: Establecer opciones de nombre de archivo de datos de generación de perfiles](../profiling/how-to-set-performance-data-file-name-options.md)|  
|En la página **Muestreo**, cambie la velocidad de muestreo, cambie el evento de muestreo de los ciclos de reloj de procesador a otro contador de rendimiento de procesador, o cambie ambos valores.|-   [Cómo: Elegir eventos de muestreo](../Topic/How%20to:%20Choose%20Sampling%20Events.md)|  
|En la página **Inicio**, si tiene varios proyectos .exe en la solución de código, especifique la aplicación que se debe iniciar y el orden de inicio.|-   [Recopilar datos de interacción de capas](../profiling/collecting-tier-interaction-data.md)|  
|En la página **Interacciones de capas**, agregue información de llamada de ADO.NET a los datos recopilados en la ejecución de generación de perfiles.|-   [Recopilar datos de interacción de capas](../profiling/collecting-tier-interaction-data.md)|  
|En la página **Eventos de Windows**, especifique uno o más eventos ETW \(Seguimiento de eventos para Windows\) que se recopilarán con los datos de muestreo.|-   [Cómo: Recopilar datos de Seguimiento de eventos para Windows \(ETW\)](../Topic/How%20to:%20Collect%20Event%20Tracing%20for%20Windows%20\(ETW\)%20Data.md)|  
|En la página **Contadores de Windows**, especifique uno o más contadores de rendimiento del sistema operativo que se deben agregar como marcas a los datos de generación de perfiles.|-   [Cómo: Recopilar datos de contadores de Windows](../profiling/how-to-collect-windows-counter-data.md)|  
|En la página **Avanzadas**, especifique la versión del runtime de .NET Framework que se usará en la generación de perfiles si los módulos de aplicación usan varias versiones.  De forma predeterminada, se generan los perfiles de la primera versión cargada.|-   [Cómo: Especificar el runtime de .NET Framework para la generación de perfiles en escenarios en paralelo](../Topic/How%20to:%20Specify%20the%20.NET%20Framework%20Runtime.md)|