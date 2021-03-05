---
description: Delegado que representa el código que se va a ejecutar en el objeto System. Threading. Tasks. Task.
title: m_action campo | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- m_action field, Task class [.NET Framework debug engines]
ms.assetid: 201838c2-260d-4071-b6c3-f526874e19c9
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 8e23baa6682d478c825ce443009e499e2619dd94
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/05/2021
ms.locfileid: "102145500"
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
