---
title: "C&#243;mo: Elegir m&#233;todos de recolecci&#243;n | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "herramientas de rendimiento, elección del método de colección"
  - "herramientas de generación de perfiles, elección del método de colección"
  - "métodos de colección de rendimiento"
ms.assetid: c87cfd3a-0fc7-49ae-9c05-d8480891cc63
caps.latest.revision: 34
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 34
---
# C&#243;mo: Elegir m&#233;todos de recolecci&#243;n
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Las Herramientas de generación de perfiles de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] admiten tres métodos de recolección de datos de rendimiento: muestreo, instrumentación y simultaneidad.  También puede usar los métodos de muestreo o instrumentación para recopilar datos de duración y de asignación de memoria de .NET.  
  
 **Requisitos**  
  
-   [!INCLUDE[vsUltLong](../code-quality/includes/vsultlong_md.md)], [!INCLUDE[vsPreLong](../code-quality/includes/vsprelong_md.md)], [!INCLUDE[vsPro](../code-quality/includes/vspro_md.md)]  
  
 Puede utilizar la propiedad **Method** de la sesión de rendimiento para especificar el método de recolección más adecuado para su aplicación.  Puede establecer el método de recolección en el Asistente de rendimiento, en el Explorador de rendimiento o en las páginas de propiedades de una sesión de rendimiento.  Si utiliza las herramientas de la línea de comandos, vea [Generación de perfiles desde la línea de comandos](../profiling/using-the-profiling-tools-from-the-command-line.md) para obtener más información.  
  
## Asistente para rendimiento  
  
#### Para seleccionar un método de recolección mediante el Asistente de rendimiento  
  
-   En la primera página del asistente, seleccione una de las siguientes opciones:  
  
|Opción|Descripción|  
|------------|-----------------|  
|**Muestreo de la CPU**|Recoge estadísticas de la aplicación que son útiles para el análisis inicial y para el análisis de problemas de utilización de la CPU.|  
|**Instrumentación**|Recoge datos detallados de control de tiempo útiles para un análisis enfocado y para analizar los problemas de rendimiento de entrada\/salida.|  
|**Asignación de memoria .NET**|Recoge los datos de asignación de memoria de [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] con el método de generación de perfiles mediante muestreo.|  
|**Simultaneidad**|Obtiene datos de contención de recursos numéricos.|  
  
## Explorador de rendimiento  
  
#### Para seleccionar un método de recolección mediante el Explorador de rendimiento  
  
1.  En la barra de herramientas **Explorador de rendimiento**, haga clic en la flecha situada junto a la lista desplegable **Método**.  
  
2.  Haga clic en el método de recolección que prefiera.  
  
## Páginas de propiedades de las sesiones de rendimiento  
  
#### Para seleccionar método de muestreo o de instrumentación con las propiedades de la sesión de rendimiento  
  
1.  En el **Explorador de rendimiento**, seleccione la sesión de rendimiento.  
  
     El nombre de archivo de la sesión de rendimiento tiene la extensión .psess.  
  
2.  Haga clic con el botón secundario del mouse en la sesión de rendimiento y, a continuación, haga clic en **Propiedades**.  
  
3.  En las **Páginas de propiedades**, haga clic en **General**.  
  
4.  Haga clic en el método de recolección que prefiera.  
  
    -   Para obtener información sobre las demás opciones que están disponibles cuando se recogen datos de muestreo, vea [Recopilar estadísticas de rendimiento mediante el muestreo](../profiling/collecting-performance-statistics-by-using-sampling.md).  
  
    -   Para obtener información sobre las demás opciones que están disponibles cuando se recogen datos de muestreo, vea [Recolección de datos de control de tiempo detallados utilizando instrumentación](../profiling/collecting-detailed-timing-data-by-using-instrumentation.md).  
  
#### Para seleccionar la recolección de datos de memoria .NET mediante las propiedades de la sesión de rendimiento  
  
1.  En el **Explorador de rendimiento**, seleccione la sesión de rendimiento.  
  
     El nombre de archivo de la sesión de rendimiento tiene la extensión .psess.  
  
2.  Haga clic con el botón secundario del mouse en la sesión de rendimiento y, a continuación, haga clic en **Propiedades**.  
  
3.  En las **Páginas de propiedades**, haga clic en **General**.  
  
4.  Haga clic en **Muestreo** o en **Instrumentación**.  
  
5.  Haga clic en **Recopilar información de asignación de objetos .NET** para recoger el tamaño y número de asignaciones de objeto [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)].  
  
6.  \(Opcional\) Haga clic en **Recopilar también la información de duración de los objetos .NET** para recoger datos sobre las generaciones de la recolección de elementos no utilizados en las que se reclamó la memoria de objeto.  
  
     Para obtener información sobre las demás opciones que están disponibles cuando se recogen datos de memoria .NET, vea [Recopilar datos referentes a la asignación y duración de memoria de .NET](../profiling/collecting-dotnet-memory-allocation-and-lifetime-data.md).  
  
#### Para seleccionar la recolección de datos de simultaneidad mediante las propiedades de la sesión de rendimiento  
  
1.  En el **Explorador de rendimiento**, haga clic con el botón secundario del mouse en la sesión de rendimiento y, a continuación, haga clic en **Propiedades**.  
  
2.  En las **Páginas de propiedades**, haga clic en **General**.  
  
3.  Haga clic en **Simultaneidad**.  
  
## Vea también  
 [Configurar sesiones de rendimiento](../profiling/configuring-performance-sessions.md)   
 [Introducción a los valores de datos de muestreo](../profiling/understanding-sampling-data-values.md)   
 [Propiedades de las sesiones de rendimiento](../profiling/performance-session-properties.md)