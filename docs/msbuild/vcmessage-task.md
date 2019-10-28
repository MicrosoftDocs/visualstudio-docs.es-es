---
title: Tarea VCMessage | Microsoft Docs
ms.date: 06/27/2018
ms.topic: reference
f1_keywords:
- vc.task.vcmessage
dev_langs:
- VB
- CSharp
- C++
- jsharp
- C++
helpviewer_keywords:
- VCMessage task (MSBuild (C++))
- MSBuild (C++), VCMessage task
ms.assetid: 956675fd-05dc-40b4-856f-616145103498
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: be4f963a5944882f14118be54e498fd4712c2e46
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/22/2019
ms.locfileid: "72747185"
---
# <a name="vcmessage-task"></a>VCMessage (tarea)
Registra mensajes de advertencia y de error durante una compilación.

## <a name="remarks"></a>Comentarios
 Esta tarea ayuda a implementar MSBuild para proyectos de C++ y no está diseñada para que la llame el usuario. Para más información, consulte <xref:Microsoft.Build.Utilities.TaskLoggingHelper>.

## <a name="parameters"></a>Parámetros
 En la tabla siguiente se describen los parámetros de la tarea **VCMessage**.

|Parámetro|DESCRIPCIÓN|
|---------------|-----------------|
|**Argumentos**|Parámetro **String** opcional.<br /><br /> Lista delimitada por punto y coma de los mensajes que se van a mostrar.|
|**Código**|Parámetro obligatorio de tipo **String**.<br /><br /> Número de error que califica el mensaje.|
|**Type**|Parámetro **String** opcional.<br /><br /> Especifica el tipo de mensaje que se va a emitir. Especifique "Warning" para emitir un mensaje de advertencia o "Error" para emitir un mensaje de error.|

## <a name="see-also"></a>Vea también
- [Referencia de tareas](../msbuild/msbuild-task-reference.md)