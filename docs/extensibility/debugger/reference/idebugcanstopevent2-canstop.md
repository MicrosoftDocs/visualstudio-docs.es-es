---
title: IDebugCanStopEvent2::CanStop | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugCanStopEvent2::CanStop
helpviewer_keywords: IDebugCanStopEvent2::CanStop
ms.assetid: 7d61adbe-6b3d-41f3-86a1-45d9cc01a7f8
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: d9008410831d3c2c7b6e93d4f35a1d08914a5336
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="idebugcanstopevent2canstop"></a>IDebugCanStopEvent2::CanStop
Notifica al motor de depuración (Alemania) si desea o no se detenga en la ubicación actual del código o simplemente continuar la ejecución.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
HRESULT CanStop (   
   BOOL fCanStop  
);  
```  
  
```csharp  
int CanStop (   
   int fCanStop  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `fCanStop`  
 [in] Es distinto de cero (`TRUE`) si debe detenerse la DE en la ubicación de código actual; en caso contrario, es cero (`FALSE`).  
  
## <a name="return-value"></a>Valor devuelto  
 Si se realiza correctamente, devuelve `S_OK`; en caso contrario, devuelve un código de error.  
  
## <a name="remarks"></a>Comentarios  
 El receptor de este evento suele ser la existencia del [GetReason](../../../extensibility/debugger/reference/idebugcanstopevent2-getreason.md) método para determinar la razón por la DE desea detener y, a continuación, llama el `IDebugCanStopEvent2::CanStop` método con la respuesta adecuada.  
  
 Si se detiene el Alemania, envía un evento que describe la razón de detención. Normalmente, hay dos eventos que se envían, un salto de señal o usuario representado por la [IDebugBreakEvent2](../../../extensibility/debugger/reference/idebugbreakevent2.md) interfaz y un evento de punto de interrupción representado por la [IDebugBreakpointEvent2](../../../extensibility/debugger/reference/idebugbreakpointevent2.md) interfaz.  
  
## <a name="see-also"></a>Vea también  
 [IDebugCanStopEvent2](../../../extensibility/debugger/reference/idebugcanstopevent2.md)   
 [IDebugBreakEvent2](../../../extensibility/debugger/reference/idebugbreakevent2.md)   
 [IDebugBreakpointEvent2](../../../extensibility/debugger/reference/idebugbreakpointevent2.md)   
 [GetReason](../../../extensibility/debugger/reference/idebugcanstopevent2-getreason.md)