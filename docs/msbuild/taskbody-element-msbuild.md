---
title: "TaskBody (Elemento) (MSBuild) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
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
  - "<TaskBody> (elemento) [MSBuild]"
  - "TaskBody (elemento) [MSBuild]"
ms.assetid: 49d8741b-f1ea-4470-94fd-a1ac27341a6a
caps.latest.revision: 7
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 7
---
# TaskBody (Elemento) (MSBuild)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Contiene los datos que se pasan a `UsingTask` `TaskFactory`. Para obtener más información, consulte [Elemento UsingTask \(MSBuild\)](../msbuild/usingtask-element-msbuild.md).  
  
## Sintaxis  
  
```  
<TaskBody Evaluate="true/false" />  
```  
  
## Atributos y elementos  
 En las próximas secciones se describen los atributos, los elementos secundarios y los elementos primarios.  
  
### Atributos  
  
|Atributo|Descripción|  
|--------------|-----------------|  
|`Evaluate`|Atributo booleano opcional.<br /><br /> Si es `true`, MSBuild evalúa los elementos interiores y expande los elementos y propiedades antes de pasar la información a `TaskFactory` cuando se crea una instancia de la tarea.|  
  
### Elementos secundarios  
  
|Elemento|Descripción|  
|--------------|-----------------|  
|Datos|El texto entre las etiquetas `TaskBody` se envía literalmente a `TaskFactory`.|  
  
### Elementos primarios  
  
|Elemento|Descripción|  
|--------------|-----------------|  
|[UsingTask](../msbuild/usingtask-element-msbuild.md)|Ofrece una manera de registrar las tareas en [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)].  Puede haber cero o más elementos `UsingTask` en un proyecto.|  
  
## Ejemplo  
 En el ejemplo siguiente se muestra cómo utilizar el elemento `TaskBody` con un atributo `Evaluate`.  
  
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