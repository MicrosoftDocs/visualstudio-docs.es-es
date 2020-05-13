---
title: Estructura AsyncTaskMethodBuilder - Miembros internos ? Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debug engines, AsyncTaskMethodBuilder structure [.NET Framework]
- AsyncTaskMethodBuilder structure [.NET Framework debug engines]
ms.assetid: f32f5857-7ef8-45fd-8b5a-7f644eb98b11
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c918890551515ab9fadbf329d4c3ee96621c7aae
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739375"
---
# <a name="asynctaskmethodbuilder-structure---internal-members"></a>Estructura AsyncTaskMethodBuilder - miembros internos
En este tema se describen los miembros internos de la <xref:System.Runtime.CompilerServices.AsyncTaskMethodBuilder> clase. Para obtener información general sobre <xref:System.Runtime.CompilerServices.AsyncTaskMethodBuilder> esta clase, consulte el tema de referencia.

 **Espacio de nombres:**<xref:System.Runtime.CompilerServices?displayProperty=fullName>

 **Ensamblado:** mscorlib (en mscorlib.dll)

 Dado que no puede tener acceso a estos miembros internos desde .NET Framework, se proporciona la sintaxis siguiente en Common Intermediate Language (CIL).

## <a name="syntax"></a>Sintaxis

```csharp
.class public sequential ansi sealed beforefieldinit System.Runtime.CompilerServices.AsyncTaskMethodBuilder
       extends System.ValueType
       implements System.Runtime.CompilerServices.IAsyncMethodBuilder
```

## <a name="internal-members"></a>Miembros internos

|Nombre|Descripción|
|----------|-----------------|
|[Propiedad ObjectIdForDebugger](../../extensibility/debugger/asynctaskmethodbuilder-objectidfordebugger-property.md)|Obtiene un objeto que se puede usar para identificar de forma única este generador en el depurador.|
|[m_builder campo](../../extensibility/debugger/asynctaskmethodbuilder-m-builder-field.md)|Representa el objeto de generador genérico al que se delega esta instancia no genérica.|

## <a name="see-also"></a>Vea también
- <xref:System.Runtime.CompilerServices.AsyncTaskMethodBuilder>
- [Internos de extensión paralela para .NET Framework](../../extensibility/debugger/parallel-extension-internals-for-the-dotnet-framework.md)
