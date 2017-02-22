---
title: "Vista Llamador y destinatario: datos de muestreo del generador de perfiles | Microsoft Docs"
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
  - "método de generación de perfiles mediante muestreo, vista Llamador/Destinatario"
  - "Llamador y destinatario (vista)"
ms.assetid: 28e85ed5-1512-4b59-bb84-138a2abca7dd
caps.latest.revision: 14
caps.handback.revision: 14
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Vista Llamador y destinatario: datos de muestreo del generador de perfiles
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

La vista Llamador y destinatario muestra información de generación de perfiles para una función seleccionada y sus funciones primarias y secundarias.  Contiene tres cuadrículas.  
  
 **Función actual** se muestra en la cuadrícula central y presenta información de generación de perfiles para la función seleccionada.  Los valores incluyen todas las llamadas muestreadas a la función.  
  
 **Funciones que llamaron a la función actual** se muestra en la cuadrícula superior y presenta las contribuciones individuales de las funciones de llamador \(primarias\) a los valores de la función seleccionada \(actual\).  
  
 **Funciones llamadas por la función actual** se muestra en la cuadrícula inferior y presenta información de generación de perfiles para las funciones destinatarias \(secundarias\) de la función seleccionada cuando la función actual llamó a la función secundaria.  
  
> [!NOTE]
>  Las características de seguridad mejoradas en Windows 8 y Windows Server 2012 requirieron cambios significativos en la forma en que el generador de perfiles de Visual Studio recopila datos en estas plataformas.  Las aplicaciones de la Tienda Windows también requieren nuevas técnicas de recolección.  Vea [Generar perfiles de aplicaciones de Windows 8 y Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).  
  
|Columna|Descripción|  
|-------------|-----------------|  
|**Id. de proceso**|Identificador de proceso \(PID\) de la generación de perfiles.|  
|**Nombre del proceso**|Nombre del proceso.|  
|**Nombre de módulo**|Nombre del módulo que contiene la función.|  
|**Ruta de acceso del módulo**|Ruta de acceso del módulo que contiene la función.|  
|**Archivo de origen**|Archivo de origen que contiene la definición de esta función.|  
|**Nombre de la función**|El nombre completo de la función.|  
|**Número de línea de función**|Número de línea del inicio de esta función en el archivo de origen.|  
|**Dirección de función**|Dirección de la función.|  
|**Tipo**|El contexto de la función:<br /><br /> -   **0** \- la función actual<br />-   **1** \- una función que llama a la función actual<br />-   **2** \- una función a la que llama la función actual|  
|**Nombre de la función raíz**|El nombre de la función actual.|  
|**Ejemplos de inclusión**|-   En la función actual, el número de muestras que se recopilaron aunque se estaba ejecutando esta función o una de sus funciones secundarias.<br />-   En una función de llamador, el número de muestras inclusivas de la función actual que se recopilaron cuando esta función llamó a la función actual.<br />-   En una función de destinatario, el número de muestras inclusivas de esta función que se recopilaron cuando la función actual llamó a esta función.|  
|**Porcentaje de muestras inclusivas**|Porcentaje de muestras inclusivas de esta función con respecto a todas las muestras de la generación de perfiles.|  
|**Ejemplos de exclusión**|-   En la función actual, el número de muestras de la ejecución de generación de perfiles que se recopilaron cuando esta función se estaba ejecutando directamente; es decir, cuando esta función estaba en la parte superior de la pila de llamadas.  En los recuentos exclusivos no se incluyen las muestras recopiladas mientras se ejecutaban las funciones secundarias de esta función.<br />-   En una función de llamador, el número de muestras exclusivas de la función actual que se recopilaron cuando esta función llamó a la función actual.<br />-   En una función de destinatario, el número de muestras exclusivas de esta función que se recopilaron cuando la función actual llamó a esta función.|  
|**Porcentaje de muestras exclusivas**|Porcentaje de muestras exclusivas de esta función con respecto a todas las muestras de la generación de perfiles.|  
  
## Vea también  
 [Vista Llamador y destinatario \- Muestreo](../profiling/caller-callee-view-dotnet-memory-sampling-data.md)   
 [Vista Llamador y destinatario \- Instrumentación](../profiling/caller-callee-view-net-memory-instrumentation-data.md)   
 [Llamador y destinatario \(Vista\)](../profiling/caller-callee-view-instrumentation-data.md)