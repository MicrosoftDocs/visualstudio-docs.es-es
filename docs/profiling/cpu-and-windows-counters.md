---
title: Contadores de Windows y de CPU | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.performance.property.counters
helpviewer_keywords:
- Windows counters in Profiling Tools
- CPU counters in Profiling Tools
ms.assetid: d2c45c6a-f975-45ab-b8a5-4768ddd518fb
caps.latest.revision: "28"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: d22300bc675de5074497589af53b304b9a1caa4d
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="cpu-and-windows-counters"></a>Contadores de Windows y de CPU
El generador de perfiles de Visual Studio le permite recopilar datos de rendimiento generados por el sistema operativo (contadores de Windows) y datos de rendimiento generados por la unidad de procesador (contadores de CPU).  
  
 **Requisitos**  
  
-   [!INCLUDE[vsUltLong](../code-quality/includes/vsultlong_md.md)], [!INCLUDE[vsPreLong](../code-quality/includes/vsprelong_md.md)], [!INCLUDE[vsPro](../code-quality/includes/vspro_md.md)]  
  
> [!NOTE]
>  Las características de seguridad mejoradas en Windows 8 y Windows Server 2012 requirieron cambios significativos en la forma en que el generador de perfiles de Visual Studio recopila datos en estas plataformas. Las aplicaciones para UWP también requieren nuevas técnicas de recopilación. Consulte [Herramientas de rendimiento en aplicaciones de Windows 8 y Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).  
  
## <a name="windows-counters"></a>Contadores de Windows  
 Los contadores de Windows forman parte de la infraestructura de diagnóstico de Windows que proporciona información sobre el rendimiento del sistema operativo o de una aplicación, un servicio o un controlador. Los contadores de Windows dependen de la configuración del equipo actual y podrían no estar disponibles en otros equipos. Los contadores de rendimiento de Windows se recopilan en archivos de datos de generación de perfiles como marcas de generación de perfiles, que pueden utilizarse para filtrar vistas e informes.  
  
## <a name="cpu-counters"></a>Contadores de CPU  
 Los contadores de CPU son una característica de la CPU del equipo que almacena el recuento de eventos relacionados con el hardware.  Al recopilar datos de contadores de CPU mediante el método de generación de perfiles de instrumentación, los datos se anexan a los datos para los módulos y las funciones. Puede recopilar varios contadores de CPU mediante el método de instrumentación. Cuando utiliza el método de muestreo, selecciona un contador para usarlo como el evento que se va a muestrear.  
  
 Los contadores de rendimiento son específicos de la CPU. Los distintos modelos y versiones de una CPU pueden tener valores de configuración significativamente diferentes para habilitar el mismo contador de rendimiento. Los eventos portátiles del generador de perfiles de [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)] desacoplan algunos contadores de rendimiento comunes de procesadores específicos y le permiten recopilar o muestrear eventos de rendimiento genéricos.  
  
 Si quiere contar un evento determinado cuando utilice el generador de perfiles, por ejemplo, líneas no ejecutadas de caché L2, puede crear una sesión de rendimiento con el remitente de ese evento. Puede hacerlo en cualquier CPU con una caché L2. La sesión de rendimiento se puede mover de una plataforma a otra sin modificación.  
  
 El generador de perfiles de Visual Studio sigue admitiendo eventos concretos para una plataforma específica. Por ejemplo, puede ser que un desarrollador en una plataforma Pentium 4 quiera contar los eventos que son específicos de la arquitectura NetBurst. Este evento no es portátil, pero seguirá disponible para el desarrollador en una sesión de rendimiento específica en una plataforma determinada.  
  
## <a name="portable-and-platform-events"></a>Eventos portátiles y de plataforma  
 Los eventos portátiles son un grupo de contadores de CPU que no son específicos de un procesador determinado. Todos los demás contadores de CPU se denominan eventos de plataforma y podrían no admitirse en diversas plataformas.  
  
 Los contadores para eventos portátiles y de plataforma se definen en archivos .XML, en que se proporcionan valores específicos relacionados con los contadores. Existen varios archivos para diferentes CPU, porque los datos de las CPU de Intel y AMD, por ejemplo, son diferentes. El generador de perfiles [!INCLUDE[vs_orcas_long](../debugger/includes/vs_orcas_long_md.md)] utiliza esta información para mostrarle al usuario contadores adecuados, tanto portátiles como de la plataforma, para medir el rendimiento.  
  
### <a name="portable-events"></a>Eventos portátiles  
 Los eventos portátiles incluyen los siguientes eventos:  
  
 **Eventos generales**  
  
|Nombre de evento|Descripción del evento|  
|----------------|-----------------------|  
|Instrucciones retiradas|Indica el número de instrucciones que se ejecutan hasta que se complete el evento.|  
|Ciclos no detenidos|Indica solo los ciclos en que el procesador no se detiene, por ejemplo, a la espera de E/S.|  
  
 **Eventos de front-end**  
  
|Nombre de evento|Descripción del evento|  
|----------------|-----------------------|  
|Líneas no ejecutadas en ITLB|Indica el número de consultas del búfer de búsqueda de traducción de la instrucción que produjeron una línea no ejecutada.|  
  
 **Eventos de bifurcaciones**  
  
|Nombre de evento|Descripción del evento|  
|----------------|-----------------------|  
|Bifurcaciones retiradas|Indica el número de instrucciones de bifurcación que se ejecutan hasta que se complete el evento.|  
|Bifurcaciones mal previstas|Indica las bifurcaciones mal previstas que se producen porque el procesador predijo una ruta de acceso incorrecta. Las bifurcaciones mal previstas afectan al rendimiento porque el procesador debe descartar todo el trabajo realizado y comenzar de nuevo en una ruta de acceso correcta.|  
  
 **Eventos de memoria:**  
  
|Nombre de evento|Descripción del evento|  
|----------------|-----------------------|  
|Líneas no ejecutadas en la lectura de caché en L2|Indica el número de líneas no ejecutadas en la lectura de caché de segundo nivel.|  
|Referencias de lectura de caché en L2|Indica el número de referencias en la lectura de caché de segundo nivel. Incluye líneas no ejecutadas de carga, así como líneas no ejecutadas y aciertos en la lectura de propiedad (RFO).|  
  
## <a name="viewing-available-counters"></a>Ver los contadores disponibles  
 Los contadores de CPU disponibles en el IDE de Visual Studio se pueden enumerar en una ventana del símbolo del sistema.  
  
### <a name="visual-studio-ui"></a>Interfaz de usuario de Visual Studio  
 Para enumerar los contadores disponibles en un equipo en el IDE de Visual Studio, debe tener abierta una sesión de rendimiento del generador de perfiles en el Explorador de rendimiento.  
  
##### <a name="to-view-a-list-of-a-list-of-all-cpu-counters-that-are-supported-on-the-current-platform"></a>Para ver una lista de todos los contadores de CPU que se admiten en la plataforma actual  
  
1.  En el Explorador de rendimiento, haga clic con el botón derecho en la sesión de rendimiento y, después, haga clic en **Propiedades**.  
  
2.  Realice una de las siguientes acciones:  
  
    -   Haga clic en **Muestreo** y, a continuación, seleccione **Contador de rendimiento** en la lista de eventos **Ejemplo**. Los contadores de CPU se enumeran en **Contadores de rendimiento disponibles**.  
  
         **Nota** Haga clic en **Cancelar** para volver a la configuración de muestreo anterior.  
  
     O bien  
  
    -   Seleccione **Contadores de CPU** y, a continuación, seleccione **Recopilar contadores de CPU**. Los contadores de CPU se enumeran en **Contadores disponibles**.  
  
         **Nota** Haga clic en **Cancelar** para volver a la configuración de colección de contadores anterior.  
  
##### <a name="to-view-a-list-of-a-list-of-window-counters-that-are-supported-on-the-current-platform"></a>Para ver una lista de los contadores de Windows que se admiten en la plataforma actual  
  
1.  En el Explorador de rendimiento, haga clic con el botón derecho en la sesión de rendimiento y, después, haga clic en **Propiedades**.  
  
2.  Haga clic en **Contadores de Windows**.  
  
3.  Seleccione **Recopilar contadores de Windows**.  
  
4.  En la lista **Categoría de contador**, seleccione un grupo de contadores. El contador de Windows para el grupo se muestra en el cuadro de lista.  
  
     **Nota:** Haga clic en **Cancelar** para volver a la configuración de colección de contadores anterior.  
  
### <a name="command-line"></a>Línea de comandos  
 Mediante la herramienta de línea de comandos [VSPerfCmd](../profiling/vsperfcmd.md), puede enumerar los contadores de CPU que están disponibles en un equipo desde la línea de comandos.  
  
##### <a name="to-list-of-cpu-counters-that-are-supported-on-the-current-platform"></a>Para enumerar los contadores de CPU que se admiten en la plataforma actual  
  
1.  Abra una ventana de símbolo del sistema.  
  
2.  Tipo  
  
     **\<Visual Studio Performance Tools Directory>\VSPerfCmd /querycounters**  
  
     donde **\<Visual Studio Performance Tools Directory>** es la ruta de acceso al directorio de herramientas de rendimiento de la instalación de Visual Studio, normalmente  
  
     C:\Archivos de programa\Microsoft Visual Studio 10.0\Team Tools\Performance Tools  
  
## <a name="see-also"></a>Vea también  
 [Temas de introducción](../profiling/overviews-performance-tools.md)   
 [Cómo: Elegir eventos de muestreo](../profiling/how-to-choose-sampling-events.md)   
 [Cómo: Recopilar datos de contadores de CPU](../profiling/how-to-collect-cpu-counter-data.md)   
 [Cómo: Recopilar datos de contadores de Windows](../profiling/how-to-collect-windows-counter-data.md)