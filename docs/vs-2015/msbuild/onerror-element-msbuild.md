---
title: Elemento OnError (MSBuild) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: conceptual
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
caps.latest.revision: 17
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 46f6907bea5954cffae92b41398717a8247350e0
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "68195661"
---
# <a name="onerror-element-msbuild"></a>Elemento OnError (MSBuild)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Hace que uno o varios destinos se ejecuten, si el atributo `ContinueOnError` es `false` para una tarea con error.  
  
 \<Project>  
 \<Target>  
 \<OnError>  
  
## <a name="syntax"></a>Sintaxis  
  
```  
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
|[Destino](../msbuild/target-element-msbuild.md)|Elemento contenedor para tareas de [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)].|  
  
## <a name="remarks"></a>Comentarios  
 [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] ejecuta el elemento `OnError` si una de las tareas del elemento `Target` da error con el atributo `ContinueOnError` establecido en `ErrorAndStop` (o `false`). Cuando la tarea produce un error, se ejecutan los destinos especificados en el atributo `ExecuteTargets`. Si hay más de un elemento `OnError` en el destino, los elementos `OnError` se ejecutan secuencialmente cuando se produce un error en la tarea.  
  
 Para obtener información sobre el `ContinueOnError` atributo, vea [elemento Task (MSBuild)](../msbuild/task-element-msbuild.md). Para más información sobre los destinos, consulte [Destinos](../msbuild/msbuild-targets.md).  
  
## <a name="example"></a>Ejemplo  
 El código siguiente ejecuta las tareas `TaskOne` y `TaskTwo`. Si `TaskOne` da error, [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] evalúa como el elemento `OnError` y ejecuta el destino `OtherTarget`.  
  
```  
<Target Name="ThisTarget">  
    <TaskOne ContinueOnError="ErrorAndStop">  
    </TaskOne>  
    <TaskTwo>  
    </TaskTwo>  
    <OnError ExecuteTargets="OtherTarget" />  
</Target>  
```  
  
## <a name="see-also"></a>Consulte también  
 [Referencia de esquema de archivo de proyecto](../msbuild/msbuild-project-file-schema-reference.md)   
 [Destinos](../msbuild/msbuild-targets.md)
