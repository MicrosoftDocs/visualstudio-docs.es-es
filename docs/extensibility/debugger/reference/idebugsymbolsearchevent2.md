---
title: IDebugSymbolSearchEvent2 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugSymbolSearchEvent2
helpviewer_keywords: IDebugSymbolSearchEvent2
ms.assetid: 9b946d55-ff85-44eb-b40a-efbf8282eafd
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: a931768dd13f2ced30f329b54c1fe6eb9333eb9c
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="idebugsymbolsearchevent2"></a>IDebugSymbolSearchEvent2
Esta interfaz se envía por el motor de depuración (Alemania) para indicar que se han cargado los símbolos de depuración para un módulo que se está depurando.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
IDebugSymbolSearchEvent2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Notas para los implementadores  
 La DE implementa esta interfaz para notificar que se han cargado símbolos de un módulo. El [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) debe implementar la interfaz en el mismo objeto que esta interfaz. Usa el SDM [QueryInterface](/cpp/atl/queryinterface) para tener acceso a la `IDebugEvent2` interfaz.  
  
## <a name="notes-for-callers"></a>Notas para los llamadores  
 El DIS crean y envía este objeto de evento para notificar que se han cargado símbolos de un módulo. El evento se envía mediante la [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) función de devolución de llamada proporcionada por el SDM cuando adjunta al programa que se está depurando.  
  
## <a name="methods-in-vtable-order"></a>Métodos en orden de Vtable  
 El `IDebugSymbolSearchEvent2` interfaz expone el método siguiente.  
  
|Método|Descripción|  
|------------|-----------------|  
|[GetSymbolSearchInfo](../../../extensibility/debugger/reference/idebugsymbolsearchevent2-getsymbolsearchinfo.md)|Recupera información sobre los resultados de una búsqueda de símbolos.|  
  
## <a name="remarks"></a>Comentarios  
 Este evento se enviará incluso si no se pudieron cargar los símbolos. Al llamar a `IDebugSymbolSearchEvent2::GetSymbolSearchInfo` permite que el controlador de este evento para determinar si el módulo tiene realmente los símbolos.  
  
 Visual Studio utiliza normalmente este evento para actualizar el estado de símbolos cargados en el **módulos** ventana.  
  
## <a name="requirements"></a>Requisitos  
 Encabezado: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vea también  
 [Interfaces de núcleo](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)