---
title: "Vista de resumen: datos de muestreo del generador de perfiles | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "método de generación de perfiles mediante muestreo, vista Resumen"
  - "Vista Resumen"
ms.assetid: 79056873-2985-40be-9112-cdbc26a65156
caps.latest.revision: 13
caps.handback.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Vista de resumen: datos de muestreo del generador de perfiles
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

La vista Resumen muestra información sobre las funciones con mayor incidencia en el rendimiento de una ejecución de generación de perfiles.  Para obtener más información, incluida una descripción de las listas de Vínculos de notificaciones y de Informes, vea [Vista Resumen](../profiling/summary-view.md).  
  
> [!NOTE]
>  Las características de seguridad mejoradas en Windows 8 y Windows Server 2012 requirieron cambios significativos en la forma en que el generador de perfiles de Visual Studio recopila datos en estas plataformas.  Las aplicaciones de la Tienda Windows también requieren nuevas técnicas de recolección.  Vea [Generar perfiles de aplicaciones de Windows 8 y Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).  
  
## Gráfico de escala de tiempo  
 El gráfico de escala de tiempo de la vista de resumen muestra el porcentaje de utilización del procesador \(CPU\) por parte de la aplicación perfilada durante el tiempo en que se produjo la generación de perfiles.  Puede usar el gráfico de escala de tiempo para filtrar la vista en función de un intervalo de tiempo seleccionado.  Para obtener más información, vea [Cómo: Filtrar vistas de informe desde la escala de tiempo de resumen](../Topic/How%20to:%20Filter%20Report%20Views%20from%20the%20Summary%20Timeline.md).  
  
## Ruta de acceso activa  
 La **Ruta de acceso activa** muestra la ruta de acceso de ejecución en la que se recopilaron la mayoría de las muestras.  Puede hacer clic en una función para mostrar la vista Detalles de la función correspondiente.  Para mostrar otras vistas de la función, haga clic con el botón secundario del mouse en la función y, a continuación, haga clic en una vista de la lista.  
  
 La **Ruta de acceso activa** incluye los datos siguientes para cada función:  
  
|Columna|Descripción|  
|-------------|-----------------|  
|**Name**|Nombre de la función.|  
|**Porcentaje de muestras inclusivas**|Porcentaje de todas las muestras que se produjeron mientras se estaba ejecutando esta función o una función llamada por esta función.|  
|**Porcentaje de muestras exclusivas**|Porcentaje de muestras que se produjeron cuando la función estaba ejecutando código del cuerpo de la función.  No se incluyen las muestras recopiladas en funciones a las que llamó esta función.|  
  
## Funciones que realizan la mayor parte de trabajo individual  
 La lista **Funciones que realizan la mayor parte de trabajo individual** muestra las funciones que tienen el mayor número de muestras exclusivas de la ejecución de generación de perfiles.  Las muestras exclusivas se asignan a una función que está ejecutando su propio código cuando se recopila la muestra.  Las muestras exclusivas no se asignan a una función que está llamando a otra función cuando se recopila la muestra.  Un gran número de muestras exclusivas indica que se ha empleado un parte importante del tiempo en la propia función.  
  
 Puede hacer clic en una función para mostrar la vista Detalles de la función correspondiente.  Para mostrar otras vistas de la función, haga clic con el botón secundario del mouse en la función y, a continuación, haga clic en una vista de la lista.  
  
 **Funciones que realizan la mayor parte de trabajo individual** incluye los datos siguientes para cada función:  
  
|Columna|Descripción|  
|-------------|-----------------|  
|**Name**|Nombre de la función.|  
|**Porcentaje de muestras exclusivas**|Porcentaje de todas las muestras de la ejecución de generación de perfiles que se recopilaron mientras la función ejecutaba código de su cuerpo de función.  El porcentaje excluye las muestras recopiladas mientras se ejecutaban funciones a las que llamó esta función.|  
  
## Vea también  
 [Vista Resumen](../profiling/summary-view-dotnet-memory-data.md)   
 [Vista Resumen](../profiling/summary-view-instrumentation-data.md)