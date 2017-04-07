---
title: IDebugQueryEngine2 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugQueryEngine2
helpviewer_keywords:
- IDebugQueryEngine2 interface
ms.assetid: 8f0e1838-a818-4459-9138-a3dceb7408de
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: ca7c86466fa23fb21a932f26dc24e37c71cf29b4
ms.openlocfilehash: cdf774a97ef3b1d0bfeec0be8482d2c116806885
ms.lasthandoff: 04/05/2017

---
# <a name="idebugqueryengine2"></a>IDebugQueryEngine2
Esta interfaz permite a la sesión de administrador de depuración (SDM) recuperar una interfaz que representa el motor de depuración (Alemania).  
  
## <a name="syntax"></a>Sintaxis  
  
```  
IDebugQueryEngine2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Notas para los implementadores  
 La DE implementa esta interfaz en los objetos que implementan las interfaces DE más comunes (como [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md), [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md), y [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)) con el fin de permitir el acceso a la [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md) interfaz de la DE sí mismo.  
  
## <a name="notes-for-callers"></a>Notas para los llamadores  
 Llame a [QueryInterface](/cpp/atl/queryinterface) en una interfaz DE típica para obtener esta interfaz.  
  
## <a name="methods-in-vtable-order"></a>Métodos en orden de Vtable  
 La tabla siguiente muestran los métodos de `IDebugQueryEngine2`.  
  
|Método|Descripción|  
|------------|-----------------|  
|[GetEngineInterface](../../../extensibility/debugger/reference/idebugqueryengine2-getengineinterface.md)|Obtiene una interfaz de motor DE depuración personalizadas.|  
  
## <a name="remarks"></a>Comentarios  
 Normalmente se implementa esta interfaz en el objeto que implementa el [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) de la interfaz para admitir la causalidad ordenados ejecución paso a paso a través de funciones; es decir, cuando el depurador está saliendo de una función, la función siguiente para ejecutar puede no ser la función anterior en la pila, pero una función en otro subproceso por completo. Para una definición de "causalidad", consulte el [Glosario de depurador de Visual Studio](../../../extensibility/debugger/reference/visual-studio-debugger-glossary.md).  
  
## <a name="requirements"></a>Requisitos  
 Encabezado: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vea también  
 [Interfaces de núcleo](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)   
 [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)   
 [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)
