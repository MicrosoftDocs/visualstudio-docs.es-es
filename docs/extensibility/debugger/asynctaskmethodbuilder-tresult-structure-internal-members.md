---
title: 'AsyncTaskMethodBuilder&lt;TResult&gt; Structure: miembros internos | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- AsyncTaskMethodBuilder<TResult> structure [.NET Framework debug engines]
- debug engines, AsyncTaskMethodBuilder<TResult> structure [.NET Framework]
ms.assetid: 17ebc340-8170-4aff-bf54-dc4548c83632
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c944671b3bdb42f72928822903ccb05742401f7e
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/29/2019
ms.locfileid: "66350968"
---
# <a name="asynctaskmethodbuilderlttresultgt-structure---internal-members"></a>AsyncTaskMethodBuilder&lt;TResult&gt; estructura - miembros internos
En este tema se describe los miembros internos de la <xref:System.Runtime.CompilerServices.AsyncTaskMethodBuilder%601> clase. Para obtener información general acerca de esta clase, vea el <xref:System.Runtime.CompilerServices.AsyncTaskMethodBuilder%601> tema de referencia.

 **Espacio de nombres:** <xref:System.Runtime.CompilerServices?displayProperty=fullName>

 **Ensamblado:** mscorlib (en mscorlib.dll)

 Dado que no se puede obtener acceso a estos miembros internos de .NET Framework, la sintaxis siguiente se proporciona el lenguaje intermedio en común (CIL).

## <a name="syntax"></a>Sintaxis

```csharp
.class public sequential ansi sealed beforefieldinit System.Runtime.CompilerServices.AsyncTaskMethodBuilder`1<TResult>
       extends System.ValueType
       implements System.Runtime.CompilerServices.IAsyncMethodBuilder
```

## <a name="internal-members"></a>Miembros internos

|Name|Descripción|
|----------|-----------------|
|[Propiedad ObjectIdForDebugger](../../extensibility/debugger/asynctaskmethodbuilder-tresult-objectidfordebugger-property.md)|Obtiene un objeto que puede utilizarse para identificar de forma única este generador para el depurador.|
|[campo m_task](../../extensibility/debugger/asynctaskmethodbuilder-tresult-m-task-field.md)|Representa el inicializado de forma diferida integradas de tarea.|

## <a name="see-also"></a>Vea también
- <xref:System.Runtime.CompilerServices.AsyncTaskMethodBuilder%601>
- [Parámetros internos de extensiones paralelas para .NET Framework](../../extensibility/debugger/parallel-extension-internals-for-the-dotnet-framework.md)