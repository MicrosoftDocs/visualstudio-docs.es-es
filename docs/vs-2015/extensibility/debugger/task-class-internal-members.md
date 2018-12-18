---
title: 'Clase de tarea: miembros internos | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- debug engines, Task class [.NET Framework]
- Task class [.NET Framework debug engines]
ms.assetid: 28e47c3b-9323-424a-80ac-6cc3bf19e09b
caps.latest.revision: 15
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 92ddc4b00f9d8eb37893e1db7ae44802e04e9c46
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/16/2018
ms.locfileid: "51764829"
---
# <a name="task-class---internal-members"></a>Clase de tarea: miembros internos
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

En este tema se describe los miembros internos de la <xref:System.Threading.Tasks.Task?displayProperty=fullName> clase que le ayudarán a implementar un depurador personalizado. Para obtener información general acerca de esta clase, vea el <xref:System.Threading.Tasks.Task> tema de referencia.  
  
 **Espacio de nombres:** <xref:System.Threading.Tasks?displayProperty=fullName>  
  
 **Ensamblado:** mscorlib (en mscorlib.dll)  
  
 Dado que no se puede obtener acceso a estos miembros internos de .NET Framework, la sintaxis siguiente se proporciona el lenguaje intermedio en común (CIL).  
  
## <a name="syntax"></a>Sintaxis  
  
```  
.class public auto ansi System.Threading.Tasks.Task  
       extends System.Object  
       implements System.Threading.IThreadPoolWorkItem,  
                  System.IAsyncResult,  
                  System.IDisposable,  
                  System.Threading.ICancelableOperation  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="methods"></a>Métodos  
  
|Name|Descripción|  
|----------|-----------------|  
|[SetNotificationForWaitCompletion (Método)](../../extensibility/debugger/setnotificationforwaitcompletion-method.md)|Establece o borra el bit de estado TASK_STATE_WAIT_COMPLETION_NOTIFICATION.|  
|[NotifyDebuggerOfWaitCompletion (Método)](../../extensibility/debugger/notifydebuggerofwaitcompletion-method.md)|Método de marcador de posición usado como un destino de punto de interrupción por el depurador.|  
  
### <a name="fields"></a>Campos  
  
|nombre|Descripción|  
|----------|-----------------|  
|[m_action](../../extensibility/debugger/m-action-field.md)|Delegado que representa el código para ejecutarlo en el <xref:System.Threading.Tasks.Task> objeto.|  
|[m_contingentProperties](../../extensibility/debugger/m-contingentproperties-field.md)|Almacena las propiedades adicionales de la <xref:System.Threading.Tasks.Task> objeto.|  
|[m_Parent](../../extensibility/debugger/m-parent-field.md)|El campo de respaldo para el <xref:System.Threading.Tasks.Task?displayProperty=fullName> propiedad principal.|  
|[m_stateFlags](../../extensibility/debugger/m-stateflags-field.md)|Almacena información sobre el estado actual de la <xref:System.Threading.Tasks.Task> objeto.|  
|[m_stateObject](../../extensibility/debugger/m-stateobject-field.md)|Objeto que representa los datos que se usará en la acción.|  
|[m_taskId](../../extensibility/debugger/m-taskid-field.md)|El campo de respaldo para el <xref:System.Threading.Tasks.Task.Id%2A?displayProperty=fullName> propiedad.|  
|[s_taskIdCounter](../../extensibility/debugger/s-taskidcounter-field.md)|El siguiente identificador disponible para un <xref:System.Threading.Tasks.Task> objeto.|  
|[TASK_STATE_CANCELED](../../extensibility/debugger/task-state-canceled-field.md)|Indica que la tarea se canceló antes de alcanzar el estado de ejecución, o que la tarea confirmado su cancelación y se haya completado sin excepciones.|  
|[TASK_STATE_EXECUTED](../../extensibility/debugger/task-state-executed-field.md)|Indica que se está ejecutando la tarea.|  
|[TASK_STATE_FAULTED](../../extensibility/debugger/task-state-faulted-field.md)|Indica que la tarea se completó debido a una excepción no controlada.|  
|[TASK_STATE_RAN_TO_COMPLETION](../../extensibility/debugger/task-state-ran-to-completion-field.md)|Indica que la tarea terminó de ejecutarse correctamente.|  
|[TASK_STATE_WAITING_ON_CHILDREN](../../extensibility/debugger/task-state-waiting-on-children-field.md)|Indica que la tarea ha terminado de ejecutar a su delegado e implícita está esperando a finalizar tareas secundarias asociadas.|  
  
## <a name="remarks"></a>Comentarios  
 Los siguientes métodos internos son útiles para un motor de depuración porque son la entrada a una marca <xref:System.Threading.Tasks.Task> la ejecución de código:  
  
-   `Execute`  
  
-   `ExecuteEntry`  
  
-   `ExecuteWithThreadLocal`  
  
-   `Finish`  
  
-   `InnerInvoke`  
  
-   `InternalWait`  
  
## <a name="see-also"></a>Vea también  
 <xref:System.Threading.Tasks.Task?displayProperty=fullName>   
 [Datos internos de extensiones paralelas para .NET Framework](../../extensibility/debugger/parallel-extension-internals-for-the-dotnet-framework.md)

