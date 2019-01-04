---
title: IDebugEngineProgram2::Stop | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugEngineProgram2::Stop
helpviewer_keywords:
- IDebugEngineProgram2::Stop
ms.assetid: 6e1c3d56-fb67-4a5b-80f9-8ee5131972bf
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 089b8c14db3caa1c9f4b3a2ad0a364bcfbb5a096
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/02/2019
ms.locfileid: "53840361"
---
# <a name="idebugengineprogram2stop"></a>IDebugEngineProgram2::Stop
Detiene todos los subprocesos que se ejecutan en este programa.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
HRESULT Stop(   
   void   
);  
```  
  
```csharp  
int Stop();  
```  
  
## <a name="return-value"></a>Valor devuelto  
 Si es correcto, devuelve `S_OK`; en caso contrario, devuelve un código de error.  
  
## <a name="remarks"></a>Comentarios  
 Este método se llama cuando este programa se está depurando en un entorno de varios programa. Cuando se recibe un evento de detención desde otro programa, este método se llama en este programa. La implementación de este método debe ser asincrónica; es decir, no todos los subprocesos deben detenerse antes de que devuelve este método. La implementación de este método puede ser tan sencilla como llamar a la [CauseBreak](../../../extensibility/debugger/reference/idebugprogram2-causebreak.md) método en este programa.  
  
 Ningún evento de depuración se envía como respuesta a este método.  
  
## <a name="see-also"></a>Vea también  
 [IDebugEngineProgram2](../../../extensibility/debugger/reference/idebugengineprogram2.md)   
 [CauseBreak](../../../extensibility/debugger/reference/idebugprogram2-causebreak.md)