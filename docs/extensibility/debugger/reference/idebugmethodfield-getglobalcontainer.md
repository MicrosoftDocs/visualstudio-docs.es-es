---
title: IDebugMethodField::GetGlobalContainer | Documentos de Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugMethodField::GetGlobalContainer
helpviewer_keywords:
- IDebugMethodField::GetGlobalContainer method
ms.assetid: 041ac5aa-0b80-4310-b9ae-b88f8e7e0e5f
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: c95e6d6f23a0a7be418d3f9fa0710e45d23f3e12
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/02/2019
ms.locfileid: "53905986"
---
# <a name="idebugmethodfieldgetglobalcontainer"></a>IDebugMethodField::GetGlobalContainer
Obtiene el contenedor del método global.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
HRESULT GetGlobalContainer(  
   IDebugClassField** ppClass  
);  
```  
  
```csharp  
int GetGlobalContainer(  
   out IDebugClassField ppClass  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `ppClass`  
 [out] Devuelve un [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md) que representa el módulo en el que se define este método.  
  
## <a name="return-value"></a>Valor devuelto  
 Si se realiza correctamente, devuelve S_OK; en caso contrario, devuelve un código de error.  
  
## <a name="remarks"></a>Comentarios  
 El valor devuelto [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md) representa todo el módulo de objeto y es un objeto artificial, es decir, el propio módulo no tiene una clase real pero se puede representar mediante un `IDebugClassField` objeto, lo que permite a los distintos elementos del módulo que se enumeran y se detectan.  
  
## <a name="see-also"></a>Vea también  
 [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)   
 [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)