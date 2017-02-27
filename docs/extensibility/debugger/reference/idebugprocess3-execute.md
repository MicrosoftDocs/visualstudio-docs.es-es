---
title: "IDebugProcess3::Execute | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugProcess3::Execute"
helpviewer_keywords: 
  - "IDebugProcess3::Execute"
ms.assetid: d831cd81-d7bf-4172-8517-aa699867791f
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugProcess3::Execute
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Sigue ejecutando este proceso de un estado detenido.  Borre cualquier estado anterior de la ejecución \(como un paso\) y el inicio del proceso que se ejecuta de nuevo.  
  
> [!NOTE]
>  Este método se debe utilizar en lugar de [Ejecutar](../../../extensibility/debugger/reference/idebugprogram2-execute.md).  
  
## Sintaxis  
  
```cpp  
HRESULT Execute(  
   IDebugThread2* pThread  
);  
```  
  
```c#  
int Execute(  
   IDebugThread2 pThread  
);  
```  
  
#### Parámetros  
 `pThread`  
 \[in\]  un objeto de [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) que representa el subproceso para ejecutarse.  
  
## Valor devuelto  
 Si finaliza correctamente, devuelve `S_OK`; de lo contrario, devuelve el código de error.  
  
## Comentarios  
 Cuando el usuario inicia la ejecución de un estado detenido en el subproceso de algún otro proceso, este método se llama en este proceso.  Este método también se llama cuando el usuario selecciona el comando de **Iniciar** de menú de **Depurar** en el IDE.  La implementación de este método puede ser tan simple como llamando al método de [Resume](../../../extensibility/debugger/reference/idebugthread2-resume.md) en el subproceso actual en el proceso.  
  
> [!WARNING]
>  No envíe un evento que detiene o un evento \(sincrónico\) inmediato a [Evento](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) mientras controla esta llamada; si no el depurador puede no responder.  
  
## Vea también  
 [IDebugProcess3](../../../extensibility/debugger/reference/idebugprocess3.md)   
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)   
 [Resume](../../../extensibility/debugger/reference/idebugthread2-resume.md)   
 [Evento](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)