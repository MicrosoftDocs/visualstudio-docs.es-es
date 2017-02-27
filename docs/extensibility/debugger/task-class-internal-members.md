---
title: "Clase de tarea: los miembros internos | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "motores de depuración, la clase de tarea [.NET Framework]"
  - "Clase de tarea [motores de depuración de .NET Framework]"
ms.assetid: 28e47c3b-9323-424a-80ac-6cc3bf19e09b
caps.latest.revision: 14
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 14
---
# Clase de tarea: los miembros internos
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Este tema describen los miembros internos de la <xref:System.Threading.Tasks.Task?displayProperty=fullName> clase que le ayudarán a implementar un depurador personalizado. Para obtener información general acerca de esta clase, vea el <xref:System.Threading.Tasks.Task> tema de referencia.  
  
 **Espacio de nombres:** <xref:System.Threading.Tasks?displayProperty=fullName>  
  
 **Ensamblado:** mscorlib \(en mscorlib.dll\)  
  
 No se puede tener acceso a estos miembros internos de .NET Framework, la sintaxis siguiente se proporciona el lenguaje intermedio en común \(CIL\).  
  
## Sintaxis  
  
```  
.class public auto ansi System.Threading.Tasks.Task  
       extends System.Object  
       implements System.Threading.IThreadPoolWorkItem,  
                  System.IAsyncResult,  
                  System.IDisposable,  
                  System.Threading.ICancelableOperation  
```  
  
## Miembros  
  
### Métodos  
  
|Name|Descripción|  
|----------|-----------------|  
|[SetNotificationForWaitCompletion \(método\)](../../extensibility/debugger/setnotificationforwaitcompletion-method.md)|Establece o borra el bit de estado TASK\_STATE\_WAIT\_COMPLETION\_NOTIFICATION.|  
|[NotifyDebuggerOfWaitCompletion \(método\)](../../extensibility/debugger/notifydebuggerofwaitcompletion-method.md)|Método de marcador de posición usado como un objetivo de punto de interrupción por el depurador.|  
  
### Campos  
  
|Nombre|Descripción|  
|------------|-----------------|  
|[m\_action](../../extensibility/debugger/m-action-field.md)|Delegado que representa el código para ejecutar en el <xref:System.Threading.Tasks.Task> objeto.|  
|[m\_contingentProperties](../../extensibility/debugger/m-contingentproperties-field.md)|Almacena propiedades adicionales de la <xref:System.Threading.Tasks.Task> objeto.|  
|[m\_Parent](../../extensibility/debugger/m-parent-field.md)|El campo de respaldo para la <xref:System.Threading.Tasks.Task?displayProperty=fullName> propiedad principal.|  
|[m\_stateFlags](../../extensibility/debugger/m-stateflags-field.md)|Almacena información sobre el estado actual de la <xref:System.Threading.Tasks.Task> objeto.|  
|[m\_stateObject](../../extensibility/debugger/m-stateobject-field.md)|Objeto que representa los datos que se va a utilizar la acción.|  
|[m\_taskId](../../extensibility/debugger/m-taskid-field.md)|El campo de respaldo para la <xref:System.Threading.Tasks.Task.Id%2A?displayProperty=fullName> propiedad.|  
|[s\_taskIdCounter](../../extensibility/debugger/s-taskidcounter-field.md)|El siguiente identificador disponible para un <xref:System.Threading.Tasks.Task> objeto.|  
|[TASK\_STATE\_CANCELED](../../extensibility/debugger/task-state-canceled-field.md)|Indica que la tarea se canceló antes de alcanzar el estado de ejecución o que la tarea confirmó la su cancelación y completa sin excepciones.|  
|[TASK\_STATE\_EXECUTED](../../extensibility/debugger/task-state-executed-field.md)|Indica que se está ejecutando la tarea.|  
|[TASK\_STATE\_FAULTED](../../extensibility/debugger/task-state-faulted-field.md)|Indica que la tarea se completó debido a una excepción no controlada.|  
|[TASK\_STATE\_RAN\_TO\_COMPLETION](../../extensibility/debugger/task-state-ran-to-completion-field.md)|Indica que la tarea terminó de ejecutarse correctamente.|  
|[TASK\_STATE\_WAITING\_ON\_CHILDREN](../../extensibility/debugger/task-state-waiting-on-children-field.md)|Indica que la tarea ha terminado de ejecutar a su delegado y espera implícitamente a finalizar tareas secundarias asociadas.|  
  
## Comentarios  
 Los siguientes métodos internos son útiles para un motor de depuración porque son la entrada a una marca <xref:System.Threading.Tasks.Task> la ejecución de código:  
  
-   `Execute`  
  
-   `ExecuteEntry`  
  
-   `ExecuteWithThreadLocal`  
  
-   `Finish`  
  
-   `InnerInvoke`  
  
-   `InternalWait`  
  
## Vea también  
 <xref:System.Threading.Tasks.Task?displayProperty=fullName>   
 [Información interna de extensiones paralelas para .NET Framework](../../extensibility/debugger/parallel-extension-internals-for-the-dotnet-framework.md)