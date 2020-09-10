---
title: 'AsyncTaskMethodBuilder (Estructura): miembros internos'
titleSuffix: ''
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
ms.openlocfilehash: 032bac9fc4eabccc2368d0b0403ce97a43b7966c
ms.sourcegitcommit: 2a201c93ed526b0f7e5848657500f1111b08ac2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/10/2020
ms.locfileid: "89741631"
---
# <a name="asynctaskmethodbuilder-structure---internal-members"></a>Estructura AsyncTaskMethodBuilder: miembros internos
En este tema se describen los miembros internos de la <xref:System.Runtime.CompilerServices.AsyncTaskMethodBuilder> clase. Para obtener información general sobre esta clase, vea el <xref:System.Runtime.CompilerServices.AsyncTaskMethodBuilder> tema de referencia.

 **Espacio de nombres:** <xref:System.Runtime.CompilerServices?displayProperty=fullName>

 **Ensamblado:** mscorlib (en mscorlib.dll)

 Dado que no puede tener acceso a estos miembros internos desde el .NET Framework, se proporciona la siguiente sintaxis en el lenguaje intermedio común (CIL).

## <a name="syntax"></a>Sintaxis

```csharp
.class public sequential ansi sealed beforefieldinit System.Runtime.CompilerServices.AsyncTaskMethodBuilder
       extends System.ValueType
       implements System.Runtime.CompilerServices.IAsyncMethodBuilder
```

## <a name="internal-members"></a>Miembros internos

|Nombre|Descripción|
|----------|-----------------|
|[Propiedad Objectidfordebugger (](../../extensibility/debugger/asynctaskmethodbuilder-objectidfordebugger-property.md)|Obtiene un objeto que se puede usar para identificar de forma única este generador en el depurador.|
|[m_builder campo](../../extensibility/debugger/asynctaskmethodbuilder-m-builder-field.md)|Representa el objeto de generador genérico en el que esta instancia no genérica delega.|

## <a name="see-also"></a>Vea también
- <xref:System.Runtime.CompilerServices.AsyncTaskMethodBuilder>
- [Interna de la extensión paralela para el .NET Framework](../../extensibility/debugger/parallel-extension-internals-for-the-dotnet-framework.md)
