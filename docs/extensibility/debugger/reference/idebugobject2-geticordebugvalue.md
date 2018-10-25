---
title: IDebugObject2::GetICorDebugValue | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugObject2::GetICorDebugValue
helpviewer_keywords:
- IDebugObject2::GetICorDebugValue method
ms.assetid: bcd4355d-3fbe-483f-bb23-a44348323c6a
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 80a70454bd28c3b59e53ee9bc1222361291e2399
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49861103"
---
# <a name="idebugobject2geticordebugvalue"></a>IDebugObject2::GetICorDebugValue
Obtiene un objeto de código administrado que representa el valor asociado a este objeto.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
HRESULT GetICorDebugValue(  
   IUnknown** ppUnk  
);  
```  
  
```csharp  
int GetICorDebugValue(  
   out object ppUnk  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `ppUnk`  
 [out] `IUnknown` interfaz que representa este alias. Esta interfaz se puede consultar el `ICorDebugValue` interfaz.  
  
## <a name="return-value"></a>Valor devuelto  
 Si se realiza correctamente, devuelve S_OK; en caso contrario, devuelve un código de error.  
  
## <a name="remarks"></a>Comentarios  
 La `ICorDebugValue` objeto es una interfaz de Common Language Runtime que representa un valor.  
  
## <a name="see-also"></a>Vea también  
 [IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md)