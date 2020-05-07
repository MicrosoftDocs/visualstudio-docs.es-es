---
author: ghogen
ms.author: ghogen
ms.topic: include
ms.date: 4/23/2020
ms.openlocfilehash: 40108f56ee9d64688fc665fdef0e0ab731bddfff
ms.sourcegitcommit: 596f92fcc84e6f4494178863a66aed85afe0bb08
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/28/2020
ms.locfileid: "82204503"
---
### <a name="tooltaskextension-parameters"></a>Parámetros de ToolTaskExtension

Esta tarea hereda de la clase <xref:Microsoft.Build.Tasks.ToolTaskExtension>, que hereda de la clase <xref:Microsoft.Build.Utilities.ToolTask>, la cual, a su vez, hereda de la clase <xref:Microsoft.Build.Utilities.Task>. Esta cadena de herencia agrega varios parámetros a las tareas que derivan de ellos.

En la siguiente tabla se describen los parámetros de las clases base:

| Parámetro | Descripción |
| - | - |
| <xref:Microsoft.Build.Utilities.ToolTask.EchoOff%2A> | Parámetro `bool` opcional.<br /><br /> Cuando se establece en `true`, esta tarea pasa **/Q** a la línea de comandos *cmd.exe* de modo que la línea de comandos no se copia en stdout. |
| <xref:Microsoft.Build.Utilities.ToolTask.EnvironmentVariables%2A> | Parámetro de matriz `String` opcional.<br /><br /> Matriz de pares de variables de entorno, separados por signos igual. Estas variables se pasan al ejecutable generado y, además, pasan el bloque de entorno normal o lo invalidan de manera selectiva. |
| <xref:Microsoft.Build.Utilities.ToolTask.ExitCode%2A> | Parámetro de solo lectura de salida `Int32` opcional.<br /><br /> Especifica el código de salida proporcionado por el comando ejecutado. Si la tarea registró errores pero el proceso tenía un código de salida de 0 (correcto), se establece en -1. |
| <xref:Microsoft.Build.Utilities.ToolTask.LogStandardErrorAsError%2A> | Parámetro `bool` opcional.<br /><br /> Si `true`, todos los mensajes recibidos en el flujo de error estándar se registran como errores. |
| <xref:Microsoft.Build.Utilities.ToolTask.LogStandardErrorAsError%2A> | Parámetro `bool` opcional.<br /><br /> Si `true`, todos los mensajes recibidos en el flujo de error estándar se registran como errores. |
| <xref:Microsoft.Build.Utilities.ToolTask.StandardErrorImportance%2A> | Parámetro `String` opcional.<br /><br /> Importancia con la que se va a registrar el texto de la secuencia de salida estándar. |
| <xref:Microsoft.Build.Utilities.ToolTask.StandardOutputImportance%2A> | Parámetro `String` opcional.<br /><br /> Importancia con la que se va a registrar el texto de la secuencia de salida estándar. |
| <xref:Microsoft.Build.Utilities.ToolTask.Timeout%2A> | Parámetro `Int32` opcional.<br /><br /> Especifica el tiempo en milisegundos después del cual se termina la tarea ejecutable. El valor predeterminado es `Int.MaxValue`, que indica que no hay período de tiempo de espera. Tiempo de espera en milisegundos. |
| <xref:Microsoft.Build.Utilities.ToolTask.ToolExe%2A> | Parámetro `string` opcional.<br /><br /> Los proyectos pueden implementarlo para invalidar ToolName. Las tareas pueden invalidarlo para conservar ToolName. |
| <xref:Microsoft.Build.Utilities.ToolTask.ToolPath%2A> | Parámetro `string` opcional.<br /><br /> Especifica la ubicación desde donde la tarea carga el archivo ejecutable subyacente. Si no se especifica este parámetro, la tarea usa la ruta de instalación del SDK que se corresponde con la versión del marco de trabajo que está ejecutando MSBuild. |
| <xref:Microsoft.Build.Utilities.ToolTask.UseCommandProcessor%2A> | Parámetro `bool` opcional.<br /><br /> Cuando se establece en `true`, esta tarea crea un archivo por lotes para la línea de comandos y lo ejecuta mediante el procesador de comandos, en lugar de ejecutar el comando directamente. |
| <xref:Microsoft.Build.Utilities.ToolTask.YieldDuringToolExecution%2A> | Parámetro `bool` opcional.<br /><br /> Cuando se establece en `true`, esta tarea produce el nodo cuando se ejecuta la tarea. |
