---
description: En este tema se describen los miembros internos de la clase System. Runtime. CompilerServices. AsyncVoidMethodBuilder.
title: 'Estructura AsyncVoidMethodBuilder: miembros internos | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debug engines, AsyncVoidMethodBuilder structure [.NET Framework]
- AsyncVoidMethodBuilder structure [.NET Framework debug engines]
ms.assetid: fe2970ab-d4c5-4355-a8e4-772ee0a57178
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: ad209fb94a9857fe0596f1e25b0dec844d03ca8f
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/05/2021
ms.locfileid: "102151149"
---
# <a name="asyncvoidmethodbuilder-structure---internal-members"></a>Estructura AsyncVoidMethodBuilder: miembros internos
En este tema se describen los miembros internos de la <xref:System.Runtime.CompilerServices.AsyncVoidMethodBuilder> clase. Para obtener información general sobre esta clase, vea el <xref:System.Runtime.CompilerServices.AsyncVoidMethodBuilder> tema de referencia.

 **Espacio de nombres:** <xref:System.Runtime.CompilerServices?displayProperty=fullName>

 **Ensamblado:** mscorlib (en mscorlib.dll)

 Dado que no puede tener acceso a estos miembros internos desde el .NET Framework, se proporciona la siguiente sintaxis en el lenguaje intermedio común (CIL).

## <a name="syntax"></a>Syntax

```csharp
.class public sequential ansi sealed beforefieldinit System.Runtime.CompilerServices.AsyncVoidMethodBuilder
       extends System.ValueType
       implements System.Runtime.CompilerServices.IAsyncMethodBuilder
```

## <a name="internal-members"></a>Miembros internos

|Nombre|Descripción|
|----------|-----------------|
|[Propiedad Objectidfordebugger (](../../extensibility/debugger/asyncvoidmethodbuilder-objectidfordebugger-property.md)|Obtiene un objeto que se puede usar para identificar de forma única este generador en el depurador.|
|[m_objectIdForDebugger campo](../../extensibility/debugger/asyncvoidmethodbuilder-m-objectidfordebugger-field.md)|Representa el objeto inicializado de forma diferida que usa el depurador para identificar de forma exclusiva a este generador.|

## <a name="see-also"></a>Consulte también
- <xref:System.Runtime.CompilerServices.AsyncVoidMethodBuilder>
- [Interna de la extensión paralela para el .NET Framework](../../extensibility/debugger/parallel-extension-internals-for-the-dotnet-framework.md)
