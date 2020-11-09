---
title: Clase TrackedVCToolTask | Microsoft Docs
description: Obtenga información sobre los parámetros que la clase base TrackedVCToolTask agrega a las tareas que se heredan de ella.
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
ms.openlocfilehash: 01b55e0ad88cb520078479217306bac948e6cd60
ms.sourcegitcommit: 1a36533f385e50c05f661f440380fda6386ed3c1
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/30/2020
ms.locfileid: "93046999"
---
# <a name="trackedvctooltask-base-class"></a>Clase base TrackedVCToolTask

En última instancia, muchas tareas se heredan de la clase <xref:Microsoft.Build.Utilities.Task> y de la clase [ToolTask](/dotnet/api/microsoft.build.utilities.tooltask). Esta clase agrega varios parámetros a las tareas que derivan de [VCToolTask](../msbuild/vctooltask-base-class.md). Estos parámetros se muestran en este documento.

## <a name="parameters"></a>Parámetros

En la tabla siguiente se describen los parámetros de la clase base **TrackedVCToolTask**.

|Parámetro|Description|
|---------------|-----------------|
|**DeleteOutputOnExecute**|Parámetro **bool** opcional.|
|**EnableExecuteTool**|Parámetro **bool** opcional.|
|**ExcludedInputPaths**|Parámetro opcional de tipo **ITaskItem[]** .|
|**MinimalRebuildFromTracking**|Parámetro **bool** opcional.|
|**PathOverride**|Parámetro **string** opcional.|
|**PostBuildTrackingCleanup**|Parámetro **bool** opcional.|
|**RootSource**|Parámetro **string** opcional.|
|**SkippedExecution**|Parámetro de salida **bool** opcional.|
|**SourcesCompiled**|Parámetro de salida opcional de tipo **ITaskItem[]**.|
|**TLogCommandFile**|Parámetro **ITaskItem** opcional.|
|**TLogReadFiles**|Parámetro opcional de tipo **ITaskItem[]** .|
|**TLogWriteFiles**|Parámetro opcional de tipo **ITaskItem[]** .|
|**ToolArchitecture**|Parámetro **string** opcional.|
|**TrackCommandLines**|Parámetro **bool** opcional.|
|**TrackFileAccess**|Parámetro **bool** opcional.|
|**TrackedInputFilesToIgnore**|Parámetro opcional de tipo **ITaskItem[]** .|
|**TrackedOutputFilesToIgnore**|Parámetro opcional de tipo **ITaskItem[]** .|
|**TrackerFrameworkPath**|Parámetro **string** opcional.|
|**TrackerSdkPath**|Parámetro **string** opcional.|

## <a name="see-also"></a>Vea también

[Referencia de tareas](../msbuild/msbuild-task-reference.md)<br/>
[Tareas](../msbuild/msbuild-tasks.md)
