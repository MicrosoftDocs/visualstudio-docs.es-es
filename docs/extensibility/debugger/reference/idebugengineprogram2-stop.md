---
title: IDebugEngineProgram2::Stop | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
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
ms.openlocfilehash: ab5bec65dc3f53681d40743bea694295ff69944b
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
ms.locfileid: "31113860"
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
 Si se realiza correctamente, devuelve `S_OK`; en caso contrario, devuelve un código de error.  
  
## <a name="remarks"></a>Comentarios  
 Se llama a este método cuando este programa se está depurando en un entorno de varios programa. Cuando se recibe un evento de detención de algún otro programa, se llama a este método en este programa. La implementación de este método debe ser asincrónica; es decir, no todos los subprocesos deben detenerse antes de que este método devuelve. La implementación de este método puede ser tan sencilla como llamar a la [CauseBreak](../../../extensibility/debugger/reference/idebugprogram2-causebreak.md) método en este programa.  
  
 En respuesta a este método se envía ningún evento de depuración.  
  
## <a name="see-also"></a>Vea también  
 [IDebugEngineProgram2](../../../extensibility/debugger/reference/idebugengineprogram2.md)   
 [CauseBreak](../../../extensibility/debugger/reference/idebugprogram2-causebreak.md)