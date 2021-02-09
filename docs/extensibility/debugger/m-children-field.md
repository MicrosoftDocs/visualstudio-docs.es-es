---
title: m_children campo | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- m_children field, ContingentProperties class [.NET Framework debug engines]
ms.assetid: 0a3b5653-7bc0-4a7a-8963-9020bc52b9cb
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 12bf76c5c9b62184a74006ddf288c7e581215ce0
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99925278"
---
# <a name="m_children-field"></a>m_children campo
La lista de tareas secundarias que se registran con esta tarea.

 **Espacio de nombres:** <xref:System.Threading.Tasks?displayProperty=fullName>

 **Ensamblado:** mscorlib (en *mscorlib.dll*)

 Dado que no puede tener acceso a este miembro interno desde el .NET Framework, se proporciona la siguiente sintaxis en el lenguaje intermedio común (CIL).

## <a name="syntax"></a>Sintaxis

```csharp
.field public class System.Collections.Generic.List`1<class System.Threading.Tasks.Task> m_children
```

## <a name="remarks"></a>Observaciones
 Mientras se ejecuta la tarea, solo el subproceso que ejecuta la tarea debe tener acceso a esta matriz.

 Si se completa la tarea, otros subprocesos pueden tener acceso a este campo siempre y cuando no agreguen nada o quiten nada de él.

## <a name="see-also"></a>Vea también
- [Clase ContingentProperties](../../extensibility/debugger/contingentproperties-class-internal-members.md)
