---
title: Tarea VCMessage | Microsoft Docs
description: Obtenga información sobre cómo MSBuild usa la tarea VCMessage para registrar mensajes de advertencia y de error durante una compilación de proyectos de C++.
ms.custom: SEO-VS-2020
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
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: c8db60044080726b61a02a59cad68d93f683e282
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99908825"
---
# <a name="vcmessage-task"></a>VCMessage (tarea)

Registra mensajes de advertencia y de error durante una compilación.

## <a name="remarks"></a>Comentarios

 Esta tarea ayuda a implementar MSBuild para proyectos de C++ y no está diseñada para que la llame el usuario. Para obtener más información, vea <xref:Microsoft.Build.Utilities.TaskLoggingHelper>.

## <a name="parameters"></a>Parámetros

 En la tabla siguiente se describen los parámetros de la tarea **VCMessage**.

|Parámetro|Description|
|---------------|-----------------|
|**Argumentos**|Parámetro **String** opcional.<br /><br /> Lista delimitada por punto y coma de los mensajes que se van a mostrar.|
|**Código**|Parámetro obligatorio de tipo **String**.<br /><br /> Número de error que califica el mensaje.|
|**Tipo**|Parámetro **String** opcional.<br /><br /> Especifica el tipo de mensaje que se va a emitir. Especifique "Warning" para emitir un mensaje de advertencia o "Error" para emitir un mensaje de error.|

## <a name="see-also"></a>Vea también

- [Referencia de tareas](../msbuild/msbuild-task-reference.md)
