---
title: m_stateObject campo | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- m_stateObject field, Task class [.NET Framework debug engines]
ms.assetid: 68c54b22-3e1c-4031-b9c7-b972c519d8a0
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: bbf16af65ab59147614ce5609de9b56ff833862a
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99925131"
---
# <a name="m_stateobject-field"></a>m_stateObject campo
Objeto que representa los datos que utilizará la acción.

 **Espacio de nombres:** <xref:System.Threading.Tasks?displayProperty=fullName>

 **Ensamblado:** mscorlib (en *mscorlib.dll*)

 Dado que no puede tener acceso a este miembro interno desde el .NET Framework, se proporciona la siguiente sintaxis en el lenguaje intermedio común (CIL).

## <a name="syntax"></a>Sintaxis

```
.field assembly object m_stateObject
```

## <a name="remarks"></a>Observaciones
 Este es el `state` parámetro del <xref:System.Threading.Tasks.Task.%23ctor%2A> constructor. También es el campo de respaldo de la <xref:System.Threading.Tasks.Task.AsyncState%2A?displayProperty=fullName> propiedad.

## <a name="see-also"></a>Vea también
- [Clase de tarea: miembros internos](../../extensibility/debugger/task-class-internal-members.md)
