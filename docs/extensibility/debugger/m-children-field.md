---
title: m_children (campo) | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- m_children field, ContingentProperties class [.NET Framework debug engines]
ms.assetid: 0a3b5653-7bc0-4a7a-8963-9020bc52b9cb
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: fefeaf07c923a5fefa282efcd96948b2d907cca1
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62889518"
---
# <a name="mchildren-field"></a>m_children field
La lista de tareas secundarias que están registrados en esta tarea.

 **Espacio de nombres:** <xref:System.Threading.Tasks?displayProperty=fullName>

 **Ensamblado:** mscorlib (en *mscorlib.dll*)

 Dado que no se puede obtener acceso a este miembro interno de .NET Framework, la sintaxis siguiente se proporciona el lenguaje intermedio en común (CIL).

## <a name="syntax"></a>Sintaxis

```csharp
.field public class System.Collections.Generic.List`1<class System.Threading.Tasks.Task> m_children
```

## <a name="remarks"></a>Comentarios
 Mientras se ejecuta la tarea, sólo el subproceso que ejecuta la tarea debe tener acceso a esta matriz.

 Si la tarea se completa, otros subprocesos pueden tener acceso a este campo, siempre que no agrega nada a él o quitarle nada.

## <a name="see-also"></a>Vea también
- [Clase ContingentProperties](../../extensibility/debugger/contingentproperties-class-internal-members.md)