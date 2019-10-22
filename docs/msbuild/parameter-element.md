---
title: Elemento Parameter | Microsoft Docs
ms.date: 03/13/2017
ms.topic: reference
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
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: fc410948f3869de5ca3059cba703e5381f93d7eb
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62999678"
---
# <a name="parameter-element"></a>Elemento Parameter
Contiene información sobre un parámetro específico para una tarea que se genera mediante `UsingTask``TaskFactory`.  El nombre del elemento es el nombre del parámetro.  Para más información, consulte [Elemento UsingTask (MSBuild)](../msbuild/usingtask-element-msbuild.md).

 \<Project> \<UsingTask> \<ParameterGroup> \<Parameter>

## <a name="syntax"></a>Sintaxis

```xml
<ParameterGroup ParameterType="SystemType"
    Output="true/false"
    Required="true/false" />
```

## <a name="attributes-and-elements"></a>Atributos y elementos
 En las siguientes secciones se describen los atributos, los elementos secundarios y los elementos primarios.

### <a name="attributes"></a>Atributos

|Atributo|Descripción|
|---------------|-----------------|
|`ParameterType`|Atributo opcional.<br /><br /> El tipo .NET del parámetro, por ejemplo, `System.String`.|
|`Output`|Atributo Boolean opcional.<br /><br /> Si es `true`, este parámetro es un parámetro de salida para la tarea. De forma predeterminada, el valor es `false`.|
|`Required`|Atributo Boolean opcional.<br /><br /> Si es `true`, este parámetro es un parámetro necesario para la tarea. De forma predeterminada, el valor es `false`.|

### <a name="child-elements"></a>Elementos secundarios
 Ninguno.

### <a name="parent-elements"></a>Elementos primarios

|Elemento|Descripción|
|-------------|-----------------|
|[ParameterGroup](../msbuild/parametergroup-element.md)|Contiene una lista opcional de parámetros que estarán presentes en la tarea generada por `UsingTask` `TaskFactory`.|

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
- [Tareas](../msbuild/msbuild-tasks.md)
- [Referencia de tareas](../msbuild/msbuild-task-reference.md)
- [Referencia de esquema de archivo de proyecto](../msbuild/msbuild-project-file-schema-reference.md)
