---
title: IDebugObject::IsReadOnly | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugObject::IsReadOnly
helpviewer_keywords:
- IDebugObject::IsReadOnly method
ms.assetid: c460f772-d08a-4b36-81f3-dff6a51a93fd
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 84cac5c66dd20dc9641fee7f05b456b25cbe2ffc
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="idebugobjectisreadonly"></a>IDebugObject::IsReadOnly
Determina si este objeto es de solo lectura.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
HRESULT IsReadOnly(   
   BOOL* pfIsReadOnly  
);  
```  
  
```csharp  
int IsReadOnly(  
   out int pfIsReadOnly  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `pfIsReadOnly`  
 [out] Devuelve distinto de cero (`TRUE`) si este objeto es de solo lectura; en caso contrario, devuelve cero (`FALSE`).  
  
## <a name="return-value"></a>Valor devuelto  
 Si se realiza correctamente, devuelve S_OK; en caso contrario, devuelve un código de error.  
  
## <a name="remarks"></a>Comentarios  
 Un objeto de solo lectura no puede tener su valor cambiado después de crearlo.  
  
## <a name="see-also"></a>Vea también  
 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)