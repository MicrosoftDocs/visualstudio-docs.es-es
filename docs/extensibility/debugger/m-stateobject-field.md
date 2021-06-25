---
description: Objeto que representa los datos que usará la acción.
title: m_stateObject campo | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- m_stateObject field, Task class [.NET Framework debug engines]
ms.assetid: 68c54b22-3e1c-4031-b9c7-b972c519d8a0
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: df510fafbfe3ed6e71e9b5290fb1df0b02ae1d39
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/25/2021
ms.locfileid: "112903962"
---
# <a name="m_stateobject-field"></a>m_stateObject campo
Objeto que representa los datos que usará la acción.

 **Espacio de nombres:** <xref:System.Threading.Tasks?displayProperty=fullName>

 **Ensamblado:** mscorlib (en *mscorlib.dll*)

 Dado que no se puede acceder a este miembro interno desde la .NET Framework, se proporciona la sintaxis siguiente en Common Intermediate Language (CIL).

## <a name="syntax"></a>Sintaxis

```
.field assembly object m_stateObject
```

## <a name="remarks"></a>Observaciones
 Este es el `state` parámetro del <xref:System.Threading.Tasks.Task.%23ctor%2A> constructor. También es el campo de respaldo de la <xref:System.Threading.Tasks.Task.AsyncState%2A?displayProperty=fullName> propiedad .

## <a name="see-also"></a>Consulta también
- [Clase de tarea: miembros internos](../../extensibility/debugger/task-class-internal-members.md)
