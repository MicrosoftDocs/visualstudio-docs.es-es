---
title: IDebugBinder::GetFunctionObject | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugBinder::GetFunctionObject
helpviewer_keywords: IDebugBinder::GetFunctionObject method
ms.assetid: 8fb789df-8f30-420d-8ca5-bb496a6738f1
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: c5a6e70764d9c0629d3bfa8fc0b172e0b27b6aad
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="idebugbindergetfunctionobject"></a>IDebugBinder::GetFunctionObject
Este método obtiene un [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md) objeto utilizado para crear parámetros de función.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
HRESULT GetFunctionObject(   
   IDebugFunctionObject **ppFunction  
);  
```  
  
```csharp  
int GetFunctionObject(  
   out IDebugFunctionObject ppFunction  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `ppFunction`  
 [out] Devuelve el [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md) interfaz que se utiliza para crear parámetros de función.  
  
## <a name="return-value"></a>Valor devuelto  
 Si se realiza correctamente, devuelve S_OK; en caso contrario, devuelve un código de error.  
  
## <a name="see-also"></a>Vea también  
 [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)   
 [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md)