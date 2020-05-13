---
title: Clase TaskScheduler - Miembros internos ? Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- TaskScheduler class [.NET Framework debug engines]
- debug engines, TaskScheduler class [.NET Framework]
ms.assetid: 87f1c969-0217-4464-8907-7609c1bf61d3
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a53abc8b24edb06445c23c19744d00d50de8735d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80712565"
---
# <a name="taskscheduler-class---internal-members"></a>TaskScheduler (Clase) - Miembros internos
En este artículo se describen los miembros internos de la <xref:System.Threading.Tasks.TaskScheduler?displayProperty=fullName> clase que le ayudan a implementar un depurador personalizado. Para obtener información general sobre <xref:System.Threading.Tasks.TaskScheduler> esta clase, consulte el artículo de referencia.

 **Espacio de nombres:**<xref:System.Threading.Tasks?displayProperty=fullName>

 **Ensamblado:** mscorlib (en *mscorlib.dll*)

 Dado que no puede tener acceso a estos miembros internos desde .NET Framework, se proporciona la sintaxis siguiente en Common Intermediate Language (CIL).

## <a name="syntax"></a>Sintaxis

```csharp
.class public abstract auto ansi beforefieldinit System.Threading.Tasks.TaskScheduler
       extends System.Object
```

## <a name="members"></a>Miembros

### <a name="methods"></a>Métodos

|Nombre|Descripción|
|----------|-----------------|
|[GetScheduledTasksForDebugger](../../extensibility/debugger/getscheduledtasksfordebugger-method.md)|Recupera una matriz de todas las tareas programadas.|
|[GetTaskSchedulersForDebugger](../../extensibility/debugger/gettaskschedulersfordebugger-method.md)|Recupera una matriz <xref:System.Threading.Tasks.TaskScheduler> de todos los objetos que están activos actualmente.|

## <a name="remarks"></a>Observaciones

## <a name="see-also"></a>Vea también
- <xref:System.Threading.Tasks.TaskScheduler?displayProperty=fullName>
- [Internos de extensión paralela para .NET Framework](../../extensibility/debugger/parallel-extension-internals-for-the-dotnet-framework.md)
