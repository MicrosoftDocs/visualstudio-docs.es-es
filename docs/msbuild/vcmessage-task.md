---
title: Tarea VCMessage | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: msbuild
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vc.task.vcmessage
dev_langs:
- VB
- CSharp
- C++
- jsharp
- C++
helpviewer_keywords:
- VCMessage task (MSBuild (Visual C++))
- MSBuild (Visual C++), VCMessage task
ms.assetid: 956675fd-05dc-40b4-856f-616145103498
caps.latest.revision: 
author: Mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 8f3ec9c3b41d7ef8bffaa1dd1c607cd39610143b
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/09/2018
---
# <a name="vcmessage-task"></a>VCMessage (Tarea)
Registra mensajes de advertencia y de error durante una compilación.  
  
## <a name="remarks"></a>Comentarios  
 Esta tarea ayuda a implementar MSBuild para Visual C++ y no está diseñada para que la llame el usuario. Para obtener más información, consulta <xref:Microsoft.Build.Utilities.TaskLoggingHelper>.  
  
## <a name="parameters"></a>Parámetros  
 En la tabla siguiente se describen los parámetros de la tarea **VCMessage**.  
  
|Parámetro|Description|  
|---------------|-----------------|  
|**Argumentos**|Parámetro **String** opcional.<br /><br /> Lista delimitada por punto y coma de los mensajes que se van a mostrar.|  
|**Código**|Parámetro obligatorio de tipo **String**.<br /><br /> Número de error que califica el mensaje.|  
|**Type**|Parámetro **String** opcional.<br /><br /> Especifica el tipo de mensaje que se va a emitir. Especifique `"Warning"` para emitir un mensaje de advertencia o `"Error"` para emitir un mensaje de error.|  
  
## <a name="see-also"></a>Vea también  
 [Referencia de tareas](../msbuild/msbuild-task-reference.md)