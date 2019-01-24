---
title: m_stateObject (campo) | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- m_stateObject field, Task class [.NET Framework debug engines]
ms.assetid: 68c54b22-3e1c-4031-b9c7-b972c519d8a0
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 7fbd5404f7138fd2f98d56d63089acdb2afdad9f
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/02/2019
ms.locfileid: "53850208"
---
# <a name="mstateobject-field"></a>m_stateObject campo
Objeto que representa los datos que se va a usar la acción.  
  
 **Espacio de nombres:** <xref:System.Threading.Tasks?displayProperty=fullName>  
  
 **Ensamblado:** mscorlib (en *mscorlib.dll*)  
  
 Dado que no se puede obtener acceso a este miembro interno de .NET Framework, la sintaxis siguiente se proporciona el lenguaje intermedio en común (CIL).  
  
## <a name="syntax"></a>Sintaxis  
  
```  
.field assembly object m_stateObject  
```  
  
## <a name="remarks"></a>Comentarios  
 Se trata de la `state` parámetro en el <xref:System.Threading.Tasks.Task.%23ctor%2A> constructor. También es el campo de respaldo para el <xref:System.Threading.Tasks.Task.AsyncState%2A?displayProperty=fullName> propiedad.  
  
## <a name="see-also"></a>Vea también  
 [Clase de tarea: miembros internos](../../extensibility/debugger/task-class-internal-members.md)