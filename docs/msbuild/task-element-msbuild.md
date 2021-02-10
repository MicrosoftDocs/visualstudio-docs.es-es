---
title: Elemento Task de Target (MSBuild) | Microsoft Docs
description: Obtenga información sobre el elemento Task de Target de MSBuild, que crea y ejecuta una instancia de una tarea de MSBuild.
ms.custom: SEO-VS-2020
ms.date: 03/13/2017
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- Task element [MSBuild]
- <Task> element [MSBuild]
ms.assetid: d82e2485-e5f0-4936-a357-745bacccc299
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: a4b8e3cb3acccc2e7ae4c6c2d93353bec79a3690
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99966050"
---
# <a name="task-element-of-target-msbuild"></a>Elemento Task de Target (MSBuild)

Crea y ejecuta una instancia de una tarea de MSBuild. El nombre del elemento se determina viene determinado por el nombre de la tarea que se va a crear.

 \<Project> \<Target>

## <a name="syntax"></a>Sintaxis

```xml
<Task Parameter1="Value1"... ParameterN="ValueN"
    ContinueOnError="WarnAndContinue/true/ErrorAndContinue/ErrorAndStop/false"
    Condition="'String A' == 'String B'" >
    <Output... />
</Task>
```

## <a name="attributes-and-elements"></a>Atributos y elementos

 En las siguientes secciones se describen los atributos, los elementos secundarios y los elementos primarios.

### <a name="attributes"></a>Atributos

|Atributo|Descripción|
|---------------|-----------------|
|`Condition`|Atributo opcional. Condición que se va a evaluar. Para obtener más información, consulte [Condiciones](../msbuild/msbuild-conditions.md).|
|`ContinueOnError`|Atributo opcional. Puede contener uno de los siguientes valores:<br /><br /> -   **WarnAndContinue** o **true**. Cuando se produce un error en una tarea, las tareas subsiguientes en el elemento [Target](../msbuild/target-element-msbuild.md) y la compilación continúan ejecutándose, y todos los errores de la tarea se tratan como advertencias.<br />-   **ErrorAndContinue**. Cuando se produce un error en una tarea, las tareas subsiguientes en el elemento `Target` y la compilación continúan ejecutándose, y todos los errores de la tarea se tratan como errores.<br />-   **ErrorAndStop** o **false** (valor predeterminado). Cuando se produce un error en una tarea, las tareas restantes en el elemento `Target` y la compilación no se ejecutan, y se considera que se ha producido un error en todo el elemento `Target` y la compilación.<br /><br /> Las versiones de .NET Framework anteriores a 4.5 solo admiten los valores `true` y `false`.<br /><br /> Para obtener más información, vea [Cómo: Pasar errores por alto en las tareas](../msbuild/how-to-ignore-errors-in-tasks.md).|
|`Parameter`|Se necesita si la clase de tarea contiene una o más propiedades etiquetadas con el atributo `[Required]`.<br /><br /> Un parámetro de tarea definido por el usuario que contiene el valor del parámetro como su valor. Puede haber cualquier número de parámetros en el elemento `Task`, con cada asignación de atributo a una propiedad de .NET en la clase de tarea.|

### <a name="child-elements"></a>Elementos secundarios

|Elemento|Descripción|
|-------------|-----------------|
|[Salida](../msbuild/output-element-msbuild.md)|Almacena salidas de la tarea en el archivo de proyecto. Puede haber cero o más elementos `Output` en una tarea.|

### <a name="parent-elements"></a>Elementos primarios

| Elemento | Descripción |
| - | - |
| [Destino](../msbuild/target-element-msbuild.md) | Elemento contenedor para tareas de MSBuild. |

## <a name="remarks"></a>Comentarios

 Un elemento `Task` en un archivo de proyecto de MSBuild crea una instancia de una tarea, establece propiedades en ella y la ejecuta. El elemento `Output` almacena los parámetros de salida en propiedades o elementos que se usarán en otro lugar en el archivo de proyecto.

 Si hay algún elemento [OnError](../msbuild/onerror-element-msbuild.md) en el elemento `Target` principal de una tarea, se evaluará si se produce un error en la tarea y `ContinueOnError` tiene un valor de `false`. Para más información sobre las tareas, consulte [Tareas](../msbuild/msbuild-tasks.md).

## <a name="example"></a>Ejemplo

 El ejemplo de código siguiente se crea una instancia de la clase [tarea Csc](../msbuild/csc-task.md), establece seis de las propiedades y ejecuta la tarea. Después de la ejecución, el valor de la propiedad `OutputAssembly` del objeto se coloca en una lista de elementos denominada `FinalAssemblyName`.

```xml
<Target Name="Compile" DependsOnTarget="Resources" >
    <Csc Sources="@(CSFile)"
          TargetType="library"
          Resources="@(CompiledResources)"
          EmitDebugInformation="$(includeDebugInformation)"
          References="@(Reference)"
          DebugType="$(debuggingType)" >
        <Output TaskParameter="OutputAssembly"
                  ItemName="FinalAssemblyName" />
    </Csc>
</Target>
```

## <a name="see-also"></a>Vea también

- [Tareas](../msbuild/msbuild-tasks.md)
- [Referencia de tareas](../msbuild/msbuild-task-reference.md)
- [Referencia de esquema de archivo de proyecto](../msbuild/msbuild-project-file-schema-reference.md)
