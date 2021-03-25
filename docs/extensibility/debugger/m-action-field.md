---
description: Delegado que representa el código que se va a ejecutar en el objeto System. Threading. Tasks. Task.
title: m_action campo | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- m_action field, Task class [.NET Framework debug engines]
ms.assetid: 201838c2-260d-4071-b6c3-f526874e19c9
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: be180bf50c61869aab889c731e40d8d43ffb7300
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/25/2021
ms.locfileid: "105094658"
---
# <a name="m_action-field"></a>m_action campo
Delegado que representa el código que se va a ejecutar en el <xref:System.Threading.Tasks.Task> objeto.

 **Espacio de nombres:** <xref:System.Threading.Tasks?displayProperty=fullName>

 **Ensamblado:** mscorlib (en *mscorlib.dll*)

 Dado que no puede tener acceso a este miembro interno desde el .NET Framework, se proporciona la siguiente sintaxis en el lenguaje intermedio común (CIL).

## <a name="syntax"></a>Sintaxis

```csharp
.field assembly object m_action
```

## <a name="remarks"></a>Observaciones
 Este es el `action` parámetro del <xref:System.Threading.Tasks.Task.%23ctor%2A> constructor.

## <a name="see-also"></a>Consulte también
- [Clase de tarea: miembros internos](../../extensibility/debugger/task-class-internal-members.md)
