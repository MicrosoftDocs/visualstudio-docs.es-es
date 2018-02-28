---
title: IDebugObject::SetValue | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugObject::SetValue
helpviewer_keywords:
- IDebugObject::SetValue method
ms.assetid: d652e09c-cdc1-4519-8116-d7c743f5679b
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: adb5987e8537938c5d6f6c6241cd466654bf4793
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
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