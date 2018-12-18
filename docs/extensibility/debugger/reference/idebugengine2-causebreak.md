---
title: IDebugEngine2::CauseBreak | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugEngine2::CauseBreak
helpviewer_keywords:
- IDebugEngine2::CauseBreak
ms.assetid: 17fe4698-b04e-4798-8412-80e0da60c387
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 08544fb80e1006dbed08e51689c1bb3b01212edb
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49820517"
---
# <a name="idebugengine2causebreak"></a>IDebugEngine2::CauseBreak
Las solicitudes de todos los programas que se está depurando por el motor de depuración (DE) para detener la ejecución de la próxima vez que uno de sus subprocesos intenta ejecutar.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
HRESULT CauseBreak(   
   void   
);  
```  
  
```csharp  
int CauseBreak();  
```  
  
## <a name="return-value"></a>Valor devuelto  
 Si es correcto, devuelve `S_OK`; en caso contrario, devuelve un código de error.  
  
## <a name="remarks"></a>Comentarios  
 Este método es asincrónico: un [IDebugBreakEvent2](../../../extensibility/debugger/reference/idebugbreakevent2.md) evento se envía cuando el programa intenta ejecutar después de que este método se llama a continuación.  
  
## <a name="see-also"></a>Vea también  
 [CauseBreak](../../../extensibility/debugger/reference/idebugprogram2-causebreak.md)   
 [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)