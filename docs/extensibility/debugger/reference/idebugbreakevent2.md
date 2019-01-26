---
title: IDebugBreakEvent2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugBreakEvent2
helpviewer_keywords:
- IDebugBreakEvent2 interface
ms.assetid: 57dfdbc2-4e68-4dbf-9579-006cd6fb1c62
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 218c1d01a693b81472a40430fa60455073bb8fb4
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/25/2019
ms.locfileid: "54929015"
---
# <a name="idebugbreakevent2"></a>IDebugBreakEvent2
Esta interfaz indica al administrador de depuración de la sesión (SDM) que una interrupción asincrónica se ha completado correctamente.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
IDebugBreakEvent2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Notas para los implementadores  
 La DE implementa esta interfaz para admitir los saltos de usuario en un programa. El [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) interfaz debe implementarse en el mismo objeto que esta interfaz (usa el SDM [QueryInterface](/cpp/atl/queryinterface) para tener acceso a la `IDebugEvent2` interfaz).  
  
## <a name="notes-for-callers"></a>Notas para los llamadores  
 Las llamadas SDM [CauseBreak](../../../extensibility/debugger/reference/idebugprogram2-causebreak.md) cuando el usuario ha solicitado el programa que se está depurando se pongan en pausa. Cuando el programa se ha detenido correctamente, se envía al DE la `IDebugBreakEvent2` eventos. Este evento se envía mediante la [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) función de devolución de llamada proporcionada por el SDM cuando adjunta al programa que se está depurando.  
  
## <a name="remarks"></a>Comentarios  
 Por ejemplo, un usuario puede seleccionar la **interrumpir todos** comando el **depurar** menú para interrumpir un programa que se ejecuta un bucle infinito. El SDM indica al programa para detener mediante una llamada a [CauseBreak](../../../extensibility/debugger/reference/idebugprogram2-causebreak.md). Los envíos DE `IDebugBreakEvent2` cuando, por último, detiene el programa.  
  
## <a name="requirements"></a>Requisitos  
 Encabezado: msdbg.h  
  
 Espacio de nombres: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vea también  
 [CauseBreak](../../../extensibility/debugger/reference/idebugprogram2-causebreak.md)   
 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)