---
description: La lista de tareas secundarias que se registran con esta tarea.
title: m_children campo | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- m_children field, ContingentProperties class [.NET Framework debug engines]
ms.assetid: 0a3b5653-7bc0-4a7a-8963-9020bc52b9cb
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 90394afd982f22977d3d3ed74850032bfb5634c8
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/25/2021
ms.locfileid: "105094697"
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

## <a name="see-also"></a>Consulte también
- [Clase ContingentProperties](../../extensibility/debugger/contingentproperties-class-internal-members.md)
