---
title: 'Clase Task: miembros internos | Microsoft Docs'
description: Obtenga información sobre los miembros internos de la clase System.Threading.Tasks.Task que le ayudarán a implementar un depurador personalizado.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- debug engines, Task class [.NET Framework]
- Task class [.NET Framework debug engines]
ms.assetid: 28e47c3b-9323-424a-80ac-6cc3bf19e09b
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 37691714d0168594b61a1a3849f7b65264e9999e
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/25/2021
ms.locfileid: "112902896"
---
# <a name="task-class---internal-members"></a>Clase Task: miembros internos
En este artículo se describen los miembros internos de la <xref:System.Threading.Tasks.Task?displayProperty=fullName> clase que le ayudan a implementar un depurador personalizado. Para obtener información general sobre esta clase, consulte el <xref:System.Threading.Tasks.Task> artículo de referencia.

 **Espacio de nombres:** <xref:System.Threading.Tasks?displayProperty=fullName>

 **Ensamblado:** mscorlib (en *mscorlib.dll*)

 Dado que no se puede acceder a estos miembros internos desde la .NET Framework, se proporciona la sintaxis siguiente en Common Intermediate Language (CIL).

## <a name="syntax"></a>Sintaxis

```csharp
.class public auto ansi System.Threading.Tasks.Task
       extends System.Object
       implements System.Threading.IThreadPoolWorkItem,
                  System.IAsyncResult,
                  System.IDisposable,
                  System.Threading.ICancelableOperation
```

## <a name="members"></a>Miembros

### <a name="methods"></a>Métodos

|Nombre|Descripción|
|----------|-----------------|
|[SetNotificationForWaitCompletion (Método)](../../extensibility/debugger/setnotificationforwaitcompletion-method.md)|Establece o borra el TASK_STATE_WAIT_COMPLETION_NOTIFICATION de estado.|
|[NotifyDebuggerOfWaitCompletion (Método)](../../extensibility/debugger/notifydebuggerofwaitcompletion-method.md)|Método de marcador de posición utilizado como destino de punto de interrupción por el depurador.|

### <a name="fields"></a>Campos

|Nombre|Descripción|
|----------|-----------------|
|[m_action](../../extensibility/debugger/m-action-field.md)|Delegado que representa el código que se ejecutará en el <xref:System.Threading.Tasks.Task> objeto .|
|[m_contingentProperties](../../extensibility/debugger/m-contingentproperties-field.md)|Almacena propiedades adicionales del <xref:System.Threading.Tasks.Task> objeto .|
|[m_parent](../../extensibility/debugger/m-parent-field.md)|Campo de respaldo de la <xref:System.Threading.Tasks.Task?displayProperty=fullName> propiedad primaria.|
|[m_stateFlags](../../extensibility/debugger/m-stateflags-field.md)|Almacena información sobre el estado actual del <xref:System.Threading.Tasks.Task> objeto.|
|[m_stateObject](../../extensibility/debugger/m-stateobject-field.md)|Objeto que representa los datos que usará la acción.|
|[m_taskId](../../extensibility/debugger/m-taskid-field.md)|Campo de respaldo de la <xref:System.Threading.Tasks.Task.Id%2A?displayProperty=fullName> propiedad.|
|[s_taskIdCounter](../../extensibility/debugger/s-taskidcounter-field.md)|El siguiente identificador disponible para un <xref:System.Threading.Tasks.Task> objeto .|
|[TASK_STATE_CANCELED](../../extensibility/debugger/task-state-canceled-field.md)|Indica que la tarea se canceló antes de alcanzar el estado en ejecución, o que la tarea confirmó su cancelación y se completó sin excepción.|
|[TASK_STATE_EXECUTED](../../extensibility/debugger/task-state-executed-field.md)|Indica que la tarea se está ejecutando.|
|[TASK_STATE_FAULTED](../../extensibility/debugger/task-state-faulted-field.md)|Indica que la tarea se completó debido a una excepción no controlada.|
|[TASK_STATE_RAN_TO_COMPLETION](../../extensibility/debugger/task-state-ran-to-completion-field.md)|Indica que la tarea se completó correctamente.|
|[TASK_STATE_WAITING_ON_CHILDREN](../../extensibility/debugger/task-state-waiting-on-children-field.md)|Indica que la tarea ha terminado de ejecutar su delegado y está esperando implícitamente a que finalicen las tareas secundarias adjuntas.|

## <a name="remarks"></a>Observaciones
 Los métodos internos siguientes son útiles para un motor del depurador porque marcan la entrada a la ejecución <xref:System.Threading.Tasks.Task> del código:

- `Execute`

- `ExecuteEntry`

- `ExecuteWithThreadLocal`

- `Finish`

- `InnerInvoke`

- `InternalWait`

## <a name="see-also"></a>Consulta también
- <xref:System.Threading.Tasks.Task?displayProperty=fullName>
- [Interno de la extensión paralela para el .NET Framework](../../extensibility/debugger/parallel-extension-internals-for-the-dotnet-framework.md)
