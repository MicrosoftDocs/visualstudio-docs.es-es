---
title: "Parameter (Elemento) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "<Parameter> (elemento) [MSBuild]"
  - "Parameter (elemento) [MSBuild]"
ms.assetid: b273afff-b500-4e97-8cfd-31f39fa64a51
caps.latest.revision: 7
caps.handback.revision: 7
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Parameter (Elemento)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Contiene información sobre un parámetro específico de una tarea generada por `UsingTask` `TaskFactory`. El nombre del elemento es el nombre del parámetro. Para obtener más información, vea [Elemento UsingTask \(MSBuild\)](../msbuild/usingtask-element-msbuild.md).  
  
## Sintaxis  
  
```  
<ParameterGroup ParameterType="SystemType"  
    Output="true/false"  
    Required="true/false" />  
```  
  
## Atributos y elementos  
 En las próximas secciones se describen los atributos, los elementos secundarios y los elementos primarios.  
  
### Atributos  
  
|Atributo|Descripción|  
|--------------|-----------------|  
|`ParameterType`|Atributo opcional.<br /><br /> El tipo .NET del parámetro, por ejemplo, "System.String".|  
|`Output`|Atributo booleano opcional.<br /><br /> Si es `true`, este parámetro es un parámetro de salida de la tarea.  De forma predeterminada, el valor es `false`.|  
|`Required`|Atributo booleano opcional.<br /><br /> Si es `true`, este parámetro es un parámetro necesario para la tarea.  De forma predeterminada, el valor es `false`.|  
  
### Elementos secundarios  
 Ninguno.  
  
### Elementos primarios  
  
|Elemento|Descripción|  
|--------------|-----------------|  
|[ParameterGroup](../msbuild/parametergroup-element.md)|Contiene una lista opcional de parámetros que estarán presentes en la tarea generada por `UsingTask` `TaskFactory`.|  
  
## Ejemplo  
 En el siguiente ejemplo se muestra cómo se utiliza el elemento `Parameter`.  
  
```  
<UsingTask TaskName="MyTask" AssemblyName="My.Assembly" TaskFactory="MyTaskFactory">  
       <ParameterGroup>  
              <Parameter1 ParameterType="System.String" Required="False" Output="False"/>  
              <Parameter2 ParameterType="System.Int" Required="True" Output="False"/>  
             ...  
</ParameterGroup>  
       <TaskBody Evaluate="true">  
      ... Task factory-specific data ...  
       </TaskBody>  
</UsingTask>  
```  
  
## Vea también  
 [Tareas](../msbuild/msbuild-tasks.md)   
 [Referencia de tareas](../msbuild/msbuild-task-reference.md)   
 [Referencia de esquemas del archivo de proyecto](../msbuild/msbuild-project-file-schema-reference.md)