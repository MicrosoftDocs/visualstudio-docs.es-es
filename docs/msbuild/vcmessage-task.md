---
title: Tarea VCMessage | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vc.task.vcmessage
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
caps.latest.revision: "7"
author: kempb
ms.author: kempb
manager: ghogen
ms.openlocfilehash: 16ed7f4207a65915afbf18a496a0152e04e9a8d0
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="vcmessage-task"></a>VCMessage (Tarea)
Registra mensajes de advertencia y de error durante una compilación.  
  
## <a name="remarks"></a>Comentarios  
 Esta tarea ayuda a implementar MSBuild para Visual C++ y no está diseñada para que la llame el usuario. Para obtener más información, consulta <xref:Microsoft.Build.Utilities.TaskLoggingHelper>.  
  
## <a name="parameters"></a>Parámetros  
 En la tabla siguiente se describen los parámetros de la tarea **VCMessage**.  
  
|Parámetro|Descripción|  
|---------------|-----------------|  
|**Argumentos**|Parámetro **String** opcional.<br /><br /> Lista delimitada por punto y coma de los mensajes que se van a mostrar.|  
|**Código**|Parámetro obligatorio de tipo **String**.<br /><br /> Número de error que califica el mensaje.|  
|**ype**|Parámetro **String** opcional.<br /><br /> Especifica el tipo de mensaje que se va a emitir. Especifique `"Warning"` para emitir un mensaje de advertencia o `"Error"` para emitir un mensaje de error.|  
  
## <a name="see-also"></a>Vea también  
 [Referencia de tareas](../msbuild/msbuild-task-reference.md)