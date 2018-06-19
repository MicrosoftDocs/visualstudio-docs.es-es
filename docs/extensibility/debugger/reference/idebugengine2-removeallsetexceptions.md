---
title: IDebugEngine2::RemoveAllSetExceptions | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugEngine2::RemoveAllSetExceptions
helpviewer_keywords:
- IDebugEngine2::RemoveAllSetExceptions
ms.assetid: 165fbe89-802d-4d99-85ca-c10fd6cccc09
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: e3446b910aa1e728319d0f4c7acdbf65b01d1cb4
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
ms.locfileid: "31106869"
---
# <a name="idebugengine2removeallsetexceptions"></a>IDebugEngine2::RemoveAllSetExceptions
Quita la lista de excepciones que se estableció el IDE para una determinada arquitectura de tiempo de ejecución o un lenguaje.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
HRESULT RemoveAllSetExceptions(   
   REFGUID guidType  
);  
```  
  
```csharp  
int RemoveAllSetExceptions(   
   ref Guid guidType  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `guidType`  
 [in] El GUID para el idioma o en el GUID para el motor de depuración que es específico de una arquitectura en tiempo de ejecución.  
  
## <a name="return-value"></a>Valor devuelto  
 Si se realiza correctamente, devuelve `S_OK`; en caso contrario, devuelve un código de error.  
  
## <a name="remarks"></a>Comentarios  
 Las excepciones que se quitan mediante este método se establecieron por las llamadas anteriores a la [SetException](../../../extensibility/debugger/reference/idebugengine2-setexception.md) método.  
  
 Para quitar una excepción específica, llame a la [RemoveSetException](../../../extensibility/debugger/reference/idebugengine2-removesetexception.md) método.  
  
## <a name="see-also"></a>Vea también  
 [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)   
 [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)   
 [RemoveSetException](../../../extensibility/debugger/reference/idebugengine2-removesetexception.md)