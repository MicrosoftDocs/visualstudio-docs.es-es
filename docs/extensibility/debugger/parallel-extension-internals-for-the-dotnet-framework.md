---
title: Datos internos de extensiones en paralelo de .NET Framework | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debug engines, internals [.NET Framework]
ms.assetid: 93e07cfa-91fa-464c-b866-8bf5570411df
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1ecc13be90259c68fa4d37daa5139b27b4ea8c7f
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/29/2019
ms.locfileid: "66351479"
---
# <a name="parallel-extension-internals-for-the-net-framework"></a>Parámetros internos de extensiones paralelas para .NET Framework
Esta sección describen los tipos internos, métodos y campos de clases que le ayudarán a implementan a un depurador personalizado para las extensiones paralelas para .NET Framework.

## <a name="in-this-section"></a>En esta sección
 [Clase de tarea](../../extensibility/debugger/task-class-internal-members.md) se describen los miembros de datos internos de la <xref:System.Threading.Tasks.Task?displayProperty=fullName> clase.

 [Clase TaskScheduler](../../extensibility/debugger/taskscheduler-class-internal-members.md) se describen los miembros de datos internos de la <xref:System.Threading.Tasks.TaskScheduler?displayProperty=fullName> clase.

 [Clase ContingentProperties](../../extensibility/debugger/contingentproperties-class-internal-members.md) se describen los miembros de datos internos de la `System.Threading.Tasks.ContingentProperties` clase.

 [Estructura AsyncTaskMethodBuilder](../../extensibility/debugger/asynctaskmethodbuilder-structure-internal-members.md) se describen los miembros internos de la <xref:System.Runtime.CompilerServices.AsyncTaskMethodBuilder> estructura.

 [AsyncTaskMethodBuilder\<TResult > estructura](../../extensibility/debugger/asynctaskmethodbuilder-tresult-structure-internal-members.md) se describen los miembros internos de la <xref:System.Runtime.CompilerServices.AsyncTaskMethodBuilder%601> estructura.

 [Estructura AsyncVoidMethodBuilder](../../extensibility/debugger/asyncvoidmethodbuilder-structure-internal-members.md) se describen los miembros internos de la <xref:System.Runtime.CompilerServices.AsyncVoidMethodBuilder> estructura.

## <a name="see-also"></a>Vea también
- <xref:System.Threading.Tasks.Task?displayProperty=fullName>
- <xref:System.Threading.Tasks.TaskScheduler?displayProperty=fullName>
- [Extensibilidad del depurador de Visual Studio](../../extensibility/debugger/visual-studio-debugger-extensibility.md)
- [Programación en paralelo en .NET](/dotnet/standard/parallel-programming/index)