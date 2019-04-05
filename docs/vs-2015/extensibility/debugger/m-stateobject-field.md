---
title: m_stateObject (campo) | Microsoft Docs
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
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/23/2019
ms.locfileid: "58987662"
---
# <a name="mstateobject-field"></a>m_stateObject (Campo)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Objeto que representa los datos que se va a usar la acción.  
  
 **Espacio de nombres:** <xref:System.Threading.Tasks?displayProperty=fullName>  
  
 **Ensamblado:** mscorlib (en mscorlib.dll)  
  
 Dado que no se puede obtener acceso a este miembro interno de .NET Framework, la sintaxis siguiente se proporciona el lenguaje intermedio en común (CIL).  
  
## <a name="syntax"></a>Sintaxis  
  
```  
.field assembly object m_stateObject  
```  
  
## <a name="remarks"></a>Comentarios  
 Se trata de la `state` parámetro en el <xref:System.Threading.Tasks.Task.%23ctor%2A> constructor. También es el campo de respaldo para el <xref:System.Threading.Tasks.Task.AsyncState%2A?displayProperty=fullName> propiedad.  
  
## <a name="see-also"></a>Vea también  
 [Clase Task](../../extensibility/debugger/task-class-internal-members.md)
