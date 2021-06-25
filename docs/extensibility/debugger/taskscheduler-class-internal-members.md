---
title: 'Clase TaskScheduler: miembros internos | Microsoft Docs'
description: Obtenga información sobre los miembros internos de la clase System.Threading.Tasks.TaskScheduler que le ayudan a implementar un depurador personalizado.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- TaskScheduler class [.NET Framework debug engines]
- debug engines, TaskScheduler class [.NET Framework]
ms.assetid: 87f1c969-0217-4464-8907-7609c1bf61d3
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 58b370a6742387f7493e4c6357cffd05f2bd88a5
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/25/2021
ms.locfileid: "112900153"
---
# <a name="taskscheduler-class---internal-members"></a>Clase TaskScheduler: miembros internos
En este artículo se describen los miembros internos de la <xref:System.Threading.Tasks.TaskScheduler?displayProperty=fullName> clase que le ayudan a implementar un depurador personalizado. Para obtener información general sobre esta clase, consulte el <xref:System.Threading.Tasks.TaskScheduler> artículo de referencia.

 **Espacio de nombres:** <xref:System.Threading.Tasks?displayProperty=fullName>

 **Ensamblado:** mscorlib (en *mscorlib.dll*)

 Dado que no se puede acceder a estos miembros internos desde la .NET Framework, se proporciona la sintaxis siguiente en Common Intermediate Language (CIL).

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
|[GetTaskSchedulersForDebugger](../../extensibility/debugger/gettaskschedulersfordebugger-method.md)|Recupera una matriz de todos <xref:System.Threading.Tasks.TaskScheduler> los objetos que están activos actualmente.|

## <a name="remarks"></a>Observaciones

## <a name="see-also"></a>Consulta también
- <xref:System.Threading.Tasks.TaskScheduler?displayProperty=fullName>
- [Interno de la extensión paralela para el .NET Framework](../../extensibility/debugger/parallel-extension-internals-for-the-dotnet-framework.md)
