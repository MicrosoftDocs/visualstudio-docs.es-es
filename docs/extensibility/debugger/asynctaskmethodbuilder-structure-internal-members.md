---
description: En este artículo se describen los miembros internos de la clase System.Runtime.CompilerServices.AsyncTaskMethodBuilder.
title: 'AsyncTaskMethodBuilder (Estructura): miembros internos'
titleSuffix: ''
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- debug engines, AsyncTaskMethodBuilder structure [.NET Framework]
- AsyncTaskMethodBuilder structure [.NET Framework debug engines]
ms.assetid: f32f5857-7ef8-45fd-8b5a-7f644eb98b11
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: c5b21045688fc2be555c7a42d6e3b9014b66c761
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/25/2021
ms.locfileid: "112903845"
---
# <a name="asynctaskmethodbuilder-structure---internal-members"></a>Estructura AsyncTaskMethodBuilder: miembros internos
En este tema se describen los miembros internos de la <xref:System.Runtime.CompilerServices.AsyncTaskMethodBuilder> clase . Para obtener información general sobre esta clase, vea el <xref:System.Runtime.CompilerServices.AsyncTaskMethodBuilder> tema de referencia.

 **Espacio de nombres:** <xref:System.Runtime.CompilerServices?displayProperty=fullName>

 **Ensamblado:** mscorlib (en mscorlib.dll)

 Dado que no se puede acceder a estos miembros internos desde .NET Framework, se proporciona la sintaxis siguiente en Common Intermediate Language (CIL).

## <a name="syntax"></a>Sintaxis

```csharp
.class public sequential ansi sealed beforefieldinit System.Runtime.CompilerServices.AsyncTaskMethodBuilder
       extends System.ValueType
       implements System.Runtime.CompilerServices.IAsyncMethodBuilder
```

## <a name="internal-members"></a>Miembros internos

|Nombre|Descripción|
|----------|-----------------|
|[Propiedad ObjectIdForDebugger](../../extensibility/debugger/asynctaskmethodbuilder-objectidfordebugger-property.md)|Obtiene un objeto que se puede usar para identificar de forma única este generador para el depurador.|
|[m_builder campo](../../extensibility/debugger/asynctaskmethodbuilder-m-builder-field.md)|Representa el objeto de generador genérico al que delega esta instancia no genérica.|

## <a name="see-also"></a>Consulta también
- <xref:System.Runtime.CompilerServices.AsyncTaskMethodBuilder>
- [Interno de la extensión en paralelo para el .NET Framework](../../extensibility/debugger/parallel-extension-internals-for-the-dotnet-framework.md)
