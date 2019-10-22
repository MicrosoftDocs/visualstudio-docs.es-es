---
title: Message (Tarea) | Microsoft Docs
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
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5efcc41a82cab32172aa395b488535f2777b9e13
ms.sourcegitcommit: 5694c5236fa32ba7f5bc1236a853f725ec7557e9
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/31/2019
ms.locfileid: "68681158"
---
# <a name="message-task"></a>Message (tarea)
Registra un mensaje durante una compilación.

## <a name="parameters"></a>Parámetros
 En la siguiente tabla se describen los parámetros de la tarea `Message` .

|Parámetro|DESCRIPCIÓN|
|---------------|-----------------|
|`Importance`|Parámetro `String` opcional.<br /><br /> Especifica la importancia del mensaje. Este parámetro puede tener un valor de `high`, `normal` o `low`. El valor predeterminado es `normal`.|
|`Text`|Parámetro `String` opcional.<br /><br /> El texto del error que se va a registrar.|

## <a name="remarks"></a>Comentarios
 La tarea `Message` permite a los proyectos de [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] enviar mensajes a los registradores en etapas diferentes del proceso de compilación.

 Si el parámetro `Condition` se evalúa como `true`, se registrará el valor del parámetro `Text` y la compilación seguirá ejecutándose. Si no existe un parámetro `Condition`, se registra el texto del mensaje. Para obtener más información sobre los registros, vea [Obtener registros de compilación con MSBuild](../msbuild/obtaining-build-logs-with-msbuild.md).

 De forma predeterminada, el mensaje se envía al registrador de la consola de MSBuild. Esto se puede cambiar si se modifica el parámetro <xref:Microsoft.Build.Tasks.TaskExtension.Log%2A>. El registrador interpreta el parámetro `Importance`. Habitualmente, un mensaje establecido en `high` se envía cuando el detalle del registrador está establecido en <xref:Microsoft.Build.Framework.LoggerVerbosity>`Minimal` o superior. Cuando el detalle del registrador está establecido en <xref:Microsoft.Build.Framework.LoggerVerbosity>`Detailed`, se envía un mensaje establecido en `low`.

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