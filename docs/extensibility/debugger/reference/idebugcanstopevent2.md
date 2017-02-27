---
title: "IDebugCanStopEvent2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugCanStopEvent2"
helpviewer_keywords: 
  - "Interfaz IDebugBreakpointRequest2"
ms.assetid: 784bd5b1-4a3f-4455-b313-c4c9a82555a5
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# IDebugCanStopEvent2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Esta interfaz se utiliza para preguntar al administrador \(SDM\) de depuración de la sesión si detener en la ubicación actual del código.  
  
## Sintaxis  
  
```  
IDebugCanStopEvent2 : IUknown  
```  
  
## Notas para los implementadores  
 El motor de depuración \(DE\) implementa esta interfaz para admitir el recorrido por código fuente.  la interfaz de [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) se debe implementar en el mismo objeto que esta interfaz \(el SDM utiliza [QueryInterface](/visual-cpp/atl/queryinterface) para tener acceso a la interfaz de `IDebugEvent2` \).  
  
 La implementación de esta interfaz debe comunicar la llamada de SDM de [CanStop](../../../extensibility/debugger/reference/idebugcanstopevent2-canstop.md) al motor de depuración.  Por ejemplo, esto se puede hacer con un mensaje enviado al subproceso del control de mensajes del motor de depuración o el objeto que implementa esta interfaz puede contener una referencia al motor y llamar de depuración de nuevo con el motor de depuración con el marcador pasado en `IDebugCanStopEvent2::CanStop`.  
  
## Notas para los llamadores  
 El OF puede enviar este método cada vez que el OF está ordenada para continuar la ejecución y el OF está recorriendo el código.  Este evento se envía mediante la función de devolución de llamada de [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) proporcionada por el SDM cuando adjuntó el programa que se depura.  
  
## métodos en el orden de Vtable  
 La tabla siguiente se muestran los métodos de `IDebugCanStopEvent2`.  
  
|Método|Descripción|  
|------------|-----------------|  
|[GetReason](../../../extensibility/debugger/reference/idebugcanstopevent2-getreason.md)|Obtiene el motivo de este evento.|  
|[CanStop](../../../extensibility/debugger/reference/idebugcanstopevent2-canstop.md)|Especifica si el programa que se depura debe detener en la ubicación de este evento \(y enviar un evento que describe el motivo de detener\) o simplemente continuar la ejecución.|  
|[GetDocumentContext](../../../extensibility/debugger/reference/idebugcanstopevent2-getdocumentcontext.md)|Obtiene el contexto del documento que describe la ubicación de este evento.|  
|[GetCodeContext](../../../extensibility/debugger/reference/idebugcanstopevent2-getcodecontext.md)|Obtiene el contexto del código que describe la ubicación de este evento.|  
  
## Comentarios  
 El OF envía esta interfaz si el usuario en una función y el OF no se encuentra ninguna información de depuración allí o existe información de depuración pero el OF no sabe si el origen se puede mostrar en esa ubicación.  
  
## Requisitos  
 encabezado: msdbg.h  
  
 espacio de nombres: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Vea también  
 [IDebugStepCompleteEvent2](../../../extensibility/debugger/reference/idebugstepcompleteevent2.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)