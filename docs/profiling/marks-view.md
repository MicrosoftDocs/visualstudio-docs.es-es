---
title: "Vista Marcas | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.performance.view.marks"
helpviewer_keywords: 
  - "informes de herramientas de generación de perfiles, Marcas (vista)"
  - "herramientas de generación de perfiles, Marcas (vista)"
ms.assetid: b2773344-8081-4116-85a1-58f770448f6a
caps.latest.revision: 18
caps.handback.revision: 18
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Vista Marcas
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

En la vista Marcas se muestran eventos ETW y de muestreo que se insertaron en la aplicación.  
  
 Las marcas predeterminadas rellenadas en el informe etiquetan el inicio y el final del programa.  
  
 Los datos de los contadores de Windows de las marcas generadas automáticamente también se presentan en esta vista.  Para obtener más información, vea [Cómo: Recopilar datos de contadores de Windows](../profiling/how-to-collect-windows-counter-data.md).  
  
 Para crear un filtro entre dos marcas, seleccione las marcas, haga clic con el botón secundario y, a continuación, haga clic en la opción **Agregar filtro por Marcas** o **Agregar filtro por Marca de tiempo**.  
  
 En la tabla siguiente se proporcionan las definiciones de las columnas disponibles en la vista Marcas.  
  
 **Id. de marca**  
 Identificador único de la marca de generación de perfiles.  
  
 **Nombre de marca**  
 Nombre del evento.  
  
 **Marca de tiempo**  
 Tiempo desde el comienzo de la generación de perfiles hasta el momento en que se registra el evento.  
  
 Datos del contador de rendimiento de Windows  
 Cuando se recopilan los datos del contador de rendimiento de Windows, los valores se muestran en una columna que tiene el nombre del contador.  
  
## Vea también  
 [Introducción a los informes de las herramientas de generación de perfiles](../profiling/performance-report-overview.md)   
 [\<PAVE\_OVER\> Procedimiento: configurar marcas de generación de perfiles](../Topic/%3CPAVE_OVER%3E%20How%20to:%20Configure%20Profiling%20Marks.md)   
 [\<PAVE\_OVER\> Cómo: Insertar marcas en un archivo de datos del generador de perfiles](../Topic/%3CPAVE_OVER%3E%20How%20to:%20Insert%20Marks%20in%20a%20Profiler%20Data%20File.md)   
 [Cómo: Recopilar datos de contadores de Windows](../profiling/how-to-collect-windows-counter-data.md)   
 [Control de recolección de datos \(ventana\)](http://msdn.microsoft.com/es-es/98d740d8-459f-4605-bf04-fb17aafaaa8f)