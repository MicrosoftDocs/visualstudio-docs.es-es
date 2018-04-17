---
title: IDebugObject::SetReferenceValue | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugObject::SetReferenceValue
helpviewer_keywords:
- IDebugObject::SetReferenceValue method
ms.assetid: 08c78a4e-98eb-41cb-8b75-02a6a43d49f7
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 8941b09a18968fccba72c6e03a2fe612234909d5
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="idebugobjectsetreferencevalue"></a>IDebugObject::SetReferenceValue
Establece el valor de referencia de este objeto.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
HRESULT SetReferenceValue(   
   IDebugObject* pObject  
);  
```  
  
```csharp  
int SetReferenceValue(  
   [In] IDebugObject pObject  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `pObject`  
 [in] Un [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) objeto que representa el nuevo valor de referencia.  
  
## <a name="return-value"></a>Valor devuelto  
 Si se realiza correctamente, devuelve S_OK; en caso contrario, devuelve un código de error.  
  
## <a name="remarks"></a>Comentarios  
 Este método convierte esta [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) objeto una referencia al valor del objeto proporcionado en el `pObject` parámetro, desechar cualquier referencia anterior. Tenga en cuenta que este `IDebugObject` objeto ya debe ser un tipo de referencia.  
  
## <a name="see-also"></a>Vea también  
 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)   
 [GetValue](../../../extensibility/debugger/reference/idebugobject-getvalue.md)