---
title: Referencia de la línea de comandos de MSBuild | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, msbuild.exe
- MSBuild, command line reference
- msbuild.exe
ms.assetid: edaa65ec-ab8a-42a1-84cb-d76d5b2f4584
caps.latest.revision: 61
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3a1827166829686801743ccc98156a0009e50dc3
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2018
ms.locfileid: "49245913"
---
# <a name="msbuild-command-line-reference"></a>Referencia de la línea de comandos de MSBuild
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Si usa MSBuild.exe para compilar un proyecto o archivo de solución, puede incluir varios modificadores para especificar distintos aspectos del proceso.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
MSBuild.exe [Switches] [ProjectFile]  
```  
  
## <a name="arguments"></a>Argumentos  
  
|Argumento|Descripción|  
|--------------|-----------------|  
|`ProjectFile`|Crea los destinos en el archivo de proyecto especificado. Si no se especifica un archivo de proyecto, MSBuild busca en el archivo de trabajo actual una extensión de nombre de archivo que termine en "proj" y usa ese archivo. También puede especificar un archivo de solución de Visual Studio para este argumento.|  
  
## <a name="switches"></a>Modificadores  
  
|Modificador|Forma abreviada|Descripción|  
|------------|----------------|-----------------|  
|/help|/? o /h|Muestra información de uso. El comando siguiente muestra un ejemplo:<br /><br /> `msbuild.exe /?`|  
|/detailedsummary|/ds|Muestra información detallada al final del registro de compilación sobre las configuraciones que se compilaron y cómo se programaron en los nodos.|  
|/ignoreprojectextensions: `extensions`|/ignore: `extensions`|Omite las extensiones especificadas al determinar qué archivo de proyecto se va a compilar. Use un punto y coma o una coma para separar varias extensiones, como se muestra en el ejemplo siguiente:<br /><br /> `/ignoreprojectextensions:.vcproj,.sln`|  
|/maxcpucount[:`number`]|/m[:`number`]|Especifica el número máximo de procesos simultáneos que se pueden usar al compilar. Si no incluye este modificador, el valor predeterminado es 1. Si incluye este modificador sin especificar un valor, MSBuild podrá usar todos los procesadores de que disponga el equipo. Para obtener más información, consulte [Compilar varios proyectos en paralelo](../msbuild/building-multiple-projects-in-parallel-with-msbuild.md).<br /><br /> En el ejemplo siguiente se indica a MSBuild que efectúe la compilación usando tres procesos de MSBuild, lo que permite compilar tres proyectos al mismo tiempo:<br /><br /> `msbuild myproject.proj /maxcpucount:3`|  
|/noautoresponse|/noautorsp|No incluye automáticamente ningún archivo MSBuild.rsp.|  
|/nodeReuse:`value`|/nr:`value`|Habilita o deshabilita la reutilización de los nodos de MSBuild. Puede especificar los siguientes valores:<br /><br /> -   **True**. Los nodos permanecen al finalizar la compilación de modo que las compilaciones subsiguientes puedan usarlos (valor predeterminado).<br />-   **False**. Los nodos no se conservan después finalizar la compilación.<br /><br /> Un nodo corresponde a un proyecto que se está ejecutando. Si incluye el modificador **/maxcpucount**, se podrán ejecutar varios nodos simultáneamente.|  
|/nologo||No muestra la pancarta de inicio ni el mensaje de copyright.|  
|/preprocess[:`filepath`]|/pp[:`filepath`]|Crea un solo archivo de proyecto agregado alineando todos los archivos que se importarían durante una compilación, con sus límites marcados. Puede usar este modificador para determinar con mayor facilidad qué archivos se van a importar, desde dónde y cuáles contribuirán a la compilación. Si se usa este modificador, el proyecto no se compila.<br /><br /> Si especifica el parámetro `filepath`, el archivo de proyecto agregado se genera en el archivo. En caso contrario, los resultados aparecen en la ventana de la consola.<br /><br /> Para obtener información sobre cómo usar el elemento `Import` para insertar un archivo del proyecto en otro archivo del proyecto, consulte [Elemento Import (MSBuild)](../msbuild/import-element-msbuild.md) y [Cómo: Usar el mismo destino en varios archivos del proyecto](../msbuild/how-to-use-the-same-target-in-multiple-project-files.md).|  
|/property:`name`=`value`|/p:`name`=`value`|Establece o invalida las propiedades en el nivel de proyecto especificadas, donde `name` es el nombre de la propiedad y `value` es el valor de propiedad. Especifique cada propiedad por separado, o use un punto y coma o una coma para separar varias propiedades, como se muestra en el ejemplo siguiente:<br /><br /> `/property:WarningLevel=2;OutDir=bin\Debug`|  
|/target:`targets`|/t:`targets`|Compila los destinos especificados en el proyecto. Especifique cada destino por separado, o use un punto y coma o una coma para separar varios destinos, como se muestra en el ejemplo siguiente:<br /><br /> `/target:Resources;Compile`<br /><br /> Si especifica destinos usando este modificador, estos se ejecutarán en lugar de los especificados en el atributo `DefaultTargets` del archivo de proyecto. Para obtener más información, vea [Orden de compilación de destinos](../msbuild/target-build-order.md) y [Cómo: Especificar qué destino utilizar primero al compilar](../msbuild/how-to-specify-which-target-to-build-first.md).<br /><br /> Un destino es un grupo de tareas. Para obtener más información, consulte [Destinos](../msbuild/msbuild-targets.md).|  
|/toolsversion:`version`|/tv:`version`|Especifica la versión del conjunto de herramientas que se va a usar para compilar el proyecto, como se muestra en el ejemplo siguiente: `/toolsversion:3.5`<br /><br /> Con este modificador, puede compilar un proyecto y especificar una versión diferente de la especificada en el [elemento Project (MSBuild)](../msbuild/project-element-msbuild.md). Para obtener más información, vea [Invalidar la configuración de ToolsVersion](../msbuild/overriding-toolsversion-settings.md).<br /><br /> En MSBuild 4.5, puede especificar los valores siguientes para `version`: 2.0, 3.5 y 4.0. Si especifica 4.0, la propiedad de compilación `VisualStudioVersion` especifica el subconjunto de herramientas que se va a usar. Para obtener más información, vea la sección de subconjuntos de herramientas de [Conjunto de herramientas (ToolsVersion)](../msbuild/msbuild-toolset-toolsversion.md).<br /><br /> Un conjunto de herramientas consta de tareas, destinos y herramientas que se utilizan para compilar una aplicación. Las herramientas incluyen compiladores como csc.exe y vbc.exe. Para obtener más información sobre los conjuntos de herramientas, vea [Conjunto de herramientas (ToolsVersion)](../msbuild/msbuild-toolset-toolsversion.md), [Configuraciones de conjuntos de herramientas estándar y personalizados](../msbuild/standard-and-custom-toolset-configurations.md) y [Compatibilidad con múltiples versiones (multi-targeting)](../msbuild/msbuild-multitargeting-overview.md). **Nota**: La versión del conjunto de herramientas no es la misma que la plataforma de destino, que es la versión de .NET Framework para la que se compila un proyecto. Para obtener más información, vea [Versión de .NET Framework de destino y plataforma de destino](../msbuild/msbuild-target-framework-and-target-platform.md).|  
|/validate:[`schema`]|/val[`schema`]|Valida el archivo de proyecto y, si la validación es correcta, lo compila.<br /><br /> Si no especifica `schema`, el proyecto se valida con el esquema predeterminado.<br /><br /> Si especifica `schema`, el proyecto se valida con el esquema especificado.<br /><br /> El valor siguiente muestra un ejemplo: `/validate:MyExtendedBuildSchema.xsd`|  
|/verbosity:`level`|/v:`level`|Especifica la cantidad de información que se va a mostrar en el registro de compilación. Cada registrador muestra eventos en función del nivel de detalle establecido para él.<br /><br /> Puede especificar los niveles de detalles siguientes: `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]` y `diag[nostic]`.<br /><br /> El valor siguiente muestra un ejemplo: `/verbosity:quiet`|  
|/version|/ver|Muestra solo la información de versión. El proyecto no se compila.|  
|@`file`||Inserta los modificadores de línea de comando de un archivo de texto. Si tiene varios archivos, deberá especificarlos por separado. Para obtener más información, vea [Archivos de respuesta](../msbuild/msbuild-response-files.md).|  
  
### <a name="switches-for-loggers"></a>Modificadores para registradores  
  
|Modificador|Forma abreviada|Descripción|  
|------------|----------------|-----------------|  
|/consoleloggerparameters:<br /><br /> `parameters`|/clp:`parameters`|Pasa los parámetros especificados al registrador de la consola, lo que muestra información de compilación en la ventana de la consola. Puede especificar los parámetros siguientes:<br /><br /> -   **PerformanceSummary**. Muestra el tiempo empleado en tareas, destinos y proyectos.<br />-   **Summary**. Muestra un resumen de errores y advertencias al final.<br />-   **NoSummary**. No muestra un resumen de errores y advertencias al final.<br />-   **ErrorsOnly**. Muestra solo errores.<br />-   **WarningsOnly**. Muestra solo advertencias.<br />-   **NoItemAndPropertyList**. No muestra la lista de elementos y propiedades que aparecerían al principio de cada compilación del proyecto si se estableciera el nivel de detalle en `diagnostic`.<br />-   **ShowCommandLine**. Muestra los mensajes de `TaskCommandLineEvent`.<br />-   **ShowTimestamp**. Muestra la marca de tiempo como un prefijo en los mensajes.<br />-   **ShowEventId**. Muestra el identificador de evento para los eventos iniciados, los eventos finalizados y los mensajes.<br />-   **ForceNoAlign**. No alinea el texto al tamaño del búfer de la consola.<br />-   **DisableConsoleColor**. Usa los colores de consola predeterminados para todos los mensajes de registro.<br />-   **DisableMPLogging**. Deshabilita el estilo de registro de resultados de multiprocesador al ejecutarse en el modo de no multiprocesador.<br />-   **EnableMPLogging**. Habilita el estilo de registro de multiprocesador aunque se ejecute en el modo de no multiprocesador. Este estilo de registro está habilitado de forma predeterminada.<br />-   **Verbosity**. Invalida el valor **/verbosity** para este registrador.<br /><br /> Use un punto y coma o una coma para separar varios parámetros, como se muestra en el ejemplo siguiente:<br /><br /> `/consoleloggerparameters:PerformanceSummary;NoSummary /verbosity:minimal`|  
|/distributedFileLogger|/dfl|Registra los resultados de la compilación de cada nodo de MSBuild en su propio archivo. La ubicación inicial de estos archivos es el directorio actual. De forma predeterminada, estos archivos se denominan "MSBuild*NodeId*.log". Puede usar el modificador **/fileLoggerParameters** para especificar la ubicación de estos archivos y otros parámetros de fileLogger.<br /><br /> Si asigna un nombre a un archivo de registro mediante el modificador **/fileLoggerParameters**, el registrador distribuido usará ese nombre como plantilla y anexará el identificador del nodo a dicho nombre al crear un archivo de registro para cada nodo.|  
|/distributedlogger:<br /><br /> `central logger`*<br /><br /> `forwarding logger`|/dl:`central logger`*`forwarding logger`|Registra eventos de MSBuild, adjuntando una instancia del registrador diferente a cada nodo. Para especificar varios registradores, hágalo por separado.<br /><br /> Use la sintaxis de registrador para especificar un registrador. Para la sintaxis de registrador, vea el modificador **/logger** a continuación.<br /><br /> En los ejemplos siguientes se muestra cómo utilizar este modificador:<br /><br /> `/dl:XMLLogger,MyLogger,Version=1.0.2,Culture=neutral`<br /><br /> `/dl:MyLogger,C:\My.dll*ForwardingLogger,C:\Logger.dll`|  
|/fileLogger<br /><br /> *[number]*|/fl[`number`]|Registra el resultado de la compilación en un archivo único en el directorio actual. Si no especifica `number`, el archivo de salida se denomina msbuild.log. Si especifica `number`, el archivo de salida se denomina msbuild`n`.log, donde n es `number`. `Number` puede ser un dígito comprendido entre 1 y 9.<br /><br /> Puede usar el modificador **/fileLoggerParameters** para especificar la ubicación del archivo y otros parámetros de fileLogger.|  
|/fileloggerparameters:[número]<br /><br /> `parameters`|/flp:[ `number`] `parameters`|Especifica parámetros adicionales del registrador de archivos y del registrador de archivos distribuido. La presencia de este modificador implica también la presencia del modificador /**filelogger[**`number`**]** correspondiente. `Number` puede ser un dígito comprendido entre 1 y 9.<br /><br /> Puede usar todos los parámetros que se enumeran para **/consoleloggerparameters**. También puede utilizar uno o varios de los parámetros siguientes:<br /><br /> -   **LogFile**. La ruta de acceso del archivo de registro donde se escribe el registro de compilación. El registrador de archivos distribuido usa esta ruta de acceso como prefijo en los nombres de los archivos de registro.<br />-   **Append**. Determina si el registro de compilación se anexará al archivo de registro o lo sobrescribirá. Cuando se establece el modificador, el registro de compilación se anexa al archivo de registro. Si el modificador no está presente, se sobrescribe el contenido de un archivo de registro existente.<br />     Si incluye el modificador append, el registro se anexará, independientemente de si está establecido en true o en false. Si no incluye el modificador append, el registro se sobrescribe.<br />     En este caso el archivo se sobrescribe: `msbuild myfile.proj /l:FileLogger,Microsoft.Build.Engine;logfile=MyLog.log`<br />     En este caso el archivo se anexa: `msbuild myfile.proj /l:FileLogger,Microsoft.Build.Engine;logfile=MyLog.log;append=true`<br />     En este caso el archivo se anexa: `msbuild myfile.proj /l:FileLogger,Microsoft.Build.Engine;logfile=MyLog.log;append=false`<br />-   **Encoding**. Especifica la codificación del archivo (por ejemplo, UTF-8, Unicode o ASCII).<br /><br /> El ejemplo siguiente genera archivos de registro independientes para advertencias y errores:<br /><br /> `/flp1:logfile=errors.txt;errorsonly /flp2:logfile=warnings.txt;warningsonly`<br /><br /> En los ejemplos siguientes se muestran otras posibilidades:<br /><br /> `/fileLoggerParameters:LogFile=MyLog.log;Append; Verbosity=diagnostic;Encoding=UTF-8`<br /><br /> `/flp:Summary;Verbosity=minimal;LogFile=msbuild.sum`<br /><br /> `/flp1:warningsonly;logfile=msbuild.wrn`<br /><br /> `/flp2:errorsonly;logfile=msbuild.err`|  
|/logger:<br /><br /> `logger`|/l:`logger`|Especifica el registrador que se debe utilizar para registrar los eventos de MSBuild. Para especificar varios registradores, hágalo por separado.<br /><br /> Utilice la sintaxis siguiente para `logger`: `[``LoggerClass``,]``LoggerAssembly``[;``LoggerParameters``]`<br /><br /> Utilice la sintaxis siguiente para `LoggerClass`: `[``PartialOrFullNamespace``.]``LoggerClassName`<br /><br /> No necesita especificar la clase de registrador si el ensamblado contiene exactamente un registrador.<br /><br /> Utilice la sintaxis siguiente para `LoggerAssembly`: `{``AssemblyName``[,``StrongName``] &#124;` `AssemblyFile``}`<br /><br /> Los parámetros del registrador son opcionales y se pasan al registrador tal como se han escrito.<br /><br /> En los ejemplos siguientes se usa el modificador **/logger**.<br /><br /> `/logger:XMLLogger,MyLogger,Version=1.0.2,Culture=neutral`<br /><br /> `/logger:XMLLogger,C:\Loggers\MyLogger.dll;OutputAsHTML`|  
|/noconsolelogger|/noconlog|Deshabilita el registrador de la consola predeterminado y no registra eventos en la consola.|  
  
## <a name="example"></a>Ejemplo  
 En el siguiente ejemplo se compila el destino `rebuild` del proyecto `MyProject.proj`.  
  
```  
MSBuild.exe MyProject.proj /t:rebuild  
```  
  
## <a name="example"></a>Ejemplo  
 Puede usar MSBuild.exe para realizar compilaciones más complejas. Por ejemplo, puede utilizarlo para compilar determinados destinos de proyectos específicos de una solución. En el ejemplo siguiente se recompila el proyecto `NotInSolutionFolder` y se "limpia" el proyecto `InSolutionFolder`, que está en la carpeta de soluciones `NewFolder`.  
  
```  
msbuild SlnFolders.sln /t:NotInSolutionfolder:Rebuild;NewFolder\InSolutionFolder:Clean  
```  
  
## <a name="see-also"></a>Vea también  
 [Referencia de MSBuild](../msbuild/msbuild-reference.md)   
 [Propiedades comunes de proyectos de MSBuild](../msbuild/common-msbuild-project-properties.md)



