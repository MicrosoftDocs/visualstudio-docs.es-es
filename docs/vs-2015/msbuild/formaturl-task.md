---
title: Tarea FormatUrl | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
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
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: bb870bcc3c4297d5d1b403176f931f75e418d423
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "68149709"
---
# <a name="formaturl-task"></a>FormatUrl (Tarea)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Convierte una dirección URL en un formato de dirección URL correcto.  
  
## <a name="parameters"></a>Parámetros  
 En la siguiente tabla se describen los parámetros de la tarea `FormatUrl`.  
  
|Parámetro|Description|  
|---------------|-----------------|  
|`InputUrl`|Parámetro `String` opcional.<br /><br /> Especifica la dirección URL a la que se va a aplicar formato.|  
|`OutputUrl`|Parámetro de salida `String` opcional.<br /><br /> Especifica la dirección URL con formato.|  
  
## <a name="remarks"></a>Observaciones  
 Además de tener los parámetros que se enumeran en la tabla, esta tarea hereda los parámetros de la clase <xref:Microsoft.Build.Tasks.TaskExtension>, que a su vez hereda de la clase <xref:Microsoft.Build.Utilities.Task>. Para obtener una lista de estos parámetros adicionales y sus descripciones, vea [clase base TaskExtension](../msbuild/taskextension-base-class.md).  
  
## <a name="see-also"></a>Consulte también  
 [Tareas](../msbuild/msbuild-tasks.md)   
 [Referencia de tareas](../msbuild/msbuild-task-reference.md)
