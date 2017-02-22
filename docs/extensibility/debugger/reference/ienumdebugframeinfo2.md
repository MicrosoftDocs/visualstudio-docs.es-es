---
title: "IEnumDebugFrameInfo2 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IEnumDebugFrameInfo2"
helpviewer_keywords: 
  - "IEnumDebugFrameInfo2"
ms.assetid: 994e30ad-435a-4f9e-9272-d96d9e01099c
caps.latest.revision: 11
caps.handback.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
---
# IEnumDebugFrameInfo2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Esta interfaz se enumeran las estructuras de [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) .  
  
## Sintaxis  
  
```  
IEnumDebugFrameInfo2 : IUnknown  
```  
  
## Notas para los implementadores  
 El motor de depuración \(DE\) implementa esta interfaz para proporcionar una lista de estructuras que describe la pila de llamadas actual.  
  
## Notas para los llamadores  
 Visual Studio llama [EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md) para obtener esta interfaz siempre que un punto de interrupción, una excepción, o alto aparece en un programa que se depura.  
  
## métodos en el orden de Vtable  
 La tabla siguiente se muestran los métodos de `IEnumDebugFrameInfo2`.  
  
|Método|Descripción|  
|------------|-----------------|  
|[Siguiente](../../../extensibility/debugger/reference/ienumdebugframeinfo2-next.md)|Recupera un número especificado de estructuras de [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) en una secuencia de enumeración.|  
|[Skip](../../../extensibility/debugger/reference/ienumdebugframeinfo2-skip.md)|Omite un número especificado de estructuras de [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) en una secuencia de enumeración.|  
|[Restablecer](../../../extensibility/debugger/reference/ienumdebugframeinfo2-reset.md)|Restaura una secuencia de enumeración al principio.|  
|[Clonar](../../../extensibility/debugger/reference/ienumdebugframeinfo2-clone.md)|Crea un enumerador que contiene al mismo estado de enumeración que el enumerador actual.|  
|[GetCount](../../../extensibility/debugger/reference/ienumdebugframeinfo2-getcount.md)|Obtiene el número de estructuras de [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) de un enumerador.|  
  
## Comentarios  
 Visual Studio obtiene esta interfaz como el primer paso para administrar un punto de interrupción, una excepción, o una pausa usuario\-generada en el programa que se depura.  La lista de estructuras de [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) representa la pila de llamadas actual, con la llamada a la función actual al principio de la lista y la más antigua llamada de función en el final de la lista.  Cada `FRAMEINFO` representa un marco de pila, un contexto en el que las expresiones se pueden evaluar y las variables locales aparecer.  
  
## Requisitos  
 encabezado: msdbg.h  
  
 espacio de nombres: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Vea también  
 [Interfaces de núcleo](../../../extensibility/debugger/reference/core-interfaces.md)   
 [EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md)   
 [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md)