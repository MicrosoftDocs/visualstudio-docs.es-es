---
title: IDebugExpressionEvaluator::GetMethodProperty | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugExpressionEvaluator::GetMethodProperty
helpviewer_keywords:
- IDebugExpressionEvaluator::GetMethodProperty method
ms.assetid: c394fe4d-eeb6-4feb-828c-098d84a6f1ba
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: b5d294e401af09ec3c10fa6dabbb878c661b559e
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
ms.locfileid: "31111812"
---
# <a name="idebugexpressionevaluatorgetmethodproperty"></a>IDebugExpressionEvaluator::GetMethodProperty
Este método obtiene un objeto de propiedad que contiene las variables locales, argumentos y otras propiedades de un método.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
HRESULT GetMethodProperty(   
   IDebugSymbolProvider* pSymbolProvider,  
   IDebugAddress*        pAddress,  
   IDebugBinder*         pBinder,  
   BOOL                  fIncludeHiddenLocals,  
   IDebugProperty2**     ppProperty  
);  
```  
  
```csharp  
int GetMethodProperty(  
   IDebugSymbolProvider pSymbolProvider,   
   IDebugAddress        pAddress,   
   IDebugBinder         pBinder,   
   int                  fIncludeHiddenLocals,   
   out IDebugProperty2  ppProperty  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `pSymbolProvider`  
 [in] El proveedor de símbolos que se usará, expresada como un [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md) objeto.  
  
 `pAddress`  
 [in] La dirección en el código, expresada como un [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) función de objeto, que se debe resolver el más cercano que contiene.  
  
 `pBinder`  
 [in] El enlazador que se usará, expresada como un [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md) objeto.  
  
 `fIncludeHiddenLocals`  
 [in] Es distinto de cero (`TRUE`) significa que debe incluir variables locales ocultos; cero (`FALSE`) significa omitir ocultos variables locales  
  
 `ppProperty`  
 [out] Devuelve un [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) objeto que representa el método.  
  
## <a name="return-value"></a>Valor devuelto  
 Si se realiza correctamente, devuelve `S_OK`; en caso contrario, devuelve un código de error.  
  
## <a name="remarks"></a>Comentarios  
 Variables locales ocultos suelen ser variables generadas por el compilador.  
  
## <a name="see-also"></a>Vea también  
 [IDebugExpressionEvaluator](../../../extensibility/debugger/reference/idebugexpressionevaluator.md)   
 [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)   
 [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)   
 [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)   
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)