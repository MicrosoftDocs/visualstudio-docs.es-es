---
title: Clase base ToolTaskExtension | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- MSBuild.ToolTask.ToolCommandFailed
dev_langs:
- VB
- CSharp
- C++
- jsharp
ms.assetid: 258ae433-f68a-49f1-b276-da20e3472e68
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: fa6ec44c857d8b8e229d8f34658e8a9d448fcb19
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2018
ms.locfileid: "49221291"
---
# <a name="tooltaskextension-base-class"></a>ToolTaskExtension (Clase base)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Muchas tareas heredan de la clase <xref:Microsoft.Build.Tasks.ToolTaskExtension>, que hereda de la clase <xref:Microsoft.Build.Utilities.ToolTask>, la cual a su vez hereda de la clase <xref:Microsoft.Build.Utilities.Task>. Esta cadena de herencia agrega varios parámetros a las tareas que derivan de ellos. Estos parámetros se muestran en este documento.  
  
## <a name="parameters"></a>Parámetros  
 En la siguiente tabla se describen los parámetros de las clases base.  
  
|Parámetro|Descripción|  
|---------------|-----------------|  
|<xref:Microsoft.Build.Utilities.Task.BuildEngine%2A>|Parámetro <xref:Microsoft.Build.Framework.IBuildEngine> opcional.<br /><br /> Especifica la interfaz del motor de compilación disponible para las tareas. El motor de compilación establece automáticamente este parámetro para permitir que las tareas vuelvan a llamarlo.|  
|<xref:Microsoft.Build.Utilities.Task.BuildEngine2%2A>|Parámetro <xref:Microsoft.Build.Framework.IBuildEngine2> opcional.<br /><br /> Especifica la interfaz del motor de compilación disponible para las tareas. El motor de compilación establece automáticamente este parámetro para permitir que las tareas vuelvan a llamarlo.<br /><br /> Esta es una propiedad que permite que los autores de las tareas que heredan de esta clase no tengan que convertir el valor de `IBuildEngine` a `IBuildEngine2`.|  
|<xref:Microsoft.Build.Utilities.Task.BuildEngine3%2A>|Parámetro <xref:Microsoft.Build.Framework.IBuildEngine3> opcional.<br /><br /> Especifica la interfaz del motor de compilación proporcionado por el host.|  
|<xref:Microsoft.Build.Utilities.ToolTask.EchoOff%2A>|Parámetro `bool` opcional.<br /><br /> Cuando se establece en `true`, esta tarea pasa **/Q** a la línea de comandos cmd.exe de modo que la línea de comandos no se copie en stdout.|  
|<xref:Microsoft.Build.Utilities.ToolTask.EnvironmentVariables%2A>|Parámetro de matriz `String` opcional.<br /><br /> Matriz de pares de variables de entorno, separados por signos igual. Estas variables se pasan al ejecutable generado y, además, pasan el bloque de entorno normal o lo invalidan de manera selectiva.|  
|<xref:Microsoft.Build.Utilities.ToolTask.ExitCode%2A>|Parámetro de solo lectura de salida `Int32` opcional.<br /><br /> Especifica el código de salida proporcionado por el comando ejecutado. Si la tarea registró errores pero el proceso tenía un código de salida de 0 (correcto), se establece en -1.|  
|<xref:Microsoft.Build.Utilities.Task.HostObject%2A>|Parámetro <xref:Microsoft.Build.Framework.ITaskHost> opcional.<br /><br /> Especifica la instancia del objeto host (puede ser null). El motor de compilación establece esta propiedad si el IDE del host tiene un objeto host asociado a esta tarea concreta.|  
|<xref:Microsoft.Build.Tasks.ToolTaskExtension.Log%2A>|Parámetro de solo lectura <xref:Microsoft.Build.Utilities.TaskLoggingHelper> opcional.<br /><br /> Obtiene una instancia de una clase <xref:Microsoft.Build.Tasks.TaskLoggingHelperExtension> que contiene métodos de registro de tareas.|  
|<xref:Microsoft.Build.Utilities.ToolTask.LogStandardErrorAsError%2A>|Parámetro `bool` opcional.<br /><br /> Si `true`, todos los mensajes recibidos en el flujo de error estándar se registran como errores.|  
|<xref:Microsoft.Build.Utilities.ToolTask.StandardErrorImportance%2A>|Parámetro `String` opcional.<br /><br /> Importancia con la que se va a registrar el texto de la secuencia de salida estándar.|  
|<xref:Microsoft.Build.Utilities.ToolTask.StandardOutputImportance%2A>|Parámetro `String` opcional.<br /><br /> Importancia con la que se va a registrar el texto de la secuencia de salida estándar.|  
|<xref:Microsoft.Build.Utilities.ToolTask.Timeout%2A>|Parámetro `Int32` opcional virtual.<br /><br /> Especifica el tiempo en milisegundos después del cual se termina la tarea ejecutable. El valor predeterminado es `Int.MaxValue`, que indica que no hay período de tiempo de espera. El tiempo de espera se expresa en milisegundos.|  
|<xref:Microsoft.Build.Utilities.ToolTask.ToolExe%2A>|Parámetro `string` opcional virtual.<br /><br /> Los proyectos pueden implementarlo para invalidar ToolName. Las tareas pueden invalidarlo para conservar ToolName.|  
|<xref:Microsoft.Build.Utilities.ToolTask.ToolPath%2A>|Parámetro `string` opcional.<br /><br /> Especifica la ubicación desde donde la tarea carga el archivo ejecutable subyacente. Si no se especifica este parámetro, la tarea usa la ruta de instalación del SDK que se corresponde con la versión del marco de trabajo que está ejecutando [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)].|  
|<xref:Microsoft.Build.Utilities.ToolTask.UseCommandProcessor%2A>|Parámetro `bool` opcional.<br /><br /> Cuando se establece en `true`, esta tarea crea un archivo por lotes para la línea de comandos y lo ejecuta mediante el procesador de comandos, en lugar de ejecutar el comando directamente.|  
|<xref:Microsoft.Build.Utilities.ToolTask.YieldDuringToolExecution%2A>|Parámetro `bool` opcional.<br /><br /> Cuando se establece en `true`, esta tarea produce el nodo cuando se ejecuta la tarea.|  
  
## <a name="see-also"></a>Vea también  
 [Referencia de tareas](../msbuild/msbuild-task-reference.md)   
 [Tareas](../msbuild/msbuild-tasks.md)



