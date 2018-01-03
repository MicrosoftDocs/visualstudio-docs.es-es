---
title: Comparar archivos de datos de rendimiento | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- profiling tools, comparing profiling tools report files
- profiling tools reports, comparing
ms.assetid: e6fda144-f21d-4912-9d16-1b8d3555a210
caps.latest.revision: "12"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 734d0531cf1fbbbc2f7924cb1743cabf9e4a9578
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="comparing-performance-data-files"></a>Comparar archivos de datos de rendimiento
La funcionalidad de comparación de archivos de datos de herramientas de generación de perfiles permite seleccionar dos archivos de informe (.VSP o .VSPS) y generar un informe que muestra las diferencias, las regresiones de rendimiento y las mejoras producidas de una sesión de generación de perfiles a otra.  
  
 En un informe de comparación de archivos de datos de herramientas de generación de perfiles [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] se comparan los resultados de un análisis en un archivo de datos de generación de perfiles con los resultados de un análisis de línea base en otro archivo de datos. Ambos archivos de datos deben haberse generado mediante el mismo método de generación de perfiles. El informe de las comparaciones analizadas se guarda como un archivo .vsps.  
  
 La vista del informe de comparación presenta una tabla con los datos modificados. La tabla presenta el delta o cambio de la línea base. El delta se calcula determinando la diferencia entre el valor anterior, el valor de la línea base y el valor del resultado del nuevo análisis.  
  
 Las comparaciones de datos del generador de perfiles pueden basarse en las funciones del código, los módulos de la aplicación, las líneas, los punteros de instrucciones (IP) y los tipos.  
  
 Los datos de generación de perfiles disponibles para la comparación incluyen la información que se muestra en las columnas. Para obtener definiciones de los nombres de estas columnas, consulte [Vistas de informes de rendimiento](../profiling/performance-report-views.md).  
  
 Puede establecerse un umbral para reducir el ruido y filtrar los datos en la vista de la tabla de comparación de las filas que no han cambiado en una cantidad especificada.  
  
## <a name="in-this-section"></a>En esta sección  
 [Cómo: Comparar archivos de datos de rendimiento](../profiling/how-to-compare-performance-data-files.md)