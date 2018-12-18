---
title: Exec (Tarea) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: msbuild
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#Exec
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- Exec task [MSBuild]
- MSBuild, Exec task
ms.assetid: c9b7525a-b1c9-40fc-8bce-77a5b8f960d8
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: bbefb90cad3b2aa3e6e7b0870548d44567ea8914
ms.sourcegitcommit: 56f3c31f1a06f6a6d2a8793b1abfa60cdf482497
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/05/2018
ms.locfileid: "48817326"
---
# <a name="exec-task"></a>Exec (tarea)
Ejecuta el programa o comando especificado mediante los argumentos especificados.  
  
## <a name="parameters"></a>Parámetros  
 En la tabla siguiente se describen los parámetros de la tarea `Exec`.  
  
|Parámetro|Descripción|  
|---------------|-----------------|  
|`Command`|Parámetro `String` requerido.<br /><br /> Comandos que se van a ejecutar. Pueden ser comandos del sistema, como attrib, o un ejecutable, como *program.exe*, *runprogram.bat* o *setup.msi*.<br /><br /> Este parámetro puede contener varias líneas de comandos. Alternativamente, puede colocar varios comandos en un archivo por lotes y ejecutarlo utilizando este parámetro.|  
|`ConsoleOutput`|Parámetro de salida <xref:Microsoft.Build.Framework.ITaskItem>`[]` opcional.<br /><br /> La salida de cada elemento es una línea de la salida estándar o de la secuencia de errores estándar que emite la herramienta. Solo se captura si `ConsoleToMsBuild` está establecido en `true`.|
|`ConsoleToMsBuild`|Parámetro `Boolean` opcional.<br /><br /> Si se establece en `true`, la tarea capturará el error estándar y la salida estándar de la herramienta y hará que estén disponibles en el parámetro de salida `ConsoleOutput`.<br /><br />Predeterminado: `false`.|  
|`CustomErrorRegularExpression`|Parámetro `String` opcional.<br /><br /> Especifica una expresión regular que se utiliza para identificar líneas de error en los resultados de la herramienta. Esto resulta útil para las herramientas que generan resultados con un formato poco común.<br /><br />Predeterminado: `null` (sin procesamiento personalizado).|  
|`CustomWarningRegularExpression`|Parámetro `String` opcional.<br /><br /> Especifica una expresión regular que se utiliza para identificar líneas de advertencia en los resultados de la herramienta. Esto resulta útil para las herramientas que generan resultados con un formato poco común.<br /><br />Predeterminado: `null` (sin procesamiento personalizado).|  
|`EchoOff`|Parámetro `Boolean` opcional.<br /><br /> Si se establece en `true`, la tarea no emitirá el formulario expandido de `Command` al registro de MSBuild.<br /><br />Predeterminado: `false`.|
|`ExitCode`|Parámetro de solo lectura de salida `Int32` opcional.<br /><br /> Especifica el código de salida proporcionado por el comando ejecutado.|  
|`IgnoreExitCode`|Parámetro `Boolean` opcional.<br /><br /> Si es `true`, la tarea omite el código de salida proporcionado por el comando ejecutado. De lo contrario, la tarea devuelve `false` si el comando ejecutado devuelve un código de salida distinto de cero.<br /><br />Predeterminado: `false`.|  
|`IgnoreStandardErrorWarningFormat`|Parámetro `Boolean` opcional.<br /><br /> Si es `false`, selecciona las líneas de los resultados que coincidan con el formato estándar de alerta/advertencia, y los registra como errores/advertencias. Si es `true`, se deshabilita este comportamiento.<br /><br />Predeterminado: `false`.|  
|`Outputs`|Parámetro de salida <xref:Microsoft.Build.Framework.ITaskItem>`[]` opcional.<br /><br /> Contiene los elementos de salida de la tarea. La tarea `Exec` no los establece por sí misma. En cambio, puede proporcionarlos como si los estableciera, para que se puedan utilizar después en el proyecto.|  
|`StdErrEncoding`|Parámetro de salida `String` opcional.<br /><br /> Especifica la codificación del flujo de error estándar de la tarea capturada. El valor predeterminado es la codificación generada de la consola actual.|  
|`StdOutEncoding`|Parámetro de salida `String` opcional.<br /><br /> Especifica la codificación del flujo de salida estándar de la tarea capturada. El valor predeterminado es la codificación generada de la consola actual.|  
|`WorkingDirectory`|Parámetro `String` opcional.<br /><br /> Especifica el directorio en el que se ejecutará el comando.<br /><br />Predeterminado: directorio de trabajo actual del proyecto.|  
  
## <a name="remarks"></a>Comentarios  
 Esta tarea es útil cuando una tarea de [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] específica para el trabajo que desea realizar no está disponible. Sin embargo, la tarea `Exec`, a diferencia de una tarea más específica, no puede realizar un procesamiento adicional ni operaciones condicionales en función del resultado de la herramienta o el comando que se ejecuta.
  
 La tarea `Exec` llama a *cmd.exe* en vez de invocar directamente a un proceso.  
  
 Además de los parámetros mencionados en este documento, esta tarea hereda los parámetros de la clase <xref:Microsoft.Build.Tasks.ToolTaskExtension>, que a su vez hereda de la clase <xref:Microsoft.Build.Utilities.ToolTask>. Para obtener una lista de estos parámetros adicionales y sus descripciones, consulte [ToolTaskExtension (Clase base)](../msbuild/tooltaskextension-base-class.md).  
  
## <a name="example"></a>Ejemplo  
 El ejemplo siguiente utiliza la tarea `Exec` para ejecutar un comando.  
  
```xml  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <ItemGroup>  
        <Binaries Include="*.dll;*.exe"/>  
    </ItemGroup>  
  
    <Target Name="SetACL">  
        <!-- set security on binaries-->  
        <Exec Command="echo y| cacls %(Binaries.Identity) /G everyone:R"/>  
    </Target>  
</Project>  
```

## <a name="see-also"></a>Vea también  
 [Tareas](../msbuild/msbuild-tasks.md)   
 [Referencia de tareas](../msbuild/msbuild-task-reference.md)
