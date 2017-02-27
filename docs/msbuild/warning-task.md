---
title: "Warning (Tarea) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "http://schemas.microsoft.com/developer/msbuild/2003#Warning"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "MSBuild, Warning (tarea)"
  - "Warning (tarea) [MSBuild]"
ms.assetid: 96ba5507-8b43-4f54-a1d7-9b15644dd56c
caps.latest.revision: 18
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 18
---
# Warning (Tarea)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Registra una advertencia durante la compilación basándose en una instrucción condicional evaluada.  
  
## Parámetros  
 En la siguiente tabla se describen los parámetros de la tarea `Warning`.  
  
|Parámetro|Descripción|  
|---------------|-----------------|  
|`Code`|Parámetro `String` opcional.<br /><br /> Código que se va a asociar a la advertencia.|  
|`File`|Parámetro `String` opcional.<br /><br /> Especifica el archivo correspondiente, si lo hay.  Si no se proporciona ningún archivo, se usará el archivo que contiene la tarea Warning.|  
|`HelpKeyword`|Parámetro `String` opcional.<br /><br /> Palabra clave de Ayuda que se va a asociar a la advertencia.|  
|`Text`|Parámetro `String` opcional.<br /><br /> Texto de advertencia que [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] registra si el parámetro `Condition` se evalúa como `true`.|  
  
## Comentarios  
 La tarea `Warning` permite a los proyectos de [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] comprobar la presencia de una configuración o propiedad necesaria antes de continuar con el siguiente paso del proceso de compilación.  
  
 Si el parámetro `Condition` de la tarea `Warning` se evalúa como `true`, se registra el valor del parámetro `Text` y la compilación sigue ejecutándose.  Si no existe un parámetro `Condition`, se anota el texto de la advertencia.  Para obtener más información sobre el registro, vea [Obtener registros de compilación](../msbuild/obtaining-build-logs-with-msbuild.md).  
  
 Además de los parámetros mencionados anteriormente, esta tarea hereda los parámetros de la clase <xref:Microsoft.Build.Tasks.TaskExtension>, que hereda de la clase <xref:Microsoft.Build.Utilities.Task>.  Para obtener una lista de estos parámetros adicionales y sus descripciones, vea [TaskExtension \(Clase base\)](../msbuild/taskextension-base-class.md).  
  
## Ejemplo  
 En el siguiente ejemplo de código se comprueban las propiedades establecidas en la línea de comandos.  Si no se han establecido propiedades, el proyecto provoca un evento de advertencia y registra el valor del parámetro `Text` de la tarea `Warning`.  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <Target Name="ValidateCommandLine">  
        <Warning  
            Text=" The 0 property was not set on the command line."  
            Condition="'$(0)' == ''" />  
        <Warning  
            Text=" The FREEBUILD property was not set on the command line."  
            Condition="'$(FREEBUILD)' == ''" />  
    </Target>  
    ...  
</Project>  
```  
  
## Vea también  
 [Obtener registros de compilación](../msbuild/obtaining-build-logs-with-msbuild.md)   
 [Referencia de esquemas del archivo de proyecto](../msbuild/msbuild-project-file-schema-reference.md)