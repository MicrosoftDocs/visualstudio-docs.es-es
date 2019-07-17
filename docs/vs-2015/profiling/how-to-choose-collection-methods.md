---
title: Procedimiento Elegir métodos de recopilación | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- performance tools, choosing collection method
- profiling tools, choosing collection method
- performance collection methods
ms.assetid: c87cfd3a-0fc7-49ae-9c05-d8480891cc63
caps.latest.revision: 39
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 33ff14ce88f2032b998214ed11310a15550321dc
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "68199805"
---
# <a name="how-to-choose-collection-methods"></a>Procedimiento Elección de métodos de recopilación
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Las herramientas de generación de perfiles [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] admiten tres métodos de recopilación de datos de rendimiento: muestreo, instrumentación y simultaneidad. También puede utilizar el método de muestreo o de instrumentación para recopilar datos de duración y de asignación de memoria de .NET.  
  
 **Requisitos**  
  
- [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)], [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)], [!INCLUDE[vsPro](../includes/vspro-md.md)]  
  
  Puede utilizar propiedad de la sesión de rendimiento **Método** para especificar el método de recolección más adecuado para su aplicación. Puede establecer el método de colección en el Asistente de rendimiento, el Explorador de rendimiento o las páginas de propiedades de una sesión de rendimiento. Si utiliza las herramientas de línea de comandos, consulte [Generación de perfiles desde la línea de comandos](../profiling/using-the-profiling-tools-from-the-command-line.md) para obtener más información.  
  
## <a name="performance-wizard"></a>Asistente para rendimiento  
  
#### <a name="to-select-a-collection-method-using-the-performance-wizard"></a>Para seleccionar un método de colección mediante el Asistente de rendimiento  
  
- En la primera página del asistente, seleccione una de las siguientes opciones:  
  
|Opción|DESCRIPCIÓN|  
|------------|-----------------|  
|**Muestreo de la CPU**|Recopila estadísticas de la aplicación que son útiles para el análisis inicial y para analizar problemas de utilización de CPU.|  
|**Instrumentación**|Recopila datos de control de tiempo detallados que son útiles para un análisis enfocado y para analizar problemas de rendimiento de entrada/salida.|  
|**Asignación de memoria de .NET**|Recopila datos de asignación de memoria de [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] mediante el método de generación de perfiles de muestreo.|  
|**Simultaneidad**|Recopila datos de contención de recursos numéricos.|  
  
## <a name="performance-explorer"></a>Explorador de rendimiento  
  
#### <a name="to-select-a-collection-method-using-performance-explorer"></a>Para seleccionar un método de colección mediante el Explorador de rendimiento  
  
1. En la barra de herramientas **Explorador de rendimiento**, haga clic en la flecha situada junto a la lista desplegable **Método**.  
  
2. Haga clic en el método de recolección que prefiera.  
  
## <a name="performance-session-property-pages"></a>Páginas de propiedades de la sesión de rendimiento  
  
#### <a name="to-select-the-sampling-or-instrumentation-method-using-performance-session-properties"></a>Para seleccionar el método de muestreo o instrumentación mediante las propiedades de la sesión de rendimiento  
  
1. En **Explorador de rendimiento**, seleccione la sesión de rendimiento.  
  
     Un nombre de archivo de la sesión de rendimiento tiene la extensión .psess.  
  
2. Haga clic con el botón derecho en la sesión de rendimiento y, después, haga clic en **Propiedades**.  
  
3. En las **Páginas de propiedades**, haga clic en **General**.  
  
4. Haga clic en el método de recolección que prefiera.  
  
    - Para obtener información sobre las demás opciones que están disponibles al recopilar datos de muestreo, consulte [Recopilar estadísticas de rendimiento mediante el uso de muestreo](../profiling/collecting-performance-statistics-by-using-sampling.md)  
  
    - Para obtener información sobre las demás opciones que están disponibles al recopilar datos de muestreo, consulte [Recopilar datos de control de tiempo detallados mediante la instrumentación](../profiling/collecting-detailed-timing-data-by-using-instrumentation.md).  
  
#### <a name="to-select-net-memory-data-collection-by-using-performance-session-properties"></a>Para seleccionar la recopilación de datos de memoria de .NET mediante las propiedades de la sesión de rendimiento  
  
1. En **Explorador de rendimiento**, seleccione la sesión de rendimiento.  
  
     Un nombre de archivo de la sesión de rendimiento tiene la extensión .psess.  
  
2. Haga clic con el botón derecho en la sesión de rendimiento y, después, haga clic en **Propiedades**.  
  
3. En las **Páginas de propiedades**, haga clic en **General**.  
  
4. Haga clic en **Muestreo** o **Instrumentación**.  
  
5. Haga clic en **Recopilar información de asignación de objetos .NET** para recopilar el tamaño y el número de asignaciones de objetos [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)].  
  
6. Haga clic en **Recopilar también la información de duración de los objetos .NET** para recopilar datos sobre las generaciones de recolección de elementos no utilizados en que se reclama la memoria del objeto (opcional).  
  
     Para obtener información sobre las demás opciones que están disponibles al recopilar datos de memoria de .NET, consulte [Recopilar datos de duración y asignación de memoria de .NET](../profiling/collecting-dotnet-memory-allocation-and-lifetime-data.md).  
  
#### <a name="to-select-concurrency-data-collection-by-using-performance-session-properties"></a>Para seleccionar la recopilación de datos de simultaneidad mediante las propiedades de la sesión de rendimiento  
  
1. En el **Explorador de rendimiento**, haga clic con el botón derecho del mouse en la sesión de rendimiento y, después, haga clic en **Propiedades**.  
  
2. En las **Páginas de propiedades**, haga clic en **General**.  
  
3. Haga clic en **Simultaneidad**.  
  
## <a name="see-also"></a>Vea también  
 [Configurar sesiones de rendimiento](../profiling/configuring-performance-sessions.md)   
 [Introducción a los valores de datos de muestreo](../profiling/understanding-sampling-data-values.md)   
 [Propiedades de la sesión de rendimiento](../profiling/performance-session-properties.md)
