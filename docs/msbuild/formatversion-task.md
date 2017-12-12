---
title: Tarea FormatVersion | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- jsharp
ms.assetid: 96e692f6-b581-46ca-8cc9-441a1861e371
caps.latest.revision: "5"
author: kempb
ms.author: kempb
manager: ghogen
ms.openlocfilehash: c74b737febc0fd91286abd4e4c43c5f84b9e6452
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="formatversion-task"></a>FormatVersion (Tarea)
Anexa el número de revisión al número de versión.  
  
-   Caso 1: Input: Version=\<undefined>;  Revision=\<don't care>;   Output: OutputVersion="1.0.0.0"  
  
-   Caso 2: Input: Version="1.0.0.*"  Revision="5"  Output: OutputVersion="1.0.0.5"  
  
-   Caso 3: Input: Version="1.0.0.0"  Revision=\<don't care>;  Output: OutputVersion="1.0.0.0"  
  
## <a name="parameters"></a>Parámetros  
 En la siguiente tabla se describen los parámetros de la tarea `FormatVersion` .  
  
|Parámetro|Descripción|  
|---------------|-----------------|  
|`FormatType`|Parámetro `String` opcional.<br /><br /> Especifica el tipo de formato.<br /><br /> - "Version" = versión.<br />- "Path" = reemplace "." por "_";|  
|`OutputVersion`|Parámetro de salida `String` opcional.<br /><br /> Especifica la versión de salida que incluye el número de revisión.|  
|`Revision`|Parámetro `Int32` opcional.<br /><br /> Especifica la revisión que se va a anexar a la versión.|  
|`Version`|Parámetro `String` opcional.<br /><br /> Especifica la cadena de número de versión a la que se va a aplicar formato.|  
  
## <a name="remarks"></a>Comentarios  
 Además de tener los parámetros que se enumeran en la tabla, esta tarea hereda los parámetros de la clase <xref:Microsoft.Build.Tasks.TaskExtension>, que a su vez hereda de la clase <xref:Microsoft.Build.Utilities.Task>. Para obtener una lista de estos parámetros adicionales y sus descripciones, vea [TaskExtension Base Class](../msbuild/taskextension-base-class.md).  
  
## <a name="see-also"></a>Vea también  
 [Tareas](../msbuild/msbuild-tasks.md)   
 [Referencia de tareas](../msbuild/msbuild-task-reference.md)