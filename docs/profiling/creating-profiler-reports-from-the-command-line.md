---
title: 'Línea de comandos de generación de perfiles: creación de informes'
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: c886f8af-2014-4fec-9b24-d98b68ecafb7
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 5eb0f1fa0f9bbe760b1ea89074d02044cf26ab7d
ms.sourcegitcommit: 566144d59c376474c09bbb55164c01d70f4b621c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2020
ms.locfileid: "90808830"
---
# <a name="create-profiler-reports-from-the-command-line"></a>Creación de informes del generador de perfiles desde la línea de comandos
La herramienta de línea de comandos **VSPerfReport** permite crear informes .*xml* o de valores separados por comas (.*csv*) a partir de archivos de datos de generación de perfiles (.*vsp*). Los tipos de informes VSPerfReport coinciden estrechamente con las vistas basadas en las tablas de la interfaz para [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Puede filtrar el informe para mostrar solo su código y mostrar solo un segmento del archivo de datos de generación de perfiles. Para obtener más información, consulte [VSPerfReport](../profiling/vsperfreport.md).

 También puede hacer que los archivos de datos de generación de perfiles sean más fáciles de compartir si inserta símbolos en los archivos .*vsp* y crea archivos de informe preanalizados (.*vsps*) que son menores y más rápidos de abrir.

## <a name="common-tasks"></a>Tareas comunes

|Tarea|Contenido relacionado|
|----------|---------------------|
|**Crear un informe básico.** Cree todos o un subconjunto de los tipos de informe de VSPerfReport.|-   [Crear informes básicos](../profiling/creating-basic-profiling-reports-from-the-command-line.md)|
|**Comparar dos archivos de datos de generación de perfiles.** Cree un informe "diff" que compara los datos de rendimiento en dos archivos de datos de generación de perfiles.|-   [Cómo: Crear un informe de comparación del generador de perfiles desde un símbolo del sistema](../profiling/how-to-create-a-profiler-comparison-report-from-a-command-prompt.md)|
|**Ver datos de seguimiento de llamadas y de Seguimiento de eventos de Windows (ETW).** Cree un informe de seguimiento de llamadas que muestre información del control de tiempo para cada punto de entrada y salida de las funciones de la aplicación y de cada llamada de la función a otras funciones. O bien, cree una lista detallada de todos los eventos ETW que se recopilaron en una ejecución de generación de perfiles.|-   [Cómo: Crear un informe de seguimiento de llamadas](../profiling/how-to-create-a-profiling-tools-call-trace-report.md)|
|**Filtrar un informe.** Limite un informe exclusivamente a las funciones del código o a un tiempo concreto en el archivo de datos de generación de perfiles.|-   [Cómo: Filtrar informes desde la línea de comandos](../profiling/how-to-filter-reports-from-the-command-line.md)|
|**Crear archivos de datos de generación de perfiles portátiles.** Para facilitar el uso compartido de los datos de generación de perfiles, puede insertar los símbolos para una ejecución de generación de perfiles en el archivo .*vsp*. También puede crear un archivo de datos de generación de perfiles pre-analizado (.*vsps*) que es menor y más rápido en abrirse.|-   [Crear archivos de datos de generación de perfiles portátiles](../profiling/creating-portable-profiling-data-files-from-the-command-line.md)|
