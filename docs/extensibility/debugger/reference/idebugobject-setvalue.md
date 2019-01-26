---
title: IDebugObject::SetValue | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugObject::SetValue
helpviewer_keywords:
- IDebugObject::SetValue method
ms.assetid: d652e09c-cdc1-4519-8116-d7c743f5679b
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4ba9b3983f3d6cab2525c391153457d362d2ad05
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/25/2019
ms.locfileid: "55038401"
---
# <a name="idebugobjectsetvalue"></a>IDebugObject::SetValue
Establece el valor del objeto de una serie de bytes consecutiva.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
HRESULT SetValue(   
   BYTE* pValue,  
   UINT  nSize  
);  
```  
  
```csharp  
int SetValue(  
   byte[] pValue,   
   uint   nSize  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `pValue`  
 [in] Una matriz de bytes que representa el nuevo valor.  
  
 `nSize`  
 [in] El tamaño del valor en bytes.  
  
## <a name="return-value"></a>Valor devuelto  
 Si se realiza correctamente, devuelve S_OK; en caso contrario, devuelve un código de error.  
  
## <a name="remarks"></a>Comentarios  
 Los valores de la matriz se copian en esta [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) objeto, reemplazando cualquier valor existente. El tamaño del nuevo valor puede ser mayor o menor que el valor existente. Esto `IDebugObject` no puede ser una referencia nula.  
  
## <a name="see-also"></a>Vea también  
 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)   
 [GetValue](../../../extensibility/debugger/reference/idebugobject-getvalue.md)