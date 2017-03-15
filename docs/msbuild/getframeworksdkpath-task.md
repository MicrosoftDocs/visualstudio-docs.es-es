---
title: "GetFrameworkSdkPath (Tarea) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "http://schemas.microsoft.com/developer/msbuild/2003#GetFrameworkSdkPath"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "GetFrameworkSdkPath (tarea) [MSBuild]"
  - "MSBuild, GetFrameworkSdkPath (tarea)"
ms.assetid: 2ef82b98-02b6-40cf-a9b5-f0e882fb5064
caps.latest.revision: 10
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 10
---
# GetFrameworkSdkPath (Tarea)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Recupera la ruta de acceso a [!INCLUDE[winsdklong](../deployment/includes/winsdklong_md.md)].  
  
## Parámetros de la tarea  
 En la siguiente tabla se describen los parámetros de la tarea `GetFrameworkSdkPath`.  
  
|Parámetro|Descripción|  
|---------------|-----------------|  
|`FrameworkSdkVersion20Path`|Parámetro de salida `String` opcional de solo lectura.<br /><br /> Devuelve la ruta de acceso al SDK de .NET versión 2.0, si existe.  En caso contrario, devuelve `String.Empty`.|  
|`FrameworkSdkVersion35Path`|Parámetro de salida `String` opcional de solo lectura.<br /><br /> Devuelve la ruta de acceso al SDK de .NET versión 3.5, si existe.  En caso contrario, devuelve `String.Empty`.|  
|`FrameworkSdkVersion40Path`|Parámetro de salida `String` opcional de solo lectura.<br /><br /> Devuelve la ruta de acceso al SDK de .NET versión 4.0, si existe.  En caso contrario, devuelve `String.Empty`.|  
|`Path`|Parámetro de salida `String` opcional.<br /><br /> Contiene la ruta de acceso al último SDK .NET, si existe alguna versión.  En caso contrario, devuelve `String.Empty`.|  
  
## Comentarios  
 Además de los parámetros mencionados anteriormente, esta tarea hereda los parámetros de la clase <xref:Microsoft.Build.Tasks.TaskExtension>, que hereda de la clase <xref:Microsoft.Build.Utilities.Task>.  Para obtener una lista de estos parámetros adicionales y sus descripciones, vea [TaskExtension \(Clase base\)](../msbuild/taskextension-base-class.md).  
  
## Ejemplo  
 En el ejemplo siguiente se utiliza la tarea `GetFrameworkSdkPath` para almacenar la ruta de acceso a [!INCLUDE[winsdkshort](../debugger/debug-interface-access/includes/winsdkshort_md.md)] en la propiedad `SdkPath`.  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <Target Name="GetPath">  
        <GetFrameworkSdkPath>  
            <Output  
                TaskParameter="Path"  
                PropertyName="SdkPath" />  
        </GetFrameworkSdkPath>  
        <Message Text="$(SdkPath)"/>  
    </Target>  
</Project>  
```  
  
## Vea también  
 [Tareas](../msbuild/msbuild-tasks.md)   
 [Referencia de tareas](../msbuild/msbuild-task-reference.md)