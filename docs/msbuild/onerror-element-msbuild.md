---
title: Elemento OnError (MSBuild) | Microsoft Docs
ms.custom: ''
ms.date: 03/13/2017
ms.technology: msbuild
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#OnError
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- OnError Element [MSBuild]
- <OnError Element [MSBuild]
ms.assetid: 765767d3-ecb7-4cd9-ba1e-d9468964dddc
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 3f05f6b8bfc2cf75887192bcead9f55023fbddbd
ms.sourcegitcommit: e6b13898cfbd89449f786c2e8f3e3e7377afcf25
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/22/2018
ms.locfileid: "36326158"
---
# <a name="onerror-element-msbuild"></a>Elemento OnError (MSBuild)
Hace que uno o varios destinos se ejecuten, si el atributo `ContinueOnError` es `false` para una tarea con error.  

 \<Project>  
 \<Target>  
 \<OnError>  

## <a name="syntax"></a>Sintaxis  

```xml  
<OnError ExecuteTargets="TargetName"  
    Condition="'String A'=='String B'" />  
```  

## <a name="attributes-and-elements"></a>Atributos y elementos  
 En las siguientes secciones se describen los atributos, los elementos secundarios y los elementos primarios.  

### <a name="attributes"></a>Atributos  

|Atributo|Descripción|  
|---------------|-----------------|  
|`Condition`|Atributo opcional.<br /><br /> Condición que se va a evaluar. Para obtener más información, consulte [Condiciones](../msbuild/msbuild-conditions.md).|  
|`ExecuteTargets`|Atributo necesario.<br /><br /> Los destinos para ejecutar si se produce un error en una tarea. Separe varios destinos con puntos y coma. Se ejecutan varios destinos en el orden especificado.|  

### <a name="child-elements"></a>Elementos secundarios  
 Ninguno.  

### <a name="parent-elements"></a>Elementos primarios  

|Elemento|Descripción|  
|-------------|-----------------|  
|[Target](../msbuild/target-element-msbuild.md)|Elemento contenedor para tareas de [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)].|  

## <a name="remarks"></a>Comentarios  
 [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] ejecuta el elemento `OnError` si una de las tareas del elemento `Target` da error con el atributo `ContinueOnError` establecido en `ErrorAndStop` (o `false`). Cuando la tarea produce un error, se ejecutan los destinos especificados en el atributo `ExecuteTargets`. Si hay más de un elemento `OnError` en el destino, los elementos `OnError` se ejecutan secuencialmente cuando se produce un error en la tarea.  

 Para obtener información sobre el atributo `ContinueOnError`, consulte [Elemento Task (MSBuild)](../msbuild/task-element-msbuild.md). Para más información sobre los destinos, consulte [Destinos](../msbuild/msbuild-targets.md).  

## <a name="example"></a>Ejemplo  
 El código siguiente ejecuta las tareas `TaskOne` y `TaskTwo`. Si `TaskOne` da error, [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] evalúa como el elemento `OnError` y ejecuta el destino `OtherTarget`.  

```xml  
<Target Name="ThisTarget">  
    <TaskOne ContinueOnError="ErrorAndStop">  
    </TaskOne>  
    <TaskTwo>  
    </TaskTwo>  
    <OnError ExecuteTargets="OtherTarget" />  
</Target>  
```  

## <a name="see-also"></a>Vea también  
 [Referencia de esquemas de archivo del proyecto](../msbuild/msbuild-project-file-schema-reference.md)   
 [Destinos](../msbuild/msbuild-targets.md)
