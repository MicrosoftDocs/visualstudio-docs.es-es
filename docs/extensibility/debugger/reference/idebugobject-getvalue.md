---
title: IDebugObject::GetValue | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugObject::GetValue
helpviewer_keywords:
- IDebugObject::GetValue method
ms.assetid: eec6051e-8ecb-49fa-bdd4-dd786f211692
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 50f65cba807abf4e8a0d7bc85ed28c765f7c6849
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="idebugobjectgetvalue"></a>IDebugObject::GetValue
Obtiene el valor del objeto como una serie de bytes consecutiva.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
HRESULT GetValue(   
   BYTE* pValue,  
   UINT  nSize  
);  
```  
  
```csharp  
int GetValue(  
   ref byte[] pValue,   
   uint nSize  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `pValue`  
 [entrada, salida] Una matriz que se rellena con una serie de bytes que representa el valor del objeto consecutiva.  
  
 `nSize`  
 [in] El número máximo de bytes que se va a capturar.  
  
## <a name="return-value"></a>Valor devuelto  
 Si se realiza correctamente, devuelve S_OK; en caso contrario, devuelve un código de error.  
  
## <a name="remarks"></a>Comentarios  
 Obtener el número total de bytes del valor que se pueden recuperar mediante una llamada a la [GetSize](../../../extensibility/debugger/reference/idebugobject-getsize.md) método.  
  
## <a name="see-also"></a>Vea también  
 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)