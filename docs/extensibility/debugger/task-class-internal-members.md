---
title: Clase de tarea - Miembros internos ? Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debug engines, Task class [.NET Framework]
- Task class [.NET Framework debug engines]
ms.assetid: 28e47c3b-9323-424a-80ac-6cc3bf19e09b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: dcf278c0248b344cea4be7cf161ecc91581f5f2e
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80712734"
---
# <a name="task-class---internal-members"></a>Clase de tarea - miembros internos
En este artículo se describen los miembros internos de la <xref:System.Threading.Tasks.Task?displayProperty=fullName> clase que le ayudan a implementar un depurador personalizado. Para obtener información general sobre <xref:System.Threading.Tasks.Task> esta clase, consulte el artículo de referencia.

 **Espacio de nombres:**<xref:System.Threading.Tasks?displayProperty=fullName>

 **Ensamblado:** mscorlib (en *mscorlib.dll*)

 Dado que no puede tener acceso a estos miembros internos desde .NET Framework, se proporciona la sintaxis siguiente en Common Intermediate Language (CIL).

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
|[SetNotificationForWaitCompletion (Método)](../../extensibility/debugger/setnotificationforwaitcompletion-method.md)|Establece o borra el bit de estado de TASK_STATE_WAIT_COMPLETION_NOTIFICATION.|
|[NotifyDebuggerOfWaitCompletion (Método)](../../extensibility/debugger/notifydebuggerofwaitcompletion-method.md)|Método de marcador de posición utilizado como destino de punto de interrupción por el depurador.|

### <a name="fields"></a>Fields

|Nombre|Descripción|
|----------|-----------------|
|[m_action](../../extensibility/debugger/m-action-field.md)|El delegado que representa el código <xref:System.Threading.Tasks.Task> que se va a ejecutar en el objeto.|
|[m_contingentProperties](../../extensibility/debugger/m-contingentproperties-field.md)|Almacena propiedades adicionales <xref:System.Threading.Tasks.Task> del objeto.|
|[m_parent](../../extensibility/debugger/m-parent-field.md)|El campo de <xref:System.Threading.Tasks.Task?displayProperty=fullName> respaldo de la propiedad primaria.|
|[m_stateFlags](../../extensibility/debugger/m-stateflags-field.md)|Almacena información sobre el <xref:System.Threading.Tasks.Task> estado actual del objeto.|
|[m_stateObject](../../extensibility/debugger/m-stateobject-field.md)|Objeto que representa los datos que usará la acción.|
|[m_taskId](../../extensibility/debugger/m-taskid-field.md)|El campo de <xref:System.Threading.Tasks.Task.Id%2A?displayProperty=fullName> respaldo de la propiedad.|
|[s_taskIdCounter](../../extensibility/debugger/s-taskidcounter-field.md)|El siguiente identificador <xref:System.Threading.Tasks.Task> disponible para un objeto.|
|[TASK_STATE_CANCELED](../../extensibility/debugger/task-state-canceled-field.md)|Indica que la tarea cancelada antes de que alcanzara el estado de ejecución o que la tarea confirmara su cancelación y se completó sin excepción.|
|[TASK_STATE_EXECUTED](../../extensibility/debugger/task-state-executed-field.md)|Indica que la tarea se está ejecutando.|
|[TASK_STATE_FAULTED](../../extensibility/debugger/task-state-faulted-field.md)|Indica que la tarea se ha completado debido a una excepción no controlada.|
|[TASK_STATE_RAN_TO_COMPLETION](../../extensibility/debugger/task-state-ran-to-completion-field.md)|Indica que la tarea ha completado la ejecución correctamente.|
|[TASK_STATE_WAITING_ON_CHILDREN](../../extensibility/debugger/task-state-waiting-on-children-field.md)|Indica que la tarea ha terminado de ejecutar su delegado y está esperando implícitamente a que finalicen las tareas secundarias adjuntas.|

## <a name="remarks"></a>Observaciones
 Los siguientes métodos internos son útiles para <xref:System.Threading.Tasks.Task> un motor de depurador porque marcan la entrada a la ejecución de código:

- `Execute`

- `ExecuteEntry`

- `ExecuteWithThreadLocal`

- `Finish`

- `InnerInvoke`

- `InternalWait`

## <a name="see-also"></a>Vea también
- <xref:System.Threading.Tasks.Task?displayProperty=fullName>
- [Internos de extensión paralela para .NET Framework](../../extensibility/debugger/parallel-extension-internals-for-the-dotnet-framework.md)
