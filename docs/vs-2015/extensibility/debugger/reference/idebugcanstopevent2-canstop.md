---
title: IDebugCanStopEvent2::CanStop | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugCanStopEvent2::CanStop
helpviewer_keywords:
- IDebugCanStopEvent2::CanStop
ms.assetid: 7d61adbe-6b3d-41f3-86a1-45d9cc01a7f8
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: c0b89f694d544cc622ee63f87c77e2ddaf8646d3
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/16/2018
ms.locfileid: "51745428"
---
# <a name="idebugcanstopevent2canstop"></a>IDebugCanStopEvent2::CanStop
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Notifica al motor de depuración (DE) o no se detenga en la ubicación actual del código o simplemente continuar la ejecución.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp#  
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
 [in] Distinto de cero (`TRUE`) si detiene la DE en la ubicación de código actual; de lo contrario, es cero (`FALSE`).  
  
## <a name="return-value"></a>Valor devuelto  
 Si es correcto, devuelve `S_OK`; en caso contrario, devuelve un código de error.  
  
## <a name="remarks"></a>Comentarios  
 El receptor de este evento normalmente se llama el [GetReason](../../../extensibility/debugger/reference/idebugcanstopevent2-getreason.md) método para determinar la razón por la DE que desea detener y, a continuación, llama a la `IDebugCanStopEvent2::CanStop` método con la respuesta adecuada.  
  
 Si se detiene la DE, envía un evento que describe la razón de detención. Normalmente, hay dos eventos que se envían un salto de señal o del usuario representado por la [IDebugBreakEvent2](../../../extensibility/debugger/reference/idebugbreakevent2.md) interfaz y un evento de punto de interrupción representado por la [IDebugBreakpointEvent2](../../../extensibility/debugger/reference/idebugbreakpointevent2.md) interfaz.  
  
## <a name="see-also"></a>Vea también  
 [IDebugCanStopEvent2](../../../extensibility/debugger/reference/idebugcanstopevent2.md)   
 [IDebugBreakEvent2](../../../extensibility/debugger/reference/idebugbreakevent2.md)   
 [IDebugBreakpointEvent2](../../../extensibility/debugger/reference/idebugbreakpointevent2.md)   
 [GetReason](../../../extensibility/debugger/reference/idebugcanstopevent2-getreason.md)

