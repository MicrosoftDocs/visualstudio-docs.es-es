---
title: Elemento TaskBody (MSBuild) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- TaskBody element [MSBuild]
- <TaskBody> element [MSBuild]
ms.assetid: 49d8741b-f1ea-4470-94fd-a1ac27341a6a
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 6b02616b54c0697f824d53eab978142679e8a358
ms.sourcegitcommit: a83c60bb00bf95e6bea037f0e1b9696c64deda3c
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 02/19/2019
ms.locfileid: "54752398"
---
# <a name="taskbody-element-msbuild"></a>TaskBody (Elemento) (MSBuild)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Contiene los datos que se pasen a `UsingTask``TaskFactory`. Para obtener más información, consulte [Elemento UsingTask (MSBuild)](../msbuild/usingtask-element-msbuild.md).  
  
 \<Project>  
 \<UsingTask>  
 \<TaskBody>  
  
## <a name="syntax"></a>Sintaxis  
  
```  
<TaskBody Evaluate="true/false" />  
```  
  
## <a name="attributes-and-elements"></a>Atributos y elementos  
 En las siguientes secciones se describen los atributos, los elementos secundarios y los elementos primarios.  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descripción|  
|---------------|-----------------|  
|`Evaluate`|Atributo Boolean opcional.<br /><br /> Si es `true`, MSBuild evalúa los elementos internos y expande los elementos y las propiedades antes de pasar la información a `TaskFactory` cuando se crea una instancia de la tarea.|  
  
### <a name="child-elements"></a>Elementos secundarios  
  
|Elemento|Descripción|  
|-------------|-----------------|  
|Datos|El texto entre las etiquetas `TaskBody` se envía textual a `TaskFactory`.|  
  
### <a name="parent-elements"></a>Elementos primarios  
  
|Elemento|Descripción|  
|-------------|-----------------|  
|[UsingTask](../msbuild/usingtask-element-msbuild.md)|Proporciona una manera de registrar las tareas en [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)]. Puede haber cero o más elementos `UsingTask` en un proyecto.|  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra cómo usar el elemento `TaskBody` con un atributo `Evaluate`.  
  
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
  
## <a name="see-also"></a>Vea también  
 [Tareas](../msbuild/msbuild-tasks.md)   
 [Referencia de tareas](../msbuild/msbuild-task-reference.md)   
 [Referencia de esquemas de archivo del proyecto](../msbuild/msbuild-project-file-schema-reference.md)
