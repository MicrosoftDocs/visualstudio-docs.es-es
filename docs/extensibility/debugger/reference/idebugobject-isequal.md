---
title: IDebugObject::IsEqual | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugObject::IsEqual
helpviewer_keywords:
- IDebugObject::IsEqual method
ms.assetid: 4b76e663-ef2e-41ff-9be1-bf26d666a34a
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: cccce3a530aa1871e093ce5a4ab9187f1ce9d4b1
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
ms.locfileid: "31122397"
---
# <a name="idebugobjectisequal"></a>IDebugObject::IsEqual
Compara un objeto con este objeto.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
HRESULT IsEqual(   
   IDebugObject* pObject,  
   BOOL*         pfIsEqual  
);  
```  
  
```csharp  
int IsEqual(  
   IDebugObject pObject,  
   out int      pfIsEqual  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `pObject`  
 [in] Un [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) que representa el objeto que se va a comparar con el objeto.  
  
 `pfIsEqual`  
 [out] Devuelve distinto de cero (`TRUE`) si los valores de los objetos son iguales; en caso contrario, devuelve cero (`FALSE`).  
  
## <a name="return-value"></a>Valor devuelto  
 Si se realiza correctamente, devuelve S_OK; en caso contrario, devuelve un código de error.  
  
## <a name="remarks"></a>Comentarios  
 Normalmente, este método puede comparar las direcciones de los valores representados por la `pObject` parámetro y esto [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) objeto; si las direcciones son iguales, los objetos se consideran iguales.  
  
## <a name="see-also"></a>Vea también  
 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)