---
title: Crear informes del generador de perfiles desde la línea de comandos | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: c886f8af-2014-4fec-9b24-d98b68ecafb7
caps.latest.revision: 12
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 489ebd4e5aff3ef9b93ef0d8fe18f9ae8cc85011
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "62537207"
---
# <a name="creating-profiler-reports-from-the-command-line"></a>Crear informes del generador de perfiles desde la línea de comandos
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La herramienta de línea de comandos **VSPerfReport** permite crear informes. XML o de valores separados por comas (. csv) a partir de archivos de datos de generación de perfiles (. VSP). Los tipos de informes VSPerfReport coinciden estrechamente con las vistas basadas en las tablas de la interfaz para [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Puede filtrar el informe para mostrar solo su código y mostrar solo un segmento del archivo de datos de generación de perfiles. Para obtener más información, consulte [VSPerfReport](../profiling/vsperfreport.md).  
  
 También puede hacer que los archivos de datos de generación de perfiles sean más fáciles de compartir incrustando símbolos en los archivos .vsp y creando archivos de informe pre-analizados (.vsps) que son menores y más rápidos de abrir.  
  
## <a name="common-tasks"></a>Tareas comunes  
  
|Tarea|Contenido relacionado|  
|----------|---------------------|  
|**Crear un informe básico.** Cree todos o un subconjunto de los tipos de informe de VSPerfReport.|-   [Crear informes básicos](../profiling/creating-basic-profiling-reports-from-the-command-line.md)|  
|**Comparar dos archivos de datos de generación de perfiles.** Cree un informe "diff" que compara los datos de rendimiento en dos archivos de datos de generación de perfiles.|-   [Cómo: crear un informe de comparación del generador de perfiles desde un símbolo del sistema](../profiling/how-to-create-a-profiler-comparison-report-from-a-command-prompt.md)|  
|**Ver datos de seguimiento de llamadas y de Seguimiento de eventos de Windows (ETW).** Cree un informe de seguimiento de llamadas que muestre información del control de tiempo para cada punto de entrada y salida de las funciones de la aplicación y de cada llamada de la función a otras funciones. O bien, cree una lista detallada de todos los eventos ETW que se recopilaron en una ejecución de generación de perfiles.|-   [Cómo: crear un informe de seguimiento de llamadas](../profiling/how-to-create-a-profiling-tools-call-trace-report.md)|  
|**Filtrar un informe.** Limite un informe exclusivamente a las funciones del código o a un tiempo concreto en el archivo de datos de generación de perfiles.|-   [Cómo: filtrar informes desde la línea de comandos](../profiling/how-to-filter-reports-from-the-command-line.md)|  
|**Crear archivos de datos de generación de perfiles portátiles.** Para facilitar el uso compartido de los datos de generación de perfiles, puede incrustar los símbolos para una ejecución de generación de perfiles en el archivo .vsp. También puede crear un archivo de datos de generación de perfiles pre-analizado (.vsps) que es menor y más rápido en abrirse.|-   [Crear archivos de datos de generación de perfiles portátiles](../profiling/creating-portable-profiling-data-files-from-the-command-line.md)|
