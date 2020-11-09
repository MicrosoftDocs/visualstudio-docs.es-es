---
title: UpdateManifest (Tarea) | Microsoft Docs
description: Obtenga información sobre cómo MSBuild usa la tarea UpdateManifest para actualizar las propiedades seleccionadas en un manifiesto y refirmar.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, UpdateManifest task
- UpdateManifest task [MSBuild]
ms.assetid: 1291fd33-b89e-4e15-8fb1-69f9625cf2d2
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4fab3844b21e12edceb83da310e9069199578ef6
ms.sourcegitcommit: 1a36533f385e50c05f661f440380fda6386ed3c1
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/30/2020
ms.locfileid: "93046850"
---
# <a name="updatemanifest-task"></a>UpdateManifest (tarea)

Actualiza las propiedades seleccionadas en un manifiesto y se retira.

## <a name="parameters"></a>Parámetros

 En la siguiente tabla se describen los parámetros de la tarea `UpdateManifest` .

|Parámetro|Descripción|
|---------------|-----------------|
|`ApplicationManifest`|Parámetro <xref:Microsoft.Build.Framework.ITaskItem> requerido.<br /><br /> Especifica el manifiesto de aplicación.|
|`ApplicationPath`|Parámetro `String` requerido.<br /><br /> Especifica la ruta de acceso al manifiesto de aplicación.|
|`InputManifest`|Parámetro <xref:Microsoft.Build.Framework.ITaskItem> requerido.<br /><br /> Especifica el manifiesto que se desea actualizar.|
|`OutputManifest`|Parámetro de salida <xref:Microsoft.Build.Framework.ITaskItem> opcional.<br /><br /> Especifica el manifiesto que contiene propiedades actualizadas.|

## <a name="remarks"></a>Comentarios

 Además de tener los parámetros que se enumeran en la tabla, esta tarea hereda los parámetros de la clase <xref:Microsoft.Build.Utilities.Task>. Para obtener una lista de estos parámetros adicionales y sus descripciones, consulte [Task Base (Clase)](../msbuild/task-base-class.md).

## <a name="see-also"></a>Vea también

- [Tareas](../msbuild/msbuild-tasks.md)
- [Referencia de tareas](../msbuild/msbuild-task-reference.md)