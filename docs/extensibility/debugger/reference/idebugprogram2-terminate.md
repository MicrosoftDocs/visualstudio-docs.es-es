---
title: IDebugProgram2::Terminate | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugProgram2::Terminate
helpviewer_keywords:
- IDebugProgram2::Terminate
ms.assetid: 4d3127d3-b1e9-4b28-ac22-2f2eea255f86
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 88fcbf0667c026cbbfc449936f92d440590e9a8f
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49834271"
---
# <a name="idebugprogram2terminate"></a>IDebugProgram2::Terminate
Finaliza el programa.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
HRESULT Terminate(   
   void   
);  
```  
  
```csharp  
int Terminate();  
```  
  
## <a name="return-value"></a>Valor devuelto  
 Si es correcto, devuelve `S_OK`; en caso contrario, devuelve un código de error.  
  
## <a name="remarks"></a>Comentarios  
 Si es posible, el programa se termina y descarga desde el proceso; en caso contrario, el motor de depuración (DE) llevará a cabo cualquier limpieza necesaria.  
  
 Este método o el [Terminate](../../../extensibility/debugger/reference/idebugprocess2-terminate.md) se llama al método por el IDE, normalmente en respuesta al usuario Detener depuración todas. La implementación de este método Idealmente, debería, finalizar el programa dentro del proceso. Si esto no es posible, el DE debe evitar que el programa se ejecute más en este proceso (y realizar cualquier limpieza necesaria). Si el `IDebugProcess2::Terminate` se llamó al método por el IDE, todo el proceso se terminará después el `IDebugProgram2::Terminate` se llama al método.  
  
## <a name="see-also"></a>Vea también  
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [Terminate](../../../extensibility/debugger/reference/idebugprocess2-terminate.md)