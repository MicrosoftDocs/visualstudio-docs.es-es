---
title: ParameterGroup (Elemento) | Microsoft Docs
description: Obtenga información sobre el elemento ParameterGroup de MSBuild, que contiene una lista opcional de parámetros presentes en la tarea generada por TaskFactory de UsingTask.
ms.custom: SEO-VS-2020
ms.date: 03/13/2017
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- <ParameterGroup> element [MSBuild]
- ParameterGroup element [MSBuild]
ms.assetid: c3275e69-a427-4889-bc1d-51bff2c285fa
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 56ff9c63de40f6a352c10f92b937a397c683fc65
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99905298"
---
# <a name="parametergroup-element"></a>ParameterGroup (Elemento)

Contiene una lista opcional de parámetros que estarán presentes en la tarea generada por `UsingTask` `TaskFactory`. Para más información, consulte [Elemento UsingTask (MSBuild)](../msbuild/usingtask-element-msbuild.md).

 \<Project> \<UsingTask>
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
|[Parámetro](../msbuild/parameter-element.md)|Contiene información sobre un parámetro específico para una tarea que se genera mediante `UsingTask` `TaskFactory`. El nombre del elemento es el nombre del parámetro.|

### <a name="parent-elements"></a>Elementos primarios

| Elemento | Descripción |
| - | - |
| [UsingTask](../msbuild/usingtask-element-msbuild.md) | Proporciona una manera de registrar las tareas en MSBuild. Puede haber cero o más elementos `UsingTask` en un proyecto. |

## <a name="example"></a>Ejemplo

 El ejemplo siguiente muestra cómo usar el elemento `ParameterGroup`.

```xml
<UsingTask TaskName="MyTask" AssemblyName="My.Assembly" TaskFactory="MyTaskFactory">
       <ParameterGroup>
              <Parameter1 ParameterType="System.String" Required="False" Output="False"/>
              <Parameter2 ParameterType="System.Int" Required="True" Output="False"/>
             ...
</ParameterGroup>
       <Task Evaluate="true">
       ... Task factory-specific data ...
       </Task>
</UsingTask>
```

## <a name="see-also"></a>Vea también

- [Tareas](../msbuild/msbuild-tasks.md)
- [Referencia de tareas](../msbuild/msbuild-task-reference.md)
- [Referencia de esquema de archivo de proyecto](../msbuild/msbuild-project-file-schema-reference.md)
