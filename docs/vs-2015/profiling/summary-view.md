---
title: Vista Resumen | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.performance.view.summary
helpviewer_keywords:
- performance reports, summary view
- profiling tools reports, Summary view
- profiling tools, Summary view
- Summary view
ms.assetid: 98a1eb71-bbf5-4ce7-8559-cdc29f082c4b
caps.latest.revision: 42
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: f4346b0e7459ee3c78669ab9178555370ffac16d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "85545514"
---
# <a name="summary-view"></a>Vista Resumen
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

En la vista Resumen se muestra información sobre las funciones o los objetos más exigentes en una generación de perfiles. Esta vista proporciona un gráfico de escala de tiempo y dos o más listas de las funciones o los objetos más exigentes según las métricas de rendimiento del método de generación de perfiles. Los datos de esta vista dependen del método de generación de perfiles utilizado (muestreo, instrumentación o simultaneidad) y de si se ha recopilado la asignación de memoria de .NET.  
  
 Para todas las vistas Resumen, salvo la de datos de simultaneidad, el gráfico de escala de tiempo de la vista Resumen muestra la utilización del procesador (CPU) de la aplicación de la que se generan perfiles durante el tiempo en que se ha producido la generación de perfiles.  
  
- Si especifica un segmento de tiempo en el gráfico, puede volver a analizar los datos para ese segmento o acercar la presentación de la escala de tiempo al segmento especificado. Para obtener más información, vea [Cómo: filtrar vistas de informe desde la escala de tiempo de resumen.](../profiling/how-to-filter-report-views-from-the-summary-timeline.md)  
  
- Puede hacer clic en una función en una lista de la vista Resumen para abrir la vista Detalles de la función. También puede hacer clic con el botón derecho en la función para acceder a otras opciones de vista.  
  
- Para modificar el número de elementos que aparecen en las listas de la vista Resumen, abra el menú **Herramientas**, elija **Opciones** y, a continuación, haga clic en **Herramientas de rendimiento**. En **Configuración general**, modifique el valor **Número de funciones de la vista Resumen**.  
  
## <a name="notifications-links"></a>Vínculos de notificaciones  
 Puede hacer clic en los vínculos de la lista de notificaciones para establecer opciones de presentación para el informe. La lista está situada a la derecha del gráfico de escala de tiempo.  
  
|Opción|Descripción|  
|-|-|  
|**Mostrar código de no usuario**<br /><br /> **Mostrar solo mi código**|No está disponible para código nativo o para generar perfiles de datos que se han recopilado mediante el método de instrumentación. Alterna entre mostrar solo los datos de código de usuario (**Mostrar solo mi código**) y los datos de todo el código, incluido el código del sistema (**Mostrar código de no usuario**). De forma predeterminada, los datos se limitan al código de usuario. Para cambiar la configuración, consulte [Cómo: filtrar herramientas de generación de perfiles vistas de informe para mostrar solo mi código](../profiling/how-to-filter-profiling-tools-report-views-to-display-just-my-code.md).|  
|**Consultar la información orientativa**|Muestra las advertencias de reglas de rendimiento en la ventana **Lista de errores**. Para obtener más información, consulte [Usar reglas de rendimiento para analizar datos](../profiling/using-performance-rules-to-analyze-data.md)|  
  
## <a name="report"></a>Informe  
 Puede hacer clic en los vínculos de la lista del informe para abrir vistas diferentes y para comparar, guardar o filtrar el informe. La lista está situada a la derecha del gráfico de escala de tiempo.  
  
|Nombre|Descripción|  
|-|-|  
|**Mostrar árbol de llamadas reducido**|Muestra las rutas de acceso de ejecución más exigentes en la vista Árbol de llamadas. Para obtener más información, consulte [vista árbol de llamadas](../profiling/call-tree-view.md).|  
|**Mostrar líneas activas**|No está disponible para generar perfiles de datos que se han recopilado mediante el método de instrumentación. Muestra las líneas de código fuente más exigentes en la vista Líneas. Para obtener más información, consulte la [vista líneas](../profiling/lines-view.md).|  
|**Comparar informes**|Muestra el cuadro de diálogo **Seleccionar archivos de análisis para la comparación**, en el que puede especificar otro archivo de datos de generación de perfiles para compararlo con el archivo actual. Para obtener más información, consulte [Comparar archivos de datos de rendimiento](../profiling/comparing-performance-data-files.md).|  
|**Exportar datos de informe**|Muestra el cuadro de diálogo **Exportar informe**, en el que puede especificar una o varias vistas de informe para guardar como archivos de valores separados por comas (.csv) o .xml. Para obtener más información, vea [Cómo: exportar informes de herramientas de generación de perfiles](https://msdn.microsoft.com/174b5bd3-df9b-4fd4-88d4-76032ab90451).|  
|**Guardar informe analizado**|Guarda el archivo de datos de generación de perfiles actual como un archivo .vsps, que se abre más rápidamente en la interfaz para [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Para obtener más información, vea [Cómo: guardar archivos de datos de generación de perfiles analizados](https://msdn.microsoft.com/0340ddde-caf4-48ac-8af3-d15dcdade556).|  
|**Filtrar datos del informe**|Muestra el panel de filtro del informe de generación de perfiles, en el que puede especificar criterios para restringir los datos de la vista Informe. Para obtener más información, vea [filtro de vista de informe de rendimiento](../profiling/performance-report-view-filter.md)|  
|**Alternar pantalla completa**|Alterna el modo de pantalla completa para la vista Informe.|  
  
## <a name="see-also"></a>Consulte también  
 [Vista Resumen](../profiling/summary-view-sampling-data.md)   
 [Vista Resumen](../profiling/summary-view-instrumentation-data.md)   
 [Vista Resumen](../profiling/summary-view-dotnet-memory-data.md)
