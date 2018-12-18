---
title: Propiedades de las sesiones de rendimiento | Microsoft Docs
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
- Profiling Tools,properties
- property pages,Profiling Tools
- performance tools, performance session properties
ms.assetid: c3a86913-172b-488f-a31a-cea01a71b2ea
caps.latest.revision: 21
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ed020d09bc3c7b85a395625f410f0062bf4bfac9
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/16/2018
ms.locfileid: "51739285"
---
# <a name="performance-session-properties"></a>Propiedades de las sesiones de rendimiento
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Una **Sesión de rendimiento** le permite configurar opciones que determinan cómo se perfila la aplicación. También almacena informes que se generan para la sesión de generación de perfiles.  
  
 **Requisitos**  
  
- [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)], [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)], [!INCLUDE[vsPro](../includes/vspro-md.md)]  
  
  Cree una **Sesión de rendimiento** ejecutando el **Asistente de rendimiento** o creando manualmente una sesión. La **Sesión de rendimiento** se muestra en el **Explorador de rendimiento** después de la **Sesión de rendimiento** se haya creado.  
  
  Para ver las propiedades de la **Sesión de rendimiento**, seleccione el nombre de la sesión en **Explorador de rendimiento**, haga clic con el botón derecho en ella y después seleccione **Propiedades**.  
  
  La sesión de rendimiento tiene las siguientes páginas de propiedades:  
  
## <a name="general"></a>General  
 Estas opciones le permiten seleccionar el método de generación de perfiles, agregar la colección de objetos .NET y datos de duración, y especificar la ubicación predeterminada del informe y las convenciones de nomenclatura.  
  
 Para obtener más información, consulte:  
  
 [Cómo: Elegir métodos de recopilación](../profiling/how-to-choose-collection-methods.md)  
  
 [Recopilar datos referentes a la asignación y duración de memoria de .NET](../profiling/collecting-dotnet-memory-allocation-and-lifetime-data.md)  
  
 [Cómo: Establecer opciones de nombre de archivo de datos de rendimiento](../profiling/how-to-set-performance-data-file-name-options.md)  
  
## <a name="launch"></a>Launch  
 Esta configuración le permite seleccionar de una lista de binarios y especificar el orden de inicio de los binarios.  
  
 Para obtener más información, consulte [Cómo: Especificar el binario para empezar](../profiling/how-to-specify-the-binary-to-start.md)  
  
## <a name="sampling"></a>Muestreo  
 Estos valores le permiten seleccionar el intervalo de muestreo y de eventos de muestra cuando se utiliza el muestreo como método de generación de perfiles. Un evento de muestra se utiliza para recopilar datos de generación de perfiles en el intervalo especificado. Por ejemplo, si el evento de muestra es de ciclos de reloj y el intervalo de muestreo está establecido en 10.000.000, los datos de generación de perfiles se recopilan una vez cada 10 millones de ciclos de reloj. Los siguientes cuatro tipos de eventos de muestra están disponibles:  
  
- Ciclos de reloj: para problemas relacionados con la CPU  
  
- Errores de página: para problemas relacionados con la memoria  
  
- Llamadas del sistema: para problemas relacionados con E/S  
  
- Contadores de rendimiento: para problemas de rendimiento de bajo nivel  
  
- Se pueden especificar eventos de muestra adicionales en función de los contadores de rendimiento disponibles  
  
  Para obtener más información, consulte [Cómo: Elegir eventos de muestra](../profiling/how-to-choose-sampling-events.md)  
  
## <a name="binary"></a>Binary  
 Esta configuración le permite especificar si desea reubicar el binario instrumentado. Por ejemplo, si genera perfiles de My.DLL y decide no reubicar el binario instrumentado, se crea una copia de seguridad de My.DLL denominada My.Orig.DLL. Posteriormente, se modifica My.DLL insertando sondeos para recopilar datos. Si decide reubicar el binario instrumentado, no se cambia el nombre del binario original y el binario instrumentado se copia en la ubicación especificada para su uso durante la instrumentación.  
  
 Para obtener más información, consulte [Cómo: Especificar el binario para empezar](../profiling/how-to-specify-the-binary-to-start.md)  
  
