---
title: Clase ContingentProperties - Miembros internos ? Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- ContingentProperties class [.NET Framework debug engines]
- debug engines, ContingentProperties class [.NET Framework]
ms.assetid: c49d1362-ab1c-4b6d-9950-fcae40e0e66b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c6441cafcc34a06464061b41691ea5faa32fc359
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739100"
---
# <a name="contingentproperties-class---internal-members"></a>Clase ContingentProperties - miembros internos
Contiene propiedades adicionales <xref:System.Threading.Tasks.Task> para un objeto.

 **Espacio de nombres:**<xref:System.Threading.Tasks?displayProperty=fullName>

 **Ensamblado:** mscorlib (en mscorlib.dll)

 Dado que no puede tener acceso a estos miembros internos desde .NET Framework, se proporciona la sintaxis siguiente en Common Intermediate Language (CIL).

## <a name="syntax"></a>Sintaxis

```csharp
.class auto ansi nested assembly beforefieldinit ContingentProperties
       extends System.Object
```

## <a name="members"></a>Miembros

### <a name="fields"></a>Fields

|Nombre|Descripción|
|----------|-----------------|
|[m_children](../../extensibility/debugger/m-children-field.md)|La lista de tareas secundarias que se registran con esta tarea.|

## <a name="remarks"></a>Observaciones
 .NET Framework inicializa los campos de esta clase solo cuando son necesarios.

## <a name="see-also"></a>Vea también
- [Internos de extensión paralela para .NET Framework](../../extensibility/debugger/parallel-extension-internals-for-the-dotnet-framework.md)
