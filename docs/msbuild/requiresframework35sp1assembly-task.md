---
title: Tarea RequiresFramework35SP1Assembly | Microsoft Docs
description: Obtenga información sobre cómo MSBuild usa la tarea RequiresFramework35SP1Assembly para determinar si la aplicación requiere .NET Framework 3.5 SP1.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- RequiresFramework35SP1Assembly task [MSBuild]
- MSBuild, RequiresFramework35SP1Assembly task
ms.assetid: 755c018a-8a8b-4c94-8aee-3f171fc419e5
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d1819f72cc0eef389a3ef46148d4462fbd610e1a
ms.sourcegitcommit: 1a36533f385e50c05f661f440380fda6386ed3c1
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/30/2020
ms.locfileid: "93048683"
---
# <a name="requiresframework35sp1assembly-task"></a>RequiresFramework35SP1Assembly (tarea)

Determina si la aplicación requiere .NET Framework 3.5 SP1.

## <a name="parameters"></a>Parámetros

 En la siguiente tabla se describen los parámetros de la tarea `RequiresFramework35SP1Assembly` .

|Parámetro|Description|
|---------------|-----------------|
|`Assemblies`|Parámetro <xref:Microsoft.Build.Framework.ITaskItem>`[]` opcional.<br /><br /> Especifica los ensamblados a los que se hace referencia en la aplicación.|
|`CreateDesktopShortcut`|Parámetro `Boolean` opcional.<br /><br /> Si es `true`, crea un icono de acceso directo en el escritorio durante la instalación.|
|`DeploymentManifestEntryPoint`|Parámetro <xref:Microsoft.Build.Framework.ITaskItem> opcional.<br /><br /> Especifica el nombre de archivo de manifiesto de la aplicación.|
|`EntryPoint`|Parámetro <xref:Microsoft.Build.Framework.ITaskItem> opcional.<br /><br /> Especifica el ensamblado que se debe ejecutar cuando se ejecuta la aplicación.|
|`ErrorReportUrl`|Parámetro `String` opcional.<br /><br /> Especifica el sitio web que se muestra en los cuadros de diálogo que aparecen durante las instalaciones ClickOnce.|
|`Files`|Parámetro <xref:Microsoft.Build.Framework.ITaskItem>`[]` opcional.<br /><br /> Especifica la lista de archivos que se implementarán cuando se publique la aplicación.|
|`ReferencedAssemblies`|Parámetro <xref:Microsoft.Build.Framework.ITaskItem>`[]` opcional.<br /><br /> Especifica los ensamblados a los que se hace referencia en el proyecto.|
|`RequiresMinimumFramework35SP1`|Parámetro de salida `Boolean` opcional.<br /><br /> Si es `true`, la aplicación requiere .NET Framework 3.5 SP1.|
|`SigningManifests`|Parámetro de salida `Boolean` opcional.<br /><br /> Si es `true`, los manifiestos de ClickOnce están firmados.|
|`SuiteName`|Parámetro `String` opcional.<br /><br /> Especifica el nombre de la carpeta en el menú **Inicio** donde se va a instalar la aplicación.|
|`TargetFrameworkVersion`|Parámetro `String` opcional.<br /><br /> Especifica la versión de .NET Framework a la que se destina la aplicación.|

## <a name="remarks"></a>Comentarios

 Además de tener los parámetros que se enumeran en la tabla, esta tarea hereda los parámetros de la clase <xref:Microsoft.Build.Tasks.TaskExtension>, que a su vez hereda de la clase <xref:Microsoft.Build.Utilities.Task>. Para obtener una lista de estos parámetros adicionales y sus descripciones, consulte [TaskExtension base class](../msbuild/taskextension-base-class.md).

## <a name="see-also"></a>Vea también

- [Tareas](../msbuild/msbuild-tasks.md)
- [Referencia de tareas](../msbuild/msbuild-task-reference.md)