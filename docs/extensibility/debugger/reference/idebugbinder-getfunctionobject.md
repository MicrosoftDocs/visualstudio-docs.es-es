---
title: IDebugBinder::GetFunctionObject | Microsoft Docs
ms.date: 11/04/2016
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
ms.openlocfilehash: 6ed1a94fbd9abba9482d13d00e8c5c000063b276
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/02/2019
ms.locfileid: "53921074"
---
# <a name="idebugbindergetfunctionobject"></a>IDebugBinder::GetFunctionObject
Este método obtiene una [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md) objeto utilizado para crear parámetros de función.  
  
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
 [out] Devuelve el [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md) interfaz que se usa para crear parámetros de función.  
  
## <a name="return-value"></a>Valor devuelto  
 Si se realiza correctamente, devuelve S_OK; en caso contrario, devuelve un código de error.  
  
## <a name="see-also"></a>Vea también  
 [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)   
 [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md)