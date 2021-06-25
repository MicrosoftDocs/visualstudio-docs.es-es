---
description: Contiene propiedades adicionales para un objeto System.Threading.Tasks.Task.
title: 'Clase ContingentProperties: miembros internos | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- ContingentProperties class [.NET Framework debug engines]
- debug engines, ContingentProperties class [.NET Framework]
ms.assetid: c49d1362-ab1c-4b6d-9950-fcae40e0e66b
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 8fca0bf68de4493d0165f9e66e251945ba6168b2
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/25/2021
ms.locfileid: "112905688"
---
# <a name="contingentproperties-class---internal-members"></a>Clase ContingentProperties: miembros internos
Contiene propiedades adicionales para un <xref:System.Threading.Tasks.Task> objeto .

 **Espacio de nombres:** <xref:System.Threading.Tasks?displayProperty=fullName>

 **Ensamblado:** mscorlib (en mscorlib.dll)

 Dado que no se puede acceder a estos miembros internos desde .NET Framework, se proporciona la sintaxis siguiente en Common Intermediate Language (CIL).

## <a name="syntax"></a>Sintaxis

```csharp
.class auto ansi nested assembly beforefieldinit ContingentProperties
       extends System.Object
```

## <a name="members"></a>Miembros

### <a name="fields"></a>Campos

|Nombre|Descripción|
|----------|-----------------|
|[m_children](../../extensibility/debugger/m-children-field.md)|Lista de tareas secundarias registradas con esta tarea.|

## <a name="remarks"></a>Observaciones
 El .NET Framework inicializa los campos de esta clase solo cuando son necesarios.

## <a name="see-also"></a>Consulta también
- [Interno de la extensión en paralelo para el .NET Framework](../../extensibility/debugger/parallel-extension-internals-for-the-dotnet-framework.md)