## <a name="tier-interactions"></a>Interacciones de capas  
 Para obtener más información, consulte [Recopilar datos de interacción de capas](../profiling/collecting-tier-interaction-data.md)  
  
## <a name="instrumentation"></a>Instrumentación  
 Esta configuración permite recopilar datos de rendimiento de código JScript en páginas web de [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] y especificar cualquier evento **anterior a la instrumentación** y **posterior a la instrumentación** que desee que se produzcan.  
  
 Para obtener más información, consulte:  
  
 [Cómo: Generar perfiles de código de JavaScript en páginas web](../profiling/how-to-profile-javascript-code-in-web-pages.md)  
  
 [Cómo: Especificar comandos anteriores y posteriores a la instrumentación](../profiling/how-to-specify-pre-and-post-instrument-commands.md)  
  
## <a name="cpu-counters"></a>Contadores de CPU  
 Esta configuración permite recopilar datos sobre los contadores de rendimiento de CPU cuando se utiliza el método de generación de perfiles de instrumentación. Los contadores de rendimiento móviles están disponibles independientemente del fabricante o del diseño de la CPU. Los eventos de la plataforma son específicos para el diseño y fabricante de la CPU. Para obtener más información acerca de los contadores de rendimiento del procesador, consulte la documentación del procesador específica.  
  
 Para obtener más información, consulte [Cómo: Recopilar datos de contadores de CPU](../profiling/how-to-collect-cpu-counter-data.md)  
  
## <a name="windows-events"></a>Eventos de Windows  
 Durante la generación de perfiles, puede recopilar datos de proveedores de seguimiento de eventos. Puede ver los datos mediante la opción `/calltrace` de la herramienta de línea de comandos VSPerfReport.exe. Para obtener más información acerca de Seguimiento de eventos para Windows (ETW), consulte [Sobre el seguimiento de eventos](http://go.microsoft.com/fwlink/?linkid=90752).  
  
 Para obtener más información, consulte:  
  
 [Cómo: Recopilar datos de Seguimiento de eventos para Windows (ETW)](../profiling/how-to-collect-event-tracing-for-windows-etw-data.md)  
  
 [VSPerfReport](../profiling/vsperfreport.md).  
  
## <a name="windows-counters"></a>Contadores de Windows  
 Esta opción le permite recopilar datos de contadores del Monitor de rendimiento de Windows. Para recopilar estos datos, active la casilla **Recopilar contadores de rendimiento de Windows**. Se puede establecer el intervalo de recopilación en el cuadro **Intervalo de recopilación**. **Categoría de contador** e **Instancia** también pueden estar disponibles. Algunos contadores predeterminados del Monitor de rendimiento de Windows están disponibles.  
  
 Para obtener más información, consulte [Cómo: Recopilar datos de contadores de Windows](../profiling/how-to-collect-windows-counter-data.md).  
  
## <a name="advanced"></a>Avanzadas  
 Esta configuración permite agregar opciones al proceso de instrumentación mediante la especificación de una o más opciones de la herramienta de generación de perfiles de línea de comandos [VSInstr](../profiling/vsinstr.md). También puede especificar la versión de Common Runtime de la que quiere generar perfiles cuando utiliza más de una versión de la aplicación.  
  
 Para obtener más información, consulte:  
  
 [Cómo: Especificar el tiempo de ejecución de .NET Framework](../profiling/how-to-specify-the-dotnet-framework-runtime.md)  
  
 [Cómo: Especificar opciones de instrumentación adicional](../profiling/how-to-specify-additional-instrumentation-options.md)  
  
## <a name="see-also"></a>Vea también  
 [Temas de introducción](../profiling/overviews-performance-tools.md)   
 [Configurar sesiones de rendimiento](../profiling/configuring-performance-sessions.md)   
 [Controlar la recopilación de datos](../profiling/controlling-data-collection.md)



