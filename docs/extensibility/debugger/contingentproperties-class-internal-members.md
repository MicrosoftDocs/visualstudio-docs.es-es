---
title: 'ContingentProperties Class: miembros internos | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- ContingentProperties class [.NET Framework debug engines]
- debug engines, ContingentProperties class [.NET Framework]
ms.assetid: c49d1362-ab1c-4b6d-9950-fcae40e0e66b
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 60129950c2311cc94b8573de4cd8ae3c46194e75
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62926003"
---
# <a name="contingentproperties-class---internal-members"></a>ContingentProperties class: miembros internos
Contiene propiedades adicionales para un <xref:System.Threading.Tasks.Task> objeto.

 **Espacio de nombres:** <xref:System.Threading.Tasks?displayProperty=fullName>

 **Ensamblado:** mscorlib (en mscorlib.dll)

 Dado que no se puede obtener acceso a estos miembros internos de .NET Framework, la sintaxis siguiente se proporciona el lenguaje intermedio en común (CIL).

## <a name="syntax"></a>Sintaxis

```csharp
.class auto ansi nested assembly beforefieldinit ContingentProperties
       extends System.Object
```

## <a name="members"></a>Miembros

### <a name="fields"></a>Campos

|Name|Descripción|
|----------|-----------------|
|[m_children](../../extensibility/debugger/m-children-field.md)|La lista de tareas secundarias que están registrados en esta tarea.|

## <a name="remarks"></a>Comentarios
 .NET Framework inicializa los campos de esta clase solo cuando sean necesarios.

## <a name="see-also"></a>Vea también
- [Parámetros internos de extensiones paralelas para .NET Framework](../../extensibility/debugger/parallel-extension-internals-for-the-dotnet-framework.md)