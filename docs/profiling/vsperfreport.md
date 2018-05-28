---
title: VSPerfReport | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- command-line tools, VSPerfReporttool
- performance tools, VSPerfReport tool
- profiling tools,VSPerfReport
- VSPerfReport tool
- command line, tools
- instrumentation, VSPerfReporttool
ms.assetid: dbfd8d91-4430-4b82-81b9-97ac61412a6c
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: f0c0c67664cfc111483e27bc28cf39afb315b80f
ms.sourcegitcommit: 1466ac0f49ebf7448ea4507ae3f79acb25d51d3e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/22/2018
---
# <a name="vsperfreport"></a>VSPerfReport
La herramienta de la línea de comandos VSPerfReport se usa para crear informes mediante los archivos de datos para la generación de perfiles de las Herramientas de generación de perfiles de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. El formato de informe predeterminado es un archivo .csv.  
  
 VSPerfReport usa la sintaxis siguiente:  
  
```cmd  
VSPerfReport [/U] vspfilename [/options]  
```  
  
 Tenga en cuenta que `filename` debe ser un archivo .vsp o .vsps válido.  
  
 La herramienta de línea de comandos VSPerfReport también se usa para comparar archivos .vsp o .vsps. Para generar un informe de diferencias ("diff"), use la sintaxis siguiente:  
  
```cmd  
VSPerfReport [/U] /diff vspfilename1 vspfilename2 [/options]  
```  
  
 `vspfilename1 and vspfilename2` deben ser archivos .vsp o .vsps válidos.  
  
## <a name="symbol-files"></a>Archivos de símbolos  
 Para mostrar información de símbolos como nombres de función y números de línea, VSPerfReport requiere acceso a los archivos de símbolos (.PDB) de los componentes para los que se generan perfiles y a los archivos de símbolos de Windows. Para obtener más información, consulte [Cómo: Especificar ubicaciones del archivo de símbolos desde la línea de comandos](../profiling/how-to-specify-symbol-file-locations-from-the-command-line.md).  
  
## <a name="general-report-options"></a>Opciones generales de informe  
 En la tabla siguiente se describen las opciones generales de formato del informe y las opciones que seleccionan los datos de los que se va a informar.  
  
|Opciones|Description|  
|-------------|-----------------|  
|**U**|El informe de resultados y la salida de la consola redirigida se escriben como Unicode. Esta debe ser la primera opción especificada.|  
|**Summary:**[*types*]|Crea uno o varios tipos de informes.<br /><br /> -   `All`: se generan todos los tipos de informes.<br />-   `CallerCallee`: relaciones de elemento primario/secundario entre funciones.<br />-   `Function`: funciones llamadas.<br />-   `CallTree`: jerarquía de funciones llamadas.<br />-   `Counter`: todas las marcas junto con valores del contador de rendimiento de Windows.<br />-   `Ip`: instrucciones para las que se generan perfiles.<br />-   `Life`: duración de los objetos asignados (disponible cuando se han recopilado datos de asignaciones).<br />-   `Line`: datos del perfil de la línea de código fuente.<br />-   `Header`: el informe contiene información del encabezado del archivo.<br />-   `Mark`: todas las marcas.<br />-   `Module`: módulos para los que se generan perfiles.<br />-   `Process`: procesos para los que se generan perfiles.<br />-   `Thread`: subprocesos para los que se generan perfiles.<br />-   `Type`: tipos asignados.<br />-   `Contention`: contenciones de recursos.<br />-   `RuleWarnings`: problemas de reglas de rendimiento.<br />-   `ETW`: todos los eventos de Seguimiento de eventos para Windows (ETW) recopilados en la generación de perfiles. El archivo de datos .etl debe estar en su ubicación original o en el directorio que contiene el archivo .vsp o .vsps.|  
|**Xml**|Informe de resultados en formato XML.|  
|**CallTrace**|Crea una lista de entradas y salidas de la función, eventos ETW y marcas.|  
|**ClearPackedSymbols**|Quita los símbolos insertados previamente de un archivo de datos del generador de perfiles. Ejecute este comando antes de ejecutar PackSymbols por segunda vez.|  
|**SymbolPath:** `path`|Especifica una o más rutas de acceso de búsqueda o servidores de símbolos que contienen los símbolos para el archivo de datos del generador de perfiles.|  
|**DebugSymPath**|Enumera las ubicaciones en las que se buscan los símbolos y si se encuentran. Esta opción es útil para resolver problemas de resolución de símbolos.|  
|**PackSymbols**|Guarda los símbolos en el archivo de datos de generación de perfiles (.vsp) de modo que los archivos de símbolos (.pdb) no se requieran en el análisis.|  
|**Output:** *path*&#124;*filename*|Especifica una ubicación alternativa para los archivos de informe generados. De forma predeterminada, los informes se crean en el directorio actual.|  
|**SummaryFile**|Analiza y guarda la información analizada en un archivo de resumen .vsps.|  
|**PrintMarks**|Muestra los nombres y marcas de tiempo para todas las marcas del archivo de informe especificado.|  
|**?**|Muestra información de uso.|  
|**NoLogo**|Oculta la información de versión cuando el informe se está ejecutando.|  
|**UserRulesDirectory**|Especifica el directorio que contiene las reglas de rendimiento definidas por el usuario [todavía sin implementar].|  
  
