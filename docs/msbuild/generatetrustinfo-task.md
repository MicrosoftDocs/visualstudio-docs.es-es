---
title: Tarea GenerateTrustInfo | Microsoft Docs
description: Use la tarea GenerateTrustInfo de MSBuild para generar la confianza de la aplicación a partir del manifiesto base y los parámetros TargetZone y ExcludedPermissions.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, GenerateTrustInfo task
- GenerateTrustInfo task [MSBuild]
ms.assetid: 3ca60816-4bb0-4fef-ae43-ca0bfb63def3
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8a90188244e32b6f593affd2c29a227a2810227d
ms.sourcegitcommit: c4927ef8fe239005d7feff6c5a7707c594a7a05c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/22/2020
ms.locfileid: "92436450"
---
# <a name="generatetrustinfo-task"></a>GenerateTrustInfo (tarea)

Genera la información de confianza de la aplicación a partir del manifiesto base y de los parámetros `TargetZone` y `ExcludedPermissions`.

## <a name="parameters"></a>Parámetros

 En la siguiente tabla se describen los parámetros de la tarea `GenerateTrustInfo` .

|Parámetro|Description|
|---------------|-----------------|
|`ApplicationDependencies`|Parámetro <xref:Microsoft.Build.Framework.ITaskItem>`[]` opcional.<br /><br /> Especifica los ensamblados dependientes.|
|`BaseManifest`|Parámetro <xref:Microsoft.Build.Framework.ITaskItem> opcional.<br /><br /> Especifica el manifiesto base desde el cual se va a generar la confianza de la aplicación.|
|`ExcludedPermissions`|Parámetro `String` opcional.<br /><br /> Especifica uno o varios valores de identidad de permiso separados por punto y coma que se excluirán del conjunto de permisos predeterminado de la zona.|
|`TargetZone`|Parámetro `String` opcional.<br /><br /> Especifica un conjunto de permisos predeterminados de zona, que se obtiene a partir de la directiva de máquina.|
|`TrustInfoFile`|Parámetro de salida obligatorio de tipo <xref:Microsoft.Build.Framework.ITaskItem>.<br /><br /> Especifica el archivo que contiene la información de confianza de seguridad de la aplicación.|

## <a name="remarks"></a>Observaciones

 Además de tener los parámetros que se enumeran en la tabla, esta tarea hereda los parámetros de la clase <xref:Microsoft.Build.Tasks.TaskExtension>, que a su vez hereda de la clase <xref:Microsoft.Build.Utilities.Task>. Para obtener una lista de estos parámetros adicionales y sus descripciones, consulte [TaskExtension base class](../msbuild/taskextension-base-class.md).

## <a name="see-also"></a>Vea también

- [Tareas](../msbuild/msbuild-tasks.md)
- [Referencia de tareas](../msbuild/msbuild-task-reference.md)