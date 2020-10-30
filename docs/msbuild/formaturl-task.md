---
title: Tarea FormatUrl | Microsoft Docs
description: Obtenga información sobre cómo usar la tarea FormatUrl de MSBuild para convertir una dirección URL de entrada en un formato de dirección URL de salida correcto.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, FormatUrl task
- FormatUrl task [MSBuild]
ms.assetid: 81114b67-520f-43b5-8891-224f68a78516
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0e38a0f1aea6999e30d2ab2493873f66cd907878
ms.sourcegitcommit: c4927ef8fe239005d7feff6c5a7707c594a7a05c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/22/2020
ms.locfileid: "92436885"
---
# <a name="formaturl-task"></a>FormatUrl (tarea)

Convierte una dirección URL en un formato de dirección URL correcto.

## <a name="parameters"></a>Parámetros

 En la siguiente tabla se describen los parámetros de la tarea `FormatUrl` .

|Parámetro|Descripción|
|---------------|-----------------|
|`InputUrl`|Parámetro `String` opcional.<br /><br /> Especifica la dirección URL a la que se va a aplicar formato.|
|`OutputUrl`|Parámetro de salida `String` opcional.<br /><br /> Especifica la dirección URL con formato.|

## <a name="remarks"></a>Observaciones

 Además de tener los parámetros que se enumeran en la tabla, esta tarea hereda los parámetros de la clase <xref:Microsoft.Build.Tasks.TaskExtension>, que a su vez hereda de la clase <xref:Microsoft.Build.Utilities.Task>. Para obtener una lista de estos parámetros adicionales y sus descripciones, consulte [TaskExtension base class](../msbuild/taskextension-base-class.md).

## <a name="see-also"></a>Vea también

- [Tareas](../msbuild/msbuild-tasks.md)
- [Referencia de tareas](../msbuild/msbuild-task-reference.md)