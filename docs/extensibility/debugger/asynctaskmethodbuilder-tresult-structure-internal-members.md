---
title: 'AsyncTaskMethodBuilder &lt; TResult &gt; (estructura): miembros internos | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- AsyncTaskMethodBuilder<TResult> structure [.NET Framework debug engines]
- debug engines, AsyncTaskMethodBuilder<TResult> structure [.NET Framework]
ms.assetid: 17ebc340-8170-4aff-bf54-dc4548c83632
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 41cb409495b28b7dc2bc796859da413a32b90d85
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99921627"
---
# <a name="asynctaskmethodbuilderlttresultgt-structure---internal-members"></a>AsyncTaskMethodBuilder &lt; TResult &gt; (estructura): miembros internos
En este tema se describen los miembros internos de la <xref:System.Runtime.CompilerServices.AsyncTaskMethodBuilder%601> clase. Para obtener información general sobre esta clase, vea el <xref:System.Runtime.CompilerServices.AsyncTaskMethodBuilder%601> tema de referencia.

 **Espacio de nombres:** <xref:System.Runtime.CompilerServices?displayProperty=fullName>

 **Ensamblado:** mscorlib (en mscorlib.dll)

 Dado que no puede tener acceso a estos miembros internos desde el .NET Framework, se proporciona la siguiente sintaxis en el lenguaje intermedio común (CIL).

## <a name="syntax"></a>Sintaxis

```csharp
.class public sequential ansi sealed beforefieldinit System.Runtime.CompilerServices.AsyncTaskMethodBuilder`1<TResult>
       extends System.ValueType
       implements System.Runtime.CompilerServices.IAsyncMethodBuilder
```

## <a name="internal-members"></a>Miembros internos

|Nombre|Descripción|
|----------|-----------------|
|[Propiedad Objectidfordebugger (](../../extensibility/debugger/asynctaskmethodbuilder-tresult-objectidfordebugger-property.md)|Obtiene un objeto que se puede usar para identificar de forma única este generador en el depurador.|
|[m_task campo](../../extensibility/debugger/asynctaskmethodbuilder-tresult-m-task-field.md)|Representa la tarea compilada que se ha inicializado de forma diferida.|

## <a name="see-also"></a>Vea también
- <xref:System.Runtime.CompilerServices.AsyncTaskMethodBuilder%601>
- [Interna de la extensión paralela para el .NET Framework](../../extensibility/debugger/parallel-extension-internals-for-the-dotnet-framework.md)