## <a name="filter-options"></a>Opciones de filtro  
 En la tabla siguiente se describen las opciones para filtrar los datos disponibles.  
  
|Opciones|Description|  
|-------------|-----------------|  
|**JustMyCode**[**:**[`caller`][,`callee`]]|Solo se muestran las llamadas a funciones de aplicación de usuario; se ocultan las llamadas al sistema.<br /><br /> - Ningún parámetro: se ocultan todas las funciones del sistema.<br />-   `caller`: se muestra un nivel de las funciones del sistema que llaman a las funciones de aplicación.<br />-   `callee`: se muestra un nivel de las funciones del sistema invocadas por las funciones de aplicación de usuario.|  
|**StartTime:**[*value*]|Solo muestra los datos recopilados tras el valor (en milisegundos).|  
|**EndTime:**[*value*]|Solo muestra los datos recopilados antes del valor (en milisegundos).|  
|**FilterFile:** `VSPFFile`|Especifica la ubicación de un archivo de filtro que se generó en la ventana Informe de rendimiento de Visual Studio.|  
|**MsFilter:**[*starttime,duration*]|Solo se muestran los datos de `starttime` hasta la longitud de `duration` (en milisegundos).|  
|**Process:**[*pid*]|Solo muestra los datos del proceso especificado.|  
|**Thread:**[*threadid*]|Solo muestra los datos del subproceso especificado.|  
|**Thread:**[*threadid,processid*]|Solo muestra los datos del subproceso especificado asociado al proceso especificado.|  
  
## <a name="difference-report-options"></a>Opciones del informe de diferencias  
 En la tabla siguiente se describen las opciones para comparar archivos de informe.  
  
|Opciones|Description|  
|-------------|-----------------|  
|**Diff**  `vspfile1 vspfile2`|Compare dos archivos de informe (.vsp o .vsps). Las opciones de resumen se omitirán mediante la opción diff.|  
|**Diff:**[*value*]|Se descarta cualquier diferencia entre dos valores que se encuentre bajo este valor de umbral. Asimismo, no se muestran nuevos datos que tengan valores por debajo de este umbral.|  
|**DiffTable:**[*tablename*]|Use esta tabla concreta para comparar archivos. El valor predeterminado es la tabla de funciones.|  
|**DiffColumn:**[*columnname*]|Use estos valores de comparación de columna específicos. El valor predeterminado es la columna de porcentaje de muestras exclusivas.|  
|**QueryDiffTables**|Muestra las tablas y columnas válidas para los dos archivos de informe proporcionados.|  
  
## <a name="see-also"></a>Vea también  
 [Vistas de informes de rendimiento](../profiling/performance-report-views.md)