---
title: IDebugArrayField::GetElementType | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugArrayField::GetElementType
helpviewer_keywords: IDebugArrayField::GetElementType method
ms.assetid: c46bf625-0a48-4cbb-8f1f-286356f2c065
caps.latest.revision: "9"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: a2286f201e358a190510fdff634b01f7ec9a64d9
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
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