---
title: "Vista M&#243;dulos | Microsoft Docs"
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
  - "vs.performance.view.modules"
helpviewer_keywords: 
  - "Módulos (vista)"
  - "informes de herramientas de generación de perfiles, Módulos (vista)"
  - "herramientas de generación de perfiles, Módulos (vista)"
ms.assetid: 4314a404-2120-425b-be42-180cd4bac840
caps.latest.revision: 17
caps.handback.revision: 17
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Vista M&#243;dulos
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

La vista Módulos enumera los módulos de los datos de generación de perfiles.  Cada módulo es el nodo raíz de un árbol jerárquico.  Las funciones del módulo de las que se han generado perfiles se enumeran bajo el nodo de módulo.  Si los datos de generación de perfiles se recopilaron utilizando el método de muestreo, la información de línea se enumera debajo del nodo de función y los datos del puntero de instrucciones se enumeran debajo del nodo de línea.  
  
 Expanda o contraiga el nombre del módulo para mostrar o cerrar la vista de los datos de rendimiento del módulo.  
  
 Para agregar o quitar columnas, haga clic con el botón secundario en la ventana de informes y, a continuación, seleccione **Agregar o quitar columnas**.  Puede ordenar los datos si hace clic en el nombre de una columna.  Para obtener más información, vea [Cómo: Personalizar las columnas de la vista de informes](../profiling/how-to-customize-report-view-columns.md).  
  
 Las columnas que están disponibles en la vista Módulos dependen del método de generación de perfiles \(muestreo o instrumentación\) utilizado para recopilar los datos y de si se recopilaron datos de memoria de .NET durante la generación de perfiles.  
  
## Vea también  
 [Vista Módulos](../profiling/modules-view-sampling-data.md)   
 [Vista Módulos](../profiling/modules-view-instrumentation-data.md)   
 [Vista de módulos \- Instrumentación](../profiling/modules-view-dotnet-memory-instrumentation-data.md)   
 [Vista de módulos \- Muestreo](../profiling/modules-view-dotnet-memory-sampling-data.md)   
 [Vista Módulos](../profiling/modules-view-contention-data.md)