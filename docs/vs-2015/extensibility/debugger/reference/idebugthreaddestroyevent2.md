---
title: IDebugThreadDestroyEvent2 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugThreadDestroyEvent2
helpviewer_keywords:
- IDebugThreadDestroyEvent2
ms.assetid: fca3f603-9432-457b-9ddd-8b0ec17da046
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 837fba4afa64c0627fcac7ab9d904ef41c00e27a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "65704798"
---
# <a name="idebugthreaddestroyevent2"></a>IDebugThreadDestroyEvent2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

El motor DE depuración (DE) envía esta interfaz al administrador de depuración de la sesión (SDM) cuando un subproceso se ha ejecutado hasta su finalización.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
IDebugThreadDestroyEvent2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Notas para los implementadores  
 El DE implementa esta interfaz para informar de que un subproceso ha finalizado. La interfaz [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) debe implementarse en el mismo objeto que esta interfaz. El SDM usa [QueryInterface](https://msdn.microsoft.com/library/62fce95e-aafa-4187-b50b-e6611b74c3b3) para tener acceso a la `IDebugEvent2` interfaz.  
  
## <a name="notes-for-callers"></a>Notas para llamadores  
 Crea y envía este objeto DE evento para informar de que un subproceso ha finalizado. El evento se envía mediante la función de devolución de llamada [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) proporcionada por el SDM cuando se adjunta al programa que se está depurando.  
  
## <a name="methods-in-vtable-order"></a>Métodos en orden de Vtable  
 En la tabla siguiente se muestran los métodos de `IDebugThreadDestroyEvent2` .  
  
|Método|Descripción|  
|------------|-----------------|  
|[GetExitCode](../../../extensibility/debugger/reference/idebugthreaddestroyevent2-getexitcode.md)|Obtiene el código de salida del subproceso.|  
  
## <a name="remarks"></a>Observaciones  
 Visual Studio usa este evento para actualizar la ventana **subprocesos** .  
  
## <a name="requirements"></a>Requisitos  
 Encabezado: msdbg. h  
  
 Espacio de nombres: Microsoft. VisualStudio. Debugger. Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Consulte también  
 [Interfaces principales](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)   
 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
