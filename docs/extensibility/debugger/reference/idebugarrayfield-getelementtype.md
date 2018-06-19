---
title: IDebugArrayField::GetElementType | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugArrayField::GetElementType
helpviewer_keywords:
- IDebugArrayField::GetElementType method
ms.assetid: c46bf625-0a48-4cbb-8f1f-286356f2c065
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: d3c2eb6009eacd40081be28cc5945310d7a00fc1
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
ms.locfileid: "31099491"
---
# <a name="idebugarrayfieldgetelementtype"></a>IDebugArrayField::GetElementType
Obtiene el tipo de elemento de la matriz.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
HRESULT GetElementType(   
   IDebugField** ppType  
);  
```  
  
```csharp  
int GetElementType(  
   out IDebugField ppType  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `ppType`  
 [out] Devuelve un [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) objeto que describe el tipo de elemento.  
  
## <a name="return-value"></a>Valor devuelto  
 Si se realiza correctamente, devuelve S_OK; en caso contrario, devuelve un código de error.  
  
## <a name="remarks"></a>Comentarios  
 El [IDebugArrayField](../../../extensibility/debugger/reference/idebugarrayfield.md) objeto se da por supuesto que todos los elementos de la matriz son del mismo tipo.  
  
## <a name="see-also"></a>Vea también  
 [IDebugArrayField](../../../extensibility/debugger/reference/idebugarrayfield.md)   
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)