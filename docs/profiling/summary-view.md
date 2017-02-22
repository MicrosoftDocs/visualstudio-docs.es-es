---
title: "Vista Resumen | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.performance.view.summary"
helpviewer_keywords: 
  - "informes de rendimiento, Resumen (vista)"
  - "informes de herramientas de generación de perfiles, Resumen (vista)"
  - "herramientas de generación de perfiles, Resumen (vista)"
  - "Resumen (vista)"
ms.assetid: 98a1eb71-bbf5-4ce7-8559-cdc29f082c4b
caps.latest.revision: 37
caps.handback.revision: 37
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Vista Resumen
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

La vista Resumen muestra información sobre las funciones o los objetos con mayor incidencia en el rendimiento de una ejecución de generación de perfiles.  Esta vista proporciona un gráfico de escala de tiempo y dos o más listas de las funciones o los objetos más costosos basándose en las métricas de rendimiento del método de generación de perfiles.  Los datos de esta vista dependen del método de generación de perfiles utilizado \(muestreo, instrumentación o simultaneidad\) y de si se recopiló la asignación de memoria de .NET.  
  
 Para todas las vistas de resumen salvo la vista de resumen de los datos de simultaneidad, el gráfico de escala de tiempo de la vista de resumen muestra el porcentaje de utilización del procesador \(CPU\) por parte de la aplicación perfilada durante el tiempo en que se produjo la generación de perfiles.  
  
-   Si especifica un segmento de tiempo en el gráfico, puede volver a analizar los datos de ese segmento o enfocar la escala de tiempo en el segmento especificado.  Para obtener más información, vea [Cómo: Filtrar vistas de informe desde la escala de tiempo de resumen](../Topic/How%20to:%20Filter%20Report%20Views%20from%20the%20Summary%20Timeline.md)  
  
-   Puede hacer clic en una función en una lista de la vista Resumen para abrir la vista Detalles de la función correspondiente.  También puede hacer clic con el botón secundario en la función para otras opciones de vista.  
  
-   Para modificar el número de elementos que aparecen en las listas de la vista Resumen, abra el menú **Herramientas**, seleccione **Opciones** y, a continuación, haga clic en **Herramientas de rendimiento**.  En **Configuración general**, modifique el valor de **Número de funciones en la vista Resumen**.  
  
## Vínculos de notificaciones  
 Puede hacer clic en los vínculos de la lista Notificación para establecer las opciones de pantalla para el informe.  La lista está a la derecha del gráfico de escala de tiempo.  
  
|||  
|-|-|  
|**Mostrar código que no es de usuario**<br /><br /> **Mostrar solo mi código**|No está disponible para código nativo ni para los datos de generación de perfiles recopilados mediante el método de instrumentación.  Alterna entre sólo mostrar datos del código de usuario \(**Mostrar solo mi código**\) y mostrar datos de todo el código, incluyendo el código del sistema \(**Mostrar código que no es de usuario**\).  De forma predeterminada, los datos se limitan al código de usuario.  Para cambiar la configuración, vea [Cómo: Filtrar vistas de informes para mostrar Solo mi código](../Topic/How%20to:%20Filter%20Profiling%20Tools%20Report%20Views%20to%20Display%20Just%20My%20Code.md).|  
|**Ver información orientativa**|Muestra las advertencias de las reglas de rendimiento en la ventana **Lista de errores**.  Para obtener más información, vea [Usar reglas de rendimiento para analizar datos](../profiling/using-performance-rules-to-analyze-data.md)|  
  
## Informe  
 Puede hacer clic los vínculos de la lista Informe para abrir vistas diferentes y comparar, guardar o filtrar el informe.  La lista está a la derecha del gráfico de escala de tiempo.  
  
|||  
|-|-|  
|**Mostrar árbol de llamadas reducido**|Muestra las rutas de ejecución que más consumen en la vista de árbol de ejecución.  Para obtener más información, vea [Vista Árbol de llamadas](../profiling/call-tree-view.md).|  
|**Mostrar líneas activas**|No está disponible para los datos de generación de perfiles recopilados mediante el método de instrumentación.  Muestra el código fuente que más consume en la vista de líneas.  Para obtener más información, vea [Vista Líneas](../profiling/lines-view.md).|  
|**Comparar informes**|Muestra el cuadro de diálogo **Seleccionar archivos de análisis para compararlos** donde puede especificar otro archivo de datos de generación de perfiles para comparar con el archivo actual.  Para obtener más información, vea [Comparar archivos de datos de las herramientas de generación de perfiles](../profiling/comparing-performance-data-files.md).|  
|**Exportar datos de informe**|Muestra el cuadro de diálogo **Exportar informe** donde puede especificar una o más vistas de informe para guardar como archivos de valores separado por comas \(.csv\) o .xml.  Para obtener más información, vea [How to: Export Profiling Tools Reports](http://msdn.microsoft.com/es-es/174b5bd3-df9b-4fd4-88d4-76032ab90451).|  
|**Guardar informe analizado**|Guarda el archivo de datos de generación de perfiles actual como un archivo .vsps, el cual se abre más rápidamente en la interfaz de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  Para obtener más información, vea [How to: Save Analyzed Profiling Data Files](http://msdn.microsoft.com/es-es/0340ddde-caf4-48ac-8af3-d15dcdade556).|  
|**Filtrar datos del informe**|Muestra el panel de filtro de registro de informes de perfiles donde puede especificar los criterios para restringir los datos en la vista de informe.  Para obtener más información, vea [Filtro de la vista de informes de las herramientas de generación de perfiles](../profiling/performance-report-view-filter.md)|  
|**Alternar pantalla completa**|Alterna el modo de pantalla completa para la vista de informe.|  
  
## Vea también  
 [Vista Resumen](../profiling/summary-view-sampling-data.md)   
 [Vista Resumen](../profiling/summary-view-instrumentation-data.md)   
 [Vista Resumen](../profiling/summary-view-dotnet-memory-data.md)