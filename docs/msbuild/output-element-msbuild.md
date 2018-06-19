---
title: Elemento Output (MSBuild) | Microsoft Docs
ms.custom: ''
ms.date: 03/13/2017
ms.technology: msbuild
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#Output
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- <Output> Element [MSBuild]
- Output Element [MSBuild]
ms.assetid: 34bc7cd1-efd3-4b57-b691-4584eeb6a0e9
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 6e5f1d4dec10970770202e685860381cdec15608
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/19/2018
ms.locfileid: "31577358"
---
# <a name="output-element-msbuild"></a>Elemento Output (MSBuild)
Almacena valores de salida de tarea en elementos y propiedades.  

 \<Project>  
 \<Target>  
 \<Task>  
 \<Output>  

## <a name="syntax"></a>Sintaxis  

```  
<Output TaskParameter="Parameter"  
    PropertyName="PropertyName"   
    Condition = "'String A' == 'String B'" />  
```  

## <a name="attributes-and-elements"></a>Atributos y elementos  
 En las siguientes secciones se describen los atributos, los elementos secundarios y los elementos primarios.  

### <a name="attributes"></a>Atributos  

|Atributo|Description|  
|---------------|-----------------|  
|`TaskParameter`|Atributo necesario.<br /><br /> El nombre del parámetro de salida de la tarea.|  
|`PropertyName`|Se necesita el atributo `PropertyName` o `ItemName`.<br /><br /> La propiedad que recibe el valor del parámetro de salida de la tarea. Después, el proyecto puede hacer referencia a la propiedad con la sintaxis `$(`*PropertyName*`)`. Este nombre de propiedad puede ser un nuevo nombre de propiedad o un nombre que ya está definido en el proyecto.<br /><br /> Este atributo no se puede usar si `ItemName` también se utiliza.|  
|`ItemName`|Se necesita el atributo `PropertyName` o `ItemName`.<br /><br /> El elemento que recibe el valor del parámetro de salida de la tarea. Después, el proyecto puede hacer referencia al elemento con la sintaxis `@(`*ItemName*`)`. El nombre de elemento puede ser un nuevo nombre de elemento o un nombre que ya está definido en el proyecto.<br /><br /> Este atributo no se puede usar si `PropertyName` también se utiliza.|  
|`Condition`|Atributo opcional.<br /><br /> Condición que se va a evaluar. Para obtener más información, consulte [Condiciones](../msbuild/msbuild-conditions.md).|  

### <a name="child-elements"></a>Elementos secundarios  
 Ninguno.  

### <a name="parent-elements"></a>Elementos primarios  

|Elemento|Description|  
|-------------|-----------------|  
|[Task](../msbuild/task-element-msbuild.md)|Crea y ejecuta una instancia de una tarea [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)].|  

## <a name="example"></a>Ejemplo  
 En el siguiente ejemplo de código se muestra la tarea `Csc` que se ejecuta dentro de un elemento `Target`. Los elementos y las propiedades que se pasan a los parámetros de tarea se declaran fuera del ámbito de este ejemplo. El valor del parámetro de salida `OutputAssembly` se almacena en el `FinalAssemblyName` elemento y el valor del parámetro de salida `BuildSucceeded` se almacena en la propiedad `BuildWorked`. Para obtener más información, consulte [Tareas](../msbuild/msbuild-tasks.md).  

```xml  
<Target Name="Compile" DependsOnTargets="Resources">  
    <Csc  Sources="@(CSFile)"  
            TargetType="library"  
            Resources="@(CompiledResources)"  
            EmitDebugInformation="$(includeDebugInformation)"  
            References="@(Reference)"  
            DebugType="$(debuggingType)"  
            OutputAssembly="$(builtdir)\$(MSBuildProjectName).dll" >  
        <Output TaskParameter="OutputAssembly"  
                  ItemName="FinalAssemblyName" />  
        <Output TaskParameter="BuildSucceeded"  
                  PropertyName="BuildWorked" />  
    </Csc>  
</Target>  
```  

## <a name="see-also"></a>Vea también  
 [Referencia de esquemas de archivo del proyecto](../msbuild/msbuild-project-file-schema-reference.md)   
 [Tareas](../msbuild/msbuild-tasks.md)
