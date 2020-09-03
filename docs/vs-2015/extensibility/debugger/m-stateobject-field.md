---
title: m_stateObject campo | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- m_stateObject field, Task class [.NET Framework debug engines]
ms.assetid: 68c54b22-3e1c-4031-b9c7-b972c519d8a0
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 8e9cfc6f689504bef2a8366f90282641d1e9e105
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "68149052"
---
# <a name="m_stateobject-field"></a>m_stateObject (Campo)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Objeto que representa los datos que utilizará la acción.  
  
 **Espacio de nombres:** <xref:System.Threading.Tasks?displayProperty=fullName>  
  
 **Ensamblado:** mscorlib (en mscorlib.dll)  
  
 Dado que no puede tener acceso a este miembro interno desde el .NET Framework, se proporciona la siguiente sintaxis en el lenguaje intermedio común (CIL).  
  
## <a name="syntax"></a>Sintaxis  
  
```  
.field assembly object m_stateObject  
```  
  
## <a name="remarks"></a>Comentarios  
 Este es el `state` parámetro del <xref:System.Threading.Tasks.Task.%23ctor%2A> constructor. También es el campo de respaldo de la <xref:System.Threading.Tasks.Task.AsyncState%2A?displayProperty=fullName> propiedad.  
  
## <a name="see-also"></a>Consulte también  
 [Task (clase)](../../extensibility/debugger/task-class-internal-members.md)
