---
title: m_stateObject campo | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: m_stateObject field, Task class [.NET Framework debug engines]
ms.assetid: 68c54b22-3e1c-4031-b9c7-b972c519d8a0
caps.latest.revision: "13"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 85e8648fd757c6cdb7910123b3cd861f7abb3371
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="mstateobject-field"></a>m_stateObject campo
Objeto que representa los datos que se va a usar la acción.  
  
 **Namespace:**<xref:System.Threading.Tasks?displayProperty=fullName>  
  
 **Ensamblado:** mscorlib (en mscorlib.dll)  
  
 Dado que no se puede obtener acceso a este miembro interno de .NET Framework, la sintaxis siguiente se proporciona el lenguaje intermedio común (CIL).  
  
## <a name="syntax"></a>Sintaxis  
  
```  
.field assembly object m_stateObject  
```  
  
## <a name="remarks"></a>Comentarios  
 Se trata de la `state` parámetro en el <xref:System.Threading.Tasks.Task.%23ctor%2A> constructor. También es el campo de respaldo para la <xref:System.Threading.Tasks.Task.AsyncState%2A?displayProperty=fullName> propiedad.  
  
## <a name="see-also"></a>Vea también  
 [Clase de tarea](../../extensibility/debugger/task-class-internal-members.md)