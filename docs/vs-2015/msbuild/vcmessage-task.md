---
title: Tarea VCMessage | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
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
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d667c53e00e7b92d133c260b5c3cc471a64f355b
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "47575784"
---
# <a name="vcmessage-task"></a>VCMessage (Tarea)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versión más reciente de este tema puede encontrarse en [VCMessage (tarea)](https://docs.microsoft.com/visualstudio/msbuild/vcmessage-task).  
  
  
Registra mensajes de advertencia y de error durante una compilación.  
  
## <a name="remarks"></a>Comentarios  
 Esta tarea ayuda a implementar MSBuild para Visual C++ y no está diseñada para que la llame el usuario. Para obtener más información, consulta <xref:Microsoft.Build.Utilities.TaskLoggingHelper>.  
  
## <a name="parameters"></a>Parámetros  
 En la tabla siguiente se describen los parámetros de la tarea **VCMessage**.  
  
|Parámetro|Descripción|  
|---------------|-----------------|  
|**Argumentos**|Parámetro **String** opcional.<br /><br /> Lista delimitada por punto y coma de los mensajes que se van a mostrar.|  
|**Código**|Parámetro obligatorio de tipo **String**.<br /><br /> Número de error que califica el mensaje.|  
|**Type**|Parámetro **String** opcional.<br /><br /> Especifica el tipo de mensaje que se va a emitir. Especifique `"Warning"` para emitir un mensaje de advertencia o `"Error"` para emitir un mensaje de error.|  
  
## <a name="see-also"></a>Vea también  
 [Referencia de tareas](../msbuild/msbuild-task-reference.md)



