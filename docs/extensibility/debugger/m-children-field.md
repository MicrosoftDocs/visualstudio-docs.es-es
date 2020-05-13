---
title: Campo de m_children Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- m_children field, ContingentProperties class [.NET Framework debug engines]
ms.assetid: 0a3b5653-7bc0-4a7a-8963-9020bc52b9cb
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 07933fd4c9f359e72714600abdf8b4ee29268f84
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738424"
---
# <a name="m_children-field"></a>campo m_children
La lista de tareas secundarias que se registran con esta tarea.

 **Espacio de nombres:**<xref:System.Threading.Tasks?displayProperty=fullName>

 **Ensamblado:** mscorlib (en *mscorlib.dll*)

 Dado que no se puede tener acceso a este miembro interno desde .NET Framework, se proporciona la sintaxis siguiente en Common Intermediate Language (CIL).

## <a name="syntax"></a>Sintaxis

```csharp
.field public class System.Collections.Generic.List`1<class System.Threading.Tasks.Task> m_children
```

## <a name="remarks"></a>Observaciones
 Mientras se ejecuta la tarea, solo el subproceso que ejecuta la tarea debe tener acceso a esta matriz.

 Si se completa la tarea, otros subprocesos pueden tener acceso a este campo siempre y cuando no le agreguen nada ni quiten nada de él.

## <a name="see-also"></a>Vea también
- [Clase ContingentProperties](../../extensibility/debugger/contingentproperties-class-internal-members.md)
