---
title: ParameterGroup (Elemento) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- <ParameterGroup> element [MSBuild]
- ParameterGroup element [MSBuild]
ms.assetid: c3275e69-a427-4889-bc1d-51bff2c285fa
caps.latest.revision: 6
author: kempb
ms.author: kempb
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Human Translation
ms.sourcegitcommit: 79460291e91f0659df0a4241e17616e55187a0e2
ms.openlocfilehash: 387639a0432a7654163e5c476af251ccf8721b07
ms.lasthandoff: 02/22/2017

---
# <a name="parametergroup-element"></a>ParameterGroup (Elemento)
Contiene una lista opcional de parámetros que estarán presentes en la tarea generada por `UsingTask``TaskFactory`. Para obtener más información, consulte [Elemento UsingTask (MSBuild)](../msbuild/usingtask-element-msbuild.md).  
  
 \<Project>  
 \<UsingTask>  
 \<ParameterGroup>  
  
## <a name="syntax"></a>Sintaxis  
  
```xml  
<ParameterGroup />  
```  
  
## <a name="attributes-and-elements"></a>Atributos y elementos  
 En las siguientes secciones se describen los atributos, los elementos secundarios y los elementos primarios.  
  
### <a name="attributes"></a>Atributos  
 Ninguno.  
  
### <a name="child-elements"></a>Elementos secundarios  
  
|Elemento|Descripción|  
|-------------|-----------------|  
|[Parameter](../msbuild/parameter-element.md)|Contiene información sobre un parámetro específico para una tarea que se genera mediante `UsingTask``TaskFactory`. El nombre del elemento es el nombre del parámetro.|  
  
### <a name="parent-elements"></a>Elementos primarios  
  
|Elemento|Descripción|  
|-------------|-----------------|  
|[UsingTask](../msbuild/usingtask-element-msbuild.md)|Proporciona una manera de registrar las tareas en [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)]. Puede haber cero o más elementos `UsingTask` en un proyecto.|  
  
## <a name="example"></a>Ejemplo  
 El ejemplo siguiente muestra cómo usar el elemento `ParameterGroup`.  
  
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
