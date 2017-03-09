---
title: "LC (Tarea) | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "http://schemas.microsoft.com/developer/msbuild/2003#LC"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "LC (tarea) [MSBuild]"
  - "MSBuild, LC (tarea)"
ms.assetid: d5a53472-6f2a-42b8-a6db-593ca99c9790
caps.latest.revision: 15
caps.handback.revision: 15
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# LC (Tarea)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Ajusta LC.exe que genera un archivo .license de un archivo .licx.  Para obtener más información sobre LC.exe, vea [Lc.exe \(License Compiler\)](../Topic/Lc.exe%20\(License%20Compiler\).md).  
  
## Parámetros  
 En la siguiente tabla se describen los parámetros de la tarea `LC`.  
  
|Parámetro|Descripción|  
|---------------|-----------------|  
|`LicenseTarget`|Parámetro <xref:Microsoft.Build.Framework.ITaskItem> requerido.<br /><br /> Especifica el archivo ejecutable para el que se generan los archivos .licenses.|  
|`NoLogo`|Parámetro `Boolean` opcional.<br /><br /> Suprime la presentación de la portada de inicio de Microsoft.|  
|`OutputDirectory`|Parámetro `String` opcional.<br /><br /> Especifica el directorio en el que se colocan los archivos .licenses de salida.|  
|`OutputLicense`|Parámetro de salida <xref:Microsoft.Build.Framework.ITaskItem> opcional.<br /><br /> Especifica el nombre de los archivos .license.  Si no especifica un nombre, se utiliza el nombre del archivo .licx y el archivo .licenses se coloca en el directorio que contiene el archivo .licx.|  
|`ReferencedAssemblies`|Parámetro <xref:Microsoft.Build.Framework.ITaskItem>`[]` opcional.<br /><br /> Especifica los componentes a los que se hace referencia que se cargarán al generar el archivo .license.|  
|`SdkToolsPath`|Parámetro `String` opcional.<br /><br /> Especifica la ruta de acceso a las herramientas del SDK, tales como resgen.exe.|  
|`Sources`|Parámetro <xref:Microsoft.Build.Framework.ITaskItem>`[]` requerido.<br /><br /> Especifica los elementos que contienen los componentes con licencia que se incluirán en el archivo .licenses.  Para obtener más información, consulte la documentación sobre el modificador `/complist` en [Lc.exe \(License Compiler\)](../Topic/Lc.exe%20\(License%20Compiler\).md).|  
  
 Además de los parámetros mencionados anteriormente, esta tarea hereda los parámetros de la clase <xref:Microsoft.Build.Tasks.ToolTaskExtension>, que hereda de la clase <xref:Microsoft.Build.Utilities.ToolTask>.  Para obtener una lista de estos parámetros adicionales y sus descripciones, vea [ToolTaskExtension \(Clase base\)](../msbuild/tooltaskextension-base-class.md).  
  
## Ejemplo  
 En el siguiente ejemplo se utiliza la tarea `LC` para compilar las licencias.  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
<!-- Item declarations, etc -->  
  
    <Target Name="CompileLicenses">  
        <LC  
            Sources="@(LicxFile)"  
            LicenseTarget="$(TargetFileName)"  
            OutputDirectory="$(IntermediateOutputPath)"  
            OutputLicenses="$(IntermediateOutputPath)$(TargetFileName).licenses"  
            ReferencedAssemblies="@(ReferencePath);@(ReferenceDependencyPaths)">  
  
            <Output  
                TaskParameter="OutputLicenses"  
                ItemName="CompiledLicenseFile"/>  
        </LC>  
    </Target>  
</Project>  
```  
  
## Vea también  
 [Tareas](../msbuild/msbuild-tasks.md)   
 [Referencia de tareas](../msbuild/msbuild-task-reference.md)