---
title: IDebugQueryEngine2 | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugQueryEngine2
helpviewer_keywords:
- IDebugQueryEngine2 interface
ms.assetid: 8f0e1838-a818-4459-9138-a3dceb7408de
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: f80e8b44326cb082c8f6428365bad2575c317da6
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "47574103"
---
# <a name="idebugqueryengine2"></a>IDebugQueryEngine2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

La versión más reciente de este tema puede encontrarse en [IDebugQueryEngine2](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugqueryengine2).  
  
Esta interfaz permite que la sesión de depuración manager (SDM) recuperar una interfaz que representa el motor de depuración (DE).  
  
## <a name="syntax"></a>Sintaxis  
  
```  
IDebugQueryEngine2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Notas para los implementadores  
 La DE implementa esta interfaz en los objetos que implementan las interfaces DE más comunes (como [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md), [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md), y [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)) en a fin de permitir el acceso a la [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md) interfaz de la DE sí mismo.  
  
## <a name="notes-for-callers"></a>Notas para los llamadores  
 Llame a [QueryInterface](http://msdn.microsoft.com/library/62fce95e-aafa-4187-b50b-e6611b74c3b3) en una interfaz DE típica para obtener esta interfaz.  
  
## <a name="methods-in-vtable-order"></a>Métodos en orden de Vtable  
 La tabla siguiente muestran los métodos de `IDebugQueryEngine2`.  
  
|Método|Descripción|  
|------------|-----------------|  
|[GetEngineInterface](../../../extensibility/debugger/reference/idebugqueryengine2-getengineinterface.md)|Obtiene una interfaz de motor DE depuración personalizado.|  
  
## <a name="remarks"></a>Comentarios  
 Esta interfaz se implementa normalmente en el objeto que implementa el [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) interfaz con el fin de admitir ordenados de causalidad ejecución paso a paso a través de funciones, es decir, cuando el depurador salir de una función, el Para ejecutar la función Next no puede ser la función anterior en la pila, pero una función en otro subproceso por completo. Para obtener una definición de "causalidad", consulte el [Glosario del depurador de Visual Studio](../../../extensibility/debugger/reference/visual-studio-debugger-glossary.md).  
  
## <a name="requirements"></a>Requisitos  
 Encabezado: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vea también  
 [Interfaces del núcleo](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)   
 [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)   
 [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)

