---
title: IDebugQueryEngine2 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugQueryEngine2
helpviewer_keywords:
- IDebugQueryEngine2 interface
ms.assetid: 8f0e1838-a818-4459-9138-a3dceb7408de
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 7274d621e47c9c705cc0ce6bc4ad49f24e144f59
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "65683277"
---
# <a name="idebugqueryengine2"></a>IDebugQueryEngine2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Esta interfaz permite que el administrador de depuración de la sesión (SDM) recupere una interfaz que representa el motor DE depuración (DE).  
  
## <a name="syntax"></a>Sintaxis  
  
```  
IDebugQueryEngine2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Notas para los implementadores  
 El DE implementa esta interfaz en los objetos que implementan las interfaces DE más comunes (como [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md), [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)y [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)) para permitir el acceso a la interfaz [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md) del propio.  
  
## <a name="notes-for-callers"></a>Notas para llamadores  
 Llame a [QueryInterface](https://msdn.microsoft.com/library/62fce95e-aafa-4187-b50b-e6611b74c3b3) en una interfaz de una interfaz típica para obtener esta interfaz.  
  
## <a name="methods-in-vtable-order"></a>Métodos en orden de Vtable  
 En la tabla siguiente se muestran los métodos de `IDebugQueryEngine2` .  
  
|Método|Descripción|  
|------------|-----------------|  
|[GetEngineInterface](../../../extensibility/debugger/reference/idebugqueryengine2-getengineinterface.md)|Obtiene una interfaz personalizada del motor DE depuración (DE).|  
  
## <a name="remarks"></a>Observaciones  
 Esta interfaz se implementa normalmente en el objeto que implementa la interfaz [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) para admitir la ejecución de paso a través de las funciones con orden de causalidad. es decir, cuando el depurador está saliendo de una función, es posible que la función siguiente que se va a ejecutar no sea la función anterior en la pila, sino que una función de otro subproceso esté totalmente. Para obtener una definición de "causalidad", vea el [Glosario del depurador de Visual Studio](../../../extensibility/debugger/reference/visual-studio-debugger-glossary.md).  
  
## <a name="requirements"></a>Requisitos  
 Encabezado: msdbg. h  
  
 Espacio de nombres: Microsoft. VisualStudio. Debugger. Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Consulte también  
 [Interfaces principales](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)   
 [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)   
 [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)
