---
description: Contiene propiedades adicionales para un objeto System. Threading. Tasks. Task.
title: 'Clase ContingentProperties: miembros internos | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- ContingentProperties class [.NET Framework debug engines]
- debug engines, ContingentProperties class [.NET Framework]
ms.assetid: c49d1362-ab1c-4b6d-9950-fcae40e0e66b
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 295b8c3b33059811e665e362c9894103b47c422d
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/25/2021
ms.locfileid: "105055003"
---
# <a name="contingentproperties-class---internal-members"></a>Clase ContingentProperties: miembros internos
Contiene propiedades adicionales para un <xref:System.Threading.Tasks.Task> objeto.

 **Espacio de nombres:** <xref:System.Threading.Tasks?displayProperty=fullName>

 **Ensamblado:** mscorlib (en mscorlib.dll)

 Dado que no puede tener acceso a estos miembros internos desde el .NET Framework, se proporciona la siguiente sintaxis en el lenguaje intermedio común (CIL).

## <a name="syntax"></a>Sintaxis

```csharp
.class auto ansi nested assembly beforefieldinit ContingentProperties
       extends System.Object
```

## <a name="members"></a>Miembros

### <a name="fields"></a>Campos

|Nombre|Descripción|
|----------|-----------------|
|[m_children](../../extensibility/debugger/m-children-field.md)|La lista de tareas secundarias que se registran con esta tarea.|

## <a name="remarks"></a>Observaciones
 El .NET Framework inicializa los campos de esta clase solo cuando son necesarios.

## <a name="see-also"></a>Consulte también
- [Interna de la extensión paralela para el .NET Framework](../../extensibility/debugger/parallel-extension-internals-for-the-dotnet-framework.md)
