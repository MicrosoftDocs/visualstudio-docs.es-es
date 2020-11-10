---
title: Message (Tarea) | Microsoft Docs
description: Obtenga información sobre los parámetros y la configuración de la tarea Message de MSBuild, que registra mensajes durante las compilaciones.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#Message
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, Message task
- Message task [MSBuild]
ms.assetid: 2293309d-42b6-46dc-9684-8c146f66bc28
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1b7a2854220a7ee85fd680cedd8c8e0c5c3ada89
ms.sourcegitcommit: f1d47655974a2f08e69704a9a0c46cb007e51589
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/28/2020
ms.locfileid: "92903833"
---
# <a name="message-task"></a>Message (tarea)

Registra un mensaje durante una compilación.

## <a name="parameters"></a>Parámetros

 En la siguiente tabla se describen los parámetros de la tarea `Message` .

|Parámetro|Description|
|---------------|-----------------|
|`Importance`|Parámetro `String` opcional.<br /><br /> Especifica la importancia del mensaje. Este parámetro puede tener un valor de `high`, `normal` o `low`. El valor predeterminado es `normal`.|
|`Text`|Parámetro `String` opcional.<br /><br /> El texto del error que se va a registrar.|

## <a name="remarks"></a>Comentarios

 La tarea `Message` permite a los proyectos de MSBuild enviar mensajes a los registradores en etapas diferentes del proceso de compilación.

 Si el parámetro `Condition` se evalúa como `true`, se registrará el valor del parámetro `Text` y la compilación seguirá ejecutándose. Si no existe un parámetro `Condition`, se registra el texto del mensaje. Para obtener más información sobre los registros, vea [Obtener registros de compilación con MSBuild](../msbuild/obtaining-build-logs-with-msbuild.md).

 De forma predeterminada, el mensaje se envía a todos los registradores registrados. El registrador interpreta el parámetro `Importance`. Habitualmente, un mensaje establecido en `high` se envía cuando el nivel de detalle del registrador está establecido en <xref:Microsoft.Build.Framework.LoggerVerbosity>.`Minimal` o superior. Cuando el nivel de detalle del registrador está establecido en <xref:Microsoft.Build.Framework.LoggerVerbosity>.`Detailed`, se envía un mensaje establecido en `low`.

 Además de los parámetros mencionados anteriormente, esta tarea hereda los parámetros de la clase <xref:Microsoft.Build.Tasks.TaskExtension>, que a su vez hereda de la clase <xref:Microsoft.Build.Utilities.Task>. Para obtener una lista de estos parámetros adicionales y sus descripciones, consulte [TaskExtension base class](../msbuild/taskextension-base-class.md).

## <a name="example"></a>Ejemplo

 El siguiente ejemplo de código registra mensajes para todos los registradores registrados.

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
    <Target Name="DisplayMessages">
        <Message Text="Project File Name = $(MSBuildProjectFile)" />
        <Message Text="Project Extension = $(MSBuildProjectExtension)" />
    </Target>
    ...
</Project>
```

## <a name="see-also"></a>Vea también

- [Referencia de tareas](../msbuild/msbuild-task-reference.md)
- [Obtener registros de compilación](../msbuild/obtaining-build-logs-with-msbuild.md)
