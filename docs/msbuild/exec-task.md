---
title: "Exec (Tarea) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "http://schemas.microsoft.com/developer/msbuild/2003#Exec"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "Exec (tarea) [MSBuild]"
  - "MSBuild, Exec (tarea)"
ms.assetid: c9b7525a-b1c9-40fc-8bce-77a5b8f960d8
caps.latest.revision: 20
caps.handback.revision: 20
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Exec (Tarea)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Ejecuta el programa o comando especificado mediante los argumentos especificados.  
  
## Parámetros  
 En la siguiente tabla se describen los parámetros de la tarea `Exec`.  
  
|Parámetro|Descripción|  
|---------------|-----------------|  
|`Command`|Parámetro `String` requerido.<br /><br /> El comando o comandos que se va a ejecutar.  Éstos pueden ser comandos del sistema, como attrib, o una aplicación ejecutable, como program.exe, runprogram.bat o setup.msi.<br /><br /> Este parámetro contiene varias líneas de comandos.  Alternativamente, puede colocar varios comandos en un archivo por lotes y ejecutarlo utilizando este parámetro.|  
|`CustomErrorRegularExpression`|Parámetro `String` opcional.<br /><br /> Especifica una expresión regular que se utiliza para identificar líneas de error en los resultados de la herramienta.  Esto resulta útil para las herramientas que generan resultados con un formato poco común.|  
|`CustomWarningRegularExpression`|Parámetro `String` opcional.<br /><br /> Especifica una expresión regular que se utiliza para identificar líneas de advertencia en los resultados de la herramienta.  Esto resulta útil para las herramientas que generan resultados con un formato poco común.|  
|`ExitCode`|Parámetro de salida de sólo lectura `Int32` opcional.<br /><br /> Especifica el código de salida proporcionado por el comando ejecutado.|  
|`IgnoreExitCode`|Parámetro `Boolean` opcional.<br /><br /> Si es `true`, la tarea omite el código de salida proporcionado por el comando ejecutado.  De lo contrario, la tarea devuelve `false` si el comando ejecutado devuelve un código de salida distinto de cero.|  
|`IgnoreStandardErrorWarningFormat`|Parámetro `Boolean` opcional.<br /><br /> Si es `false`, selecciona las líneas de los resultados que coincidan con el formato estándar de alerta\/advertencia, y los registra como errores\/advertencias.  Si es `true`, deshabilite este comportamiento.|  
|`Outputs`|Parámetro de salida <xref:Microsoft.Build.Framework.ITaskItem>`[]` opcional.<br /><br /> Contiene los elementos de salida de la tarea.  La tarea `Exec` no los establece por sí misma.  En cambio, puede proporcionarlos como si los estableciera, para que se puedan utilizar después en el proyecto.|  
|`StdErrEncoding`|Parámetro de salida `String` opcional.<br /><br /> Especifica la codificación del flujo de error estándar de la tarea capturada.  El valor predeterminado es la codificación generada de la consola actual.|  
|`StdOutEncoding`|Parámetro de salida `String` opcional.<br /><br /> Especifica la codificación del flujo de salida estándar de la tarea capturada.  El valor predeterminado es la codificación generada de la consola actual.|  
|`WorkingDirectory`|Parámetro `String` opcional.<br /><br /> Especifica el directorio en el que el comando se ejecutará.|  
  
## Comentarios  
 Esta tarea es útil cuando una tarea de [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] específica para el trabajo que desea realizar no está disponible.  Sin embargo, la tarea `Exec`, a diferencia de una tarea más específica, no puede reunir la salida de la herramienta o comando que ejecuta.  
  
 La tarea `Exec` llama al archivo cmd.exe en vez de invocar directamente un proceso.  
  
 Además de los parámetros mencionados en este documento, esta tarea hereda los parámetros de la clase <xref:Microsoft.Build.Tasks.ToolTaskExtension>, que hereda de la clase <xref:Microsoft.Build.Utilities.ToolTask>.  Para obtener una lista de estos parámetros adicionales y sus descripciones, vea [ToolTaskExtension \(Clase base\)](../msbuild/tooltaskextension-base-class.md).  
  
## Ejemplo  
 El ejemplo siguiente utiliza la tarea `Exec` para ejecutar un comando.  
  
```  
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
  
## Vea también  
 [Tareas](../msbuild/msbuild-tasks.md)   
 [Referencia de tareas](../msbuild/msbuild-task-reference.md)