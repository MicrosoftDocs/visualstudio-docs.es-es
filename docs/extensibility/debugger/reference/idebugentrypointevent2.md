---
title: IDebugEntryPointEvent2 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugEntryPointEvent2
helpviewer_keywords: IDebugEntryPointEvent2 interface
ms.assetid: a15d1cc3-97b7-438c-8d24-c23149708f42
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: ed45b6d0166a92e9547b7ad76e189108cd2b5e02
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="idebugentrypointevent2"></a>IDebugEntryPointEvent2
El motor de depuración (Alemania) envía esta interfaz para el Administrador de sesión de depuración (SDM) cuando el programa se va a ejecutar la primera instrucción de código de usuario.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
IDebugEntryPointEvent2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Notas para los implementadores  
 La DE implementa esta interfaz como parte de sus operaciones normales. El [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) debe implementar la interfaz en el mismo objeto que esta interfaz. Usa el SDM [QueryInterface](/cpp/atl/queryinterface) para tener acceso a la `IDebugEvent2` interfaz.  
  
## <a name="notes-for-callers"></a>Notas para los llamadores  
 El DIS crean y envía este objeto event cuando el programa que se está depurando se ha cargado y esté listo para ejecutar la primera instrucción de código de usuario. El evento se envía mediante la [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) función de devolución de llamada proporcionada por el SDM cuando adjunta al programa que se está depurando.  
  
## <a name="remarks"></a>Comentarios  
 [IDebugLoadCompleteEvent2](../../../extensibility/debugger/reference/idebugloadcompleteevent2.md) se envía cuando el programa está a punto de ejecutar la primera instrucción. Por ejemplo, `IDebugEntryPoint2` se envía cuando el programa está a punto de ejecutar el usuario `main` función.  
  
 Cuando se envía el Alemania `IDebugEntryPointEvent2`, debe ser la actual posición de código en la primera instrucción del código de usuario, como `main`.  
  
## <a name="requirements"></a>Requisitos  
 Encabezado: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vea también  
 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)   
 [IDebugLoadCompleteEvent2](../../../extensibility/debugger/reference/idebugloadcompleteevent2.md)