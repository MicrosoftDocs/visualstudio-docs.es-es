---
description: Objeto que representa los datos que utilizará la acción.
title: m_stateObject campo | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- m_stateObject field, Task class [.NET Framework debug engines]
ms.assetid: 68c54b22-3e1c-4031-b9c7-b972c519d8a0
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: c2128073f47c76244a18e18005a431f9317686c3
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/25/2021
ms.locfileid: "105054795"
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

## <a name="see-also"></a>Consulte también
- [Clase de tarea: miembros internos](../../extensibility/debugger/task-class-internal-members.md)
