---
title: "IDebugReturnValueEvent2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugReturnValueEvent2"
helpviewer_keywords: 
  - "IDebugReturnValueEvent2"
ms.assetid: 2daded43-e427-4fbb-a19e-f3834e3723af
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# IDebugReturnValueEvent2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Esta interfaz es enviada por el motor de depuración \(DE\) al administrador de depuración de sesión \(SDM\) después de entrar o acerca de una función.  
  
## Sintaxis  
  
```  
IDebugReturnValueEvent2 : IUnknown  
```  
  
## Notas para los implementadores  
 El OF implementa esta interfaz para informar del valor devuelto de una función de la que se ha ejecutado o sobre.  la interfaz de [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) se debe implementar en el mismo objeto que esta interfaz.  El SDM utiliza [QueryInterface](/visual-cpp/atl/queryinterface) para tener acceso a la interfaz de `IDebugEvent2` .  
  
## Notas para los llamadores  
 El OF crea y envía este objeto event para informar del valor devuelto de una función.  El evento se envía mediante la función de devolución de llamada de [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) proporcionada por el SDM cuando se asocia al programa que se depura.  
  
## métodos en el orden de Vtable  
 La siguiente tabla se muestra el método de `IDebugReturnValueEvent2`.  
  
|Método|Descripción|  
|------------|-----------------|  
|[GetReturnValue](../../../extensibility/debugger/reference/idebugreturnvalueevent2-getreturnvalue.md)|Obtiene el valor devuelto de la entrada de una función.|  
  
## Comentarios  
 El valor devuelto por una función se puede obtener llamando a [GetReturnValue](../../../extensibility/debugger/reference/idebugreturnvalueevent2-getreturnvalue.md).  el valor devuelto aparece en la ventana de **Automtico** .  
  
## Requisitos  
 encabezado: msdbg.h  
  
 espacio de nombres: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Vea también  
 [Interfaces de núcleo](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)