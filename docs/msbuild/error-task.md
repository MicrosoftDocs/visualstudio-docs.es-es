---
title: "Error (Tarea) | Microsoft Docs"
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
  - "http://schemas.microsoft.com/developer/msbuild/2003#Error"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "Error (tarea) [MSBuild]"
  - "MSBuild, Error (tarea)"
ms.assetid: e96a90ee-a8ae-4e5b-8ef2-b5cf5fedd8b2
caps.latest.revision: 20
caps.handback.revision: 20
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Error (Tarea)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Detiene una compilación y registra un error basándose en una instrucción condicional evaluada.  
  
## Parámetros  
 En la siguiente tabla se describen los parámetros de la tarea `Error`.  
  
|Parámetro|Descripción|  
|---------------|-----------------|  
|`Code`|Parámetro `String` opcional.<br /><br /> Código de error que se va a asociar al error.|  
|`File`|Parámetro `String` opcional.<br /><br /> El nombre del archivo que contiene el error.  Si no se proporciona ningún nombre de archivo, se usará el archivo que contiene la tarea Error.|  
|`HelpKeyword`|Parámetro `String` opcional.<br /><br /> Palabra clave de Ayuda que se va a asociar al error.|  
|`Text`|Parámetro `String` opcional.<br /><br /> Texto de error que [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] registra si el parámetro `Condition` se evalúa como `true`.|  
  
## Comentarios  
 La tarea `Error` permite que los proyectos de [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] envíen un texto de error a los registradores y detengan la ejecución de la compilación.  
  
 Si el parámetro `Condition` se evalúa como `true`, se detiene la compilación y se registra un error.  Si no existe un parámetro `Condition`, se registra el error y se detiene la ejecución de la compilación.  Para obtener más información sobre el registro, vea [Obtener registros de compilación](../msbuild/obtaining-build-logs-with-msbuild.md).  
  
 Además de los parámetros mencionados anteriormente, esta tarea hereda los parámetros de la clase <xref:Microsoft.Build.Tasks.TaskExtension>, que hereda de la clase <xref:Microsoft.Build.Utilities.Task>.  Para obtener una lista de estos parámetros adicionales y sus descripciones, vea [TaskExtension \(Clase base\)](../msbuild/taskextension-base-class.md).  
  
## Ejemplo  
 En el ejemplo de código siguiente se comprueba que se han establecido todas las propiedades necesarias.  Si no están establecidas, el proyecto produce un evento de error y registra el valor del parámetro `Text` de la tarea `Error`.  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <Target Name="ValidateCommandLine">  
        <Error  
            Text=" The 0 property must be set on the command line."  
            Condition="'$(0)' == ''" />  
        <Error  
            Text="The FREEBUILD property must be set on the command line."  
            Condition="'$(FREEBUILD)' == ''" />  
    </Target>  
    ...  
</Project>  
```  
  
## Vea también  
 [Referencia de tareas](../msbuild/msbuild-task-reference.md)   
 [Obtener registros de compilación](../msbuild/obtaining-build-logs-with-msbuild.md)