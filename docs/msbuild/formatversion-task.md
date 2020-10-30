---
title: Tarea FormatVersion | Microsoft Docs
description: Obtenga información sobre las distintas formas en que las tareas FormatVersion de MSBuild anexan el número de revisión al número de versión.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
ms.assetid: 96e692f6-b581-46ca-8cc9-441a1861e371
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 16da018e49e6cb456074ebabac52a8768d06c1c6
ms.sourcegitcommit: c4927ef8fe239005d7feff6c5a7707c594a7a05c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/22/2020
ms.locfileid: "92436704"
---
# <a name="formatversion-task"></a>Tarea FormatVersion

Anexa el número de revisión al número de versión.

- Caso n.º 1: Entrada: Versión=\<undefined>;  Revisión=\<don't care>;   Salida: OutputVersion="1.0.0.0"

- Caso 2: Input: Version="1.0.0.*"  Revision="5"  Output: OutputVersion="1.0.0.5"

- Caso n.º 3: Entrada: Versión="1.0.0.0"  Revisión=\<don't care>;  Salida: OutputVersion="1.0.0.0"

## <a name="parameters"></a>Parámetros

 En la siguiente tabla se describen los parámetros de la tarea `FormatVersion` .

|Parámetro|Descripción|
|---------------|-----------------|
|`FormatType`|Parámetro `String` opcional.<br /><br /> Especifica el tipo de formato.<br /><br /> - "Version" = versión.<br />- "Path" = reemplace "." por "_";|
|`OutputVersion`|Parámetro de salida `String` opcional.<br /><br /> Especifica la versión de salida que incluye el número de revisión.|
|`Revision`|Parámetro `Int32` opcional.<br /><br /> Especifica la revisión que se va a anexar a la versión.|
|`Version`|Parámetro `String` opcional.<br /><br /> Especifica la cadena de número de versión a la que se va a aplicar formato.|

## <a name="remarks"></a>Observaciones

 Además de tener los parámetros que se enumeran en la tabla, esta tarea hereda los parámetros de la clase <xref:Microsoft.Build.Tasks.TaskExtension>, que a su vez hereda de la clase <xref:Microsoft.Build.Utilities.Task>. Para obtener una lista de estos parámetros adicionales y sus descripciones, consulte [TaskExtension base class](../msbuild/taskextension-base-class.md).

## <a name="see-also"></a>Vea también

- [Tareas](../msbuild/msbuild-tasks.md)
- [Referencia de tareas](../msbuild/msbuild-task-reference.md)
