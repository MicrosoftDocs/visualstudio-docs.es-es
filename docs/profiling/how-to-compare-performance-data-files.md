---
title: 'Cómo: Comparar archivos de datos de rendimiento | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vsperf.choosediffbinaries
helpviewer_keywords:
- profiling tools, how to compare profiler result files
- profiler result files, how to compare
ms.assetid: 1905b45d-c6b3-43c8-87b1-1aee734f37f9
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: eeb9f26091deaf995ef1221d39aa7264553f5c70
ms.sourcegitcommit: 1b9c1e333c2f096d35cfc77e846116f8e5054557
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/06/2018
ms.locfileid: "34815384"
---
# <a name="how-to-compare-performance-data-files"></a>Cómo: Comparar archivos de datos de rendimiento
Puede crear un informe o una vista de comparación ("Diff") para comparar los resultados de dos archivos de datos de generador de perfiles diferentes (.*vsp* o .*vsps*). La comparación muestra las diferencias, reducciones de rendimiento y mejoras producidas de una sesión de generación de perfiles a la otra.  
  
 El informe Diff presenta una vista de tabla de los datos. La tabla presenta el delta o cambio de la línea base. Esto se calcula determinando la diferencia entre el valor anterior, el valor de la línea base y el valor de resultado del nuevo análisis.  
  
 Las comparaciones de datos del generador de perfiles pueden basarse en las funciones en el código, los módulos de la aplicación, las líneas, los punteros de instrucción (IP) y los tipos.  
  
 Se puede establecer un umbral para reducir el ruido y filtrar cualquier dato que aparezca en la vista de tabla de las filas que no han cambiado en una cantidad especificada.  
  
### <a name="to-create-comparison-file-view-for-a-project-in-performance-explorer"></a>Para crear una vista de archivos de comparación para un proyecto en el Explorador de rendimiento  
  
1.  En **Explorador de rendimiento**, en **Informes**, seleccione el archivo de informe .*vsp* o .*vsps* que quiere utilizar como valores de línea base para la comparación.  
  
2.  Seleccione los archivos de informe .*vsp* o .*vsps* que quiera comparar.  
  
3.  Haga clic con el botón derecho en uno de los archivos seleccionados y después en **Comparar informes**.  
  
### <a name="to-compare-values"></a>Para comparar valores  
  
1.  Seleccione la pestaña **Informe de comparación** en la ventana Vista de informe.  
  
2.  En la lista desplegable **Tabla**, seleccione la función o los módulos para comparar.  
  
3.  En la lista desplegable **Columna**, seleccione el valor que desea comparar.  
  
4.  (opcional) Escriba un valor para **Umbral**.  
  
5.  Haga clic en **Aplicar**.  
  
### <a name="to-compare-report-files"></a>Para comparar archivos de informe  
  
1.  En el menú **Analizar**, seleccione **Comparar informes de rendimiento**.  
  
2.  En la ventana **Seleccionar archivos de análisis para compararlos**, busque y seleccione el archivo de análisis **Archivo de línea base** (.*vsp* o .*vsps*) y el **Archivo de comparación** (.*vsp* o .*vsps*).  
  
3.  Haga clic en **Aceptar**.