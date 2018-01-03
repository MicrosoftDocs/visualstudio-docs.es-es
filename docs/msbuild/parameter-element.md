---
title: Elemento Parameter | Microsoft Docs
ms.custom: 
ms.date: 03/13/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- jsharp
- xml
helpviewer_keywords:
- Parameter element [MSBuild]
- <Parameter> element [MSBuild]
ms.assetid: b273afff-b500-4e97-8cfd-31f39fa64a51
caps.latest.revision: "7"
author: kempb
ms.author: kempb
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 359f0f58a1c3b813216e4a760a1c750710fb3416
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="parameter-element"></a>Parameter (Elemento)
Contiene información sobre un parámetro específico para una tarea que se genera mediante `UsingTask``TaskFactory`.  El nombre del elemento es el nombre del parámetro.  Para más información, consulte [Elemento UsingTask (MSBuild)](../msbuild/usingtask-element-msbuild.md).  

 \<Project>  
 \<UsingTask>  
 \<ParameterGroup>  
 \<Parameter>  

## <a name="syntax"></a>Sintaxis  

```  
<ParameterGroup ParameterType="SystemType"  
    Output="true/false"  
    Required="true/false" />  
```  

## <a name="attributes-and-elements"></a>Atributos y elementos  
 En las siguientes secciones se describen los atributos, los elementos secundarios y los elementos primarios.  

### <a name="attributes"></a>Atributos  

|Atributo|Description|  
|---------------|-----------------|  
|`ParameterType`|Atributo opcional.<br /><br /> El tipo .NET del parámetro, por ejemplo, "System.String".|  
|`Output`|Atributo Boolean opcional.<br /><br /> Si es `true`, este parámetro es un parámetro de salida para la tarea. De forma predeterminada, el valor es `false`.|  
|`Required`|Atributo Boolean opcional.<br /><br /> Si es `true`, este parámetro es un parámetro necesario para la tarea. De forma predeterminada, el valor es `false`.|  

### <a name="child-elements"></a>Elementos secundarios  
 Ninguno.  

### <a name="parent-elements"></a>Elementos primarios  

|Elemento|Description|  
|-------------|-----------------|  
|[ParameterGroup](../msbuild/parametergroup-element.md)|Contiene una lista opcional de parámetros que estarán presentes en la tarea generada por `UsingTask``TaskFactory`.|  

## <a name="example"></a>Ejemplo  
 El ejemplo siguiente muestra cómo usar el elemento `Parameter`.  

```xml  
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

## <a name="see-also"></a>Vea también  
 [Tareas](../msbuild/msbuild-tasks.md)   
 [Referencia de tareas](../msbuild/msbuild-task-reference.md)   
 [Referencia de esquemas de archivo del proyecto](../msbuild/msbuild-project-file-schema-reference.md)
