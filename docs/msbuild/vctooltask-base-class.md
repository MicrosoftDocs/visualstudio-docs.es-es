---
title: Clase VCToolTask | Microsoft Docs
ms.date: 03/10/2019
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
author: ghogen
ms.author: ghogen
ms.workload:
- multiple
ms.openlocfilehash: df75bb998d2b8c6486e20c4c3ca0d80347c8f88a
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/18/2020
ms.locfileid: "75591676"
---
# <a name="vctooltask-base-class"></a>Clase base VCToolTask

En última instancia, muchas tareas se heredan de la clase <xref:Microsoft.Build.Utilities.Task> y de la clase [ToolTask](/dotnet/api/microsoft.build.utilities.tooltask). Esta clase agrega varios parámetros a las tareas que derivan de ellos. Estos parámetros se muestran en este documento.

## <a name="parameters"></a>Parámetros

En la tabla siguiente se describen los parámetros de la clase base **VCToolTask**.

|Parámetro|Description|
|---------------|-----------------|
|**ActiveToolSwitchesValues**|Parámetro **Dictionary\<string, ToolSwitch>** opcional.|
|**AdditionalOptions**|Parámetro **string** opcional.|
|**EffectiveWorkingDirectory**|Parámetro **string** opcional.|
|**EnableErrorListRegex**|Parámetro **bool** opcional.<br/><br/>El valor predeterminado es `true`.|
|**ErrorListRegex**|Parámetro opcional de tipo **ITaskItem[]** .|
|**ErrorListListExclusion**|Parámetro opcional de tipo **ITaskItem[]** .|
|**GenerateCommandLine**|Parámetro **string** opcional.<br/><br/>Usa los valores **CommandLineFormat** *format* [default = CommandLineFormat.ForBuildLog] y **EscapeFormat** *escapeFormat* [default = EscapeFormat.Default].|
|**GenerateCommandLineExceptSwitches**|Parámetro **string** opcional.<br/><br/>Usa los valores **string[]** *switchesToRemove*, **CommandLineFormat** *format* [default = CommandLineFormat.ForBuildLog] y **EscapeFormat** *escapeFormat* [default = EscapeFormat.Default].|

## <a name="see-also"></a>Vea también

[Referencia de tareas](../msbuild/msbuild-task-reference.md)<br/>
[Tareas](../msbuild/msbuild-tasks.md)
