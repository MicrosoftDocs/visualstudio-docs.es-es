---
description: Contiene propiedades adicionales para un objeto System. Threading. Tasks. Task.
title: 'Clase ContingentProperties: miembros internos | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- ContingentProperties class [.NET Framework debug engines]
- debug engines, ContingentProperties class [.NET Framework]
ms.assetid: c49d1362-ab1c-4b6d-9950-fcae40e0e66b
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 2303318c7a5f36027ce7709c5b09b5846fc6fab6
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/05/2021
ms.locfileid: "102154982"
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

## <a name="members"></a>Members

### <a name="fields"></a>Campos

|Nombre|Descripción|
|----------|-----------------|
|[m_children](../../extensibility/debugger/m-children-field.md)|La lista de tareas secundarias que se registran con esta tarea.|

## <a name="remarks"></a>Observaciones
 El .NET Framework inicializa los campos de esta clase solo cuando son necesarios.

## <a name="see-also"></a>Consulte también
- [Interna de la extensión paralela para el .NET Framework](../../extensibility/debugger/parallel-extension-internals-for-the-dotnet-framework.md)
