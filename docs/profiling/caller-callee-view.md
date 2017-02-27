---
title: "Vista Llamador y destinatario | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.performance.view.callercallee"
helpviewer_keywords: 
  - "herramientas de generación de perfiles, informes, vista Llamador y destinatario"
  - "herramientas de generación de perfiles, vista Llamador y destinatario"
  - "informes de rendimiento, vista Llamador y destinatario"
  - "Llamador y destinatario (vista)"
ms.assetid: d3511bcf-cce0-4cbe-aecb-b94c7c80ad1b
caps.latest.revision: 32
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 32
---
# Vista Llamador y destinatario
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

La vista Llamador y destinatario muestra información de generación de perfiles para una función seleccionada y sus funciones primarias y secundarias.  Contiene tres cuadrículas:  
  
 **Función actual** se muestra en la cuadrícula central y presenta información de generación de perfiles para la función seleccionada.  Los valores incluyen todas las llamadas a la función que se recopilaron durante la generación de perfiles.  
  
 **Funciones que llamaron a la función actual** se muestra en la cuadrícula superior y presenta el número de valores de la función seleccionada \(actual\) generados por llamadas de la función llamadora \(primaria\).  
  
 **Funciones llamadas por la función actual** se muestra en la cuadrícula inferior y presenta información de generación de perfiles para las funciones destinatarias \(secundarias\) de la función seleccionada cuando la función actual llamó a la función secundaria.  
  
 Las columnas que están disponibles en la vista Llamador y destinatario dependen del método de generación de perfiles \(muestreo o instrumentación\) utilizado para recopilar los datos y de si se recopilaron datos de memoria de .NET durante la generación de perfiles.  
  
 Puede seleccionar otra función para que se convierta en la Función actual de la parte central de la vista Informe si hace doble clic en cualquiera de las funciones que aparecen en las otras dos partes de la vista.  La vista Informe se actualiza automáticamente para reflejar los cambios.  
  
 Puede ordenar los datos haciendo clic en los nombres de las columnas.  Se pueden agregar columnas adicionales a la vista Llamador y destinatario.  Para obtener más información, vea [Cómo: Personalizar las columnas de la vista de informes](../profiling/how-to-customize-report-view-columns.md).  
  
## Vea también  
 [Llamador y destinatario \(Vista\)](../profiling/caller-callee-view-sampling-data.md)   
 [Llamador y destinatario \(Vista\)](../profiling/caller-callee-view-instrumentation-data.md)   
 [Vista Llamador y destinatario \- Instrumentación](../profiling/caller-callee-view-net-memory-instrumentation-data.md)   
 [Vista Llamador y destinatario \- Muestreo](../profiling/caller-callee-view-dotnet-memory-sampling-data.md)   
 [Llamador y destinatario \(Vista\)](../profiling/caller-callee-view-contention-data.md)