---
title: IDebugExpressionEvaluator::GetMethodProperty | Documentos de Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugExpressionEvaluator::GetMethodProperty
helpviewer_keywords:
- IDebugExpressionEvaluator::GetMethodProperty method
ms.assetid: c394fe4d-eeb6-4feb-828c-098d84a6f1ba
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: b84ac959241a8f68f4d9516879660b6414708731
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "68155364"
---
# <a name="idebugexpressionevaluatorgetmethodproperty"></a>IDebugExpressionEvaluator::GetMethodProperty
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Este método obtiene un objeto de propiedad que contiene las variables locales, argumentos y otras propiedades de un método.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp#  
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
 [in] El proveedor de símbolos que se usará, expresado como un [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md) objeto.  
  
 `pAddress`  
 [in] La dirección en el código, expresado como un [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) función del objeto, que debe resolverse en el más cercano que contiene.  
  
 `pBinder`  
 [in] El enlazador para usarse, expresado como un [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md) objeto.  
  
 `fIncludeHiddenLocals`  
 [in] Distinto de cero (`TRUE`) significa que se incluyen las variables ocultas locales; cero (`FALSE`) significa que se omita variables locales ocultas  
  
 `ppProperty`  
 [out] Devuelve un [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) objeto que representa el método.  
  
## <a name="return-value"></a>Valor devuelto  
 Si es correcto, devuelve `S_OK`; en caso contrario, devuelve un código de error.  
  
## <a name="remarks"></a>Comentarios  
 Oculta las variables locales suelen ser variables generadas por el compilador.  
  
## <a name="see-also"></a>Vea también  
 [IDebugExpressionEvaluator](../../../extensibility/debugger/reference/idebugexpressionevaluator.md)   
 [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)   
 [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)   
 [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)   
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
