---
title: XslTransformation (Tarea) | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, XslTransformation task
- XslTransformation task [MSBuild]
ms.assetid: 6f3a7d81-3ae3-4703-9a06-870b32b69d80
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 84bc83f60d133dcaf22c9fa690357fa2624adabd
ms.sourcegitcommit: 96737c54162f5fd5c97adef9b2d86ccc660b2135
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/26/2020
ms.locfileid: "77630800"
---
# <a name="xsltransformation-task"></a>XslTransformation (tarea)

Transforma una entrada XML mediante una transformación XSL o una transformación XSL compilada y la envía a un dispositivo de salida o archivo.

## <a name="parameters"></a>Parámetros

 En la siguiente tabla se describen los parámetros de la tarea `XslTransformation` .

|Parámetro|Descripción|
|---------------|-----------------|
|`OutputPaths`|Parámetro <xref:Microsoft.Build.Framework.ITaskItem>`[]` requerido.<br /><br /> Especifica los archivos de salida de la transformación XML.|
|`Parameters`|Parámetro `String` opcional.<br /><br /> Especifica los parámetros del documento de entrada XSLT.|
|`XmlContent`|Parámetro `String` opcional.<br /><br /> Especifica la entrada XML como una cadena.|
|`XmlInputPaths`|Parámetro <xref:Microsoft.Build.Framework.ITaskItem>`[]` opcional.<br /><br /> Especifica los archivos de entrada XML.|
|`XslCompiledDllPath`|Parámetro <xref:Microsoft.Build.Framework.ITaskItem> opcional.<br /><br /> Especifica el XSLT compilado.|
|`XslContent`|Parámetro `String` opcional.<br /><br /> Especifica la entrada XSLT como una cadena.|
|`XslInputPath`|Parámetro <xref:Microsoft.Build.Framework.ITaskItem> opcional.<br /><br /> Especifica el archivo de entrada XSLT.|

## <a name="remarks"></a>Comentarios

 Además de tener los parámetros que se enumeran en la tabla, esta tarea hereda los parámetros de la clase <xref:Microsoft.Build.Tasks.TaskExtension>, que a su vez hereda de la clase <xref:Microsoft.Build.Utilities.Task>. Para obtener una lista de estos parámetros adicionales y sus descripciones, consulte [TaskExtension base class](../msbuild/taskextension-base-class.md).

## <a name="see-also"></a>Vea también

- [Tareas](../msbuild/msbuild-tasks.md)
- [Referencia de tareas](../msbuild/msbuild-task-reference.md)
