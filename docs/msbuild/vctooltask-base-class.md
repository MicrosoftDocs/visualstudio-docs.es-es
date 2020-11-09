---
title: Clase VCToolTask | Microsoft Docs
description: Obtenga información sobre varios parámetros que la clase base VCToolTask agrega a las tareas que se heredan de ella.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: b2e45d7c672ebc2177c2bb197399133e7b077a5c
ms.sourcegitcommit: 1a36533f385e50c05f661f440380fda6386ed3c1
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/30/2020
ms.locfileid: "93046738"
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
|**GenerateCommandLineExceptSwitches**|Parámetro **string** opcional.<br/><br/>Usa los valores **string[]** *switchesToRemove* , **CommandLineFormat** *format* [default = CommandLineFormat.ForBuildLog] y **EscapeFormat** *escapeFormat* [default = EscapeFormat.Default].|

## <a name="see-also"></a>Vea también

[Referencia de tareas](../msbuild/msbuild-task-reference.md)<br/>
[Tareas](../msbuild/msbuild-tasks.md)
