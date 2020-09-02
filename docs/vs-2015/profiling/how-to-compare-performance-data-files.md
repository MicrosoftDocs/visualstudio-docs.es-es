---
title: 'Cómo: Comparar archivos de datos de rendimiento | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vsperf.choosediffbinaries
helpviewer_keywords:
- profiling tools, how to compare profiler result files
- profiler result files, how to compare
ms.assetid: 1905b45d-c6b3-43c8-87b1-1aee734f37f9
caps.latest.revision: 25
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 185494623e019ef666374bd46e52bca0d58738f4
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "68185938"
---
# <a name="how-to-compare-performance-data-files"></a>Cómo: Comparar archivos de datos de rendimiento
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Puede crear un informe o una vista de comparación ("Diff") para comparar los resultados de dos archivos de datos de generador de perfiles diferentes (.vsp o .vsps). La comparación muestra las diferencias, reducciones de rendimiento y mejoras producidas de una sesión de generación de perfiles a la otra.  
  
 El informe Diff presenta una vista de tabla de los datos. La tabla presenta el delta o cambio de la línea base. Esto se calcula determinando la diferencia entre el valor anterior, el valor de la línea base y el valor de resultado del nuevo análisis.  
  
 Las comparaciones de datos del generador de perfiles pueden basarse en las funciones en el código, los módulos de la aplicación, las líneas, los punteros de instrucción (IP) y los tipos.  
  
 Se puede establecer un umbral para reducir el ruido y filtrar cualquier dato que aparezca en la vista de tabla de las filas que no han cambiado en una cantidad especificada.  
  
### <a name="to-create-comparison-file-view-for-a-project-in-performance-explorer"></a>Para crear una vista de archivos de comparación para un proyecto en el Explorador de rendimiento  
  
1. En **Explorador de rendimiento**, en **informes**, seleccione el archivo de informe. VSP o. VSPs que desea usar como valores de línea de base para la comparación.  
  
2. Seleccione los archivos de informe .vsp o .vsps que desea comparar.  
  
3. Haga clic con el botón derecho en uno de los archivos seleccionados y después en **Comparar informes**.  
  
### <a name="to-compare-values"></a>Para comparar valores  
  
1. Seleccione la pestaña **Informe de comparación** en la ventana Vista de informe.  
  
2. En la lista desplegable **Tabla**, seleccione la función o los módulos para comparar.  
  
3. En la lista desplegable **Columna**, seleccione el valor que desea comparar.  
  
4. (opcional) Escriba un valor para **Umbral**.  
  
5. Haga clic en **Aplicar**.  
  
### <a name="to-compare-report-files"></a>Para comparar archivos de informe  
  
1. En el menú **Analizar**, seleccione **Comparar informes de rendimiento**.  
  
2. En la ventana **seleccionar archivos de análisis para compararlos** , busque y seleccione el archivo de análisis de **archivos de línea de base** (. VSP o. VSPs) y el archivo de **comparación** (. VSP o. VSPs).  
  
3. Haga clic en **Aceptar**.
