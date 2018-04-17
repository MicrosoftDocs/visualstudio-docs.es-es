---
title: IDebugBinder::GetFunctionObject | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugBinder::GetFunctionObject
helpviewer_keywords:
- IDebugBinder::GetFunctionObject method
ms.assetid: 8fb789df-8f30-420d-8ca5-bb496a6738f1
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 302c6c983b07e2e2a7a393fac86999df4cb2b492
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="idebugbindergetfunctionobject"></a>IDebugBinder::GetFunctionObject
Este método obtiene un [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md) objeto utilizado para crear parámetros de función.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
HRESULT GetFunctionObject(   
   IDebugFunctionObject **ppFunction  
);  
```  
  
```csharp  
int GetFunctionObject(  
   out IDebugFunctionObject ppFunction  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `ppFunction`  
 [out] Devuelve el [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md) interfaz que se utiliza para crear parámetros de función.  
  
## <a name="return-value"></a>Valor devuelto  
 Si se realiza correctamente, devuelve S_OK; en caso contrario, devuelve un código de error.  
  
## <a name="see-also"></a>Vea también  
 [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)   
 [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md)