---
title: IDebugExpressionEvaluator::GetMethodLocationProperty | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugExpressionEvaluator::GetMethodLocationProperty
helpviewer_keywords:
- IDebugExpressionEvaluator::GetMethodLocationProperty method
ms.assetid: 52c42a2e-f144-476b-8bef-442464c8fe8e
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: af772ebfd844679c7fb8d482b0fd0adf7d84e0e7
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49905355"
---
# <a name="idebugexpressionevaluatorgetmethodlocationproperty"></a>IDebugExpressionEvaluator::GetMethodLocationProperty
Este método convierte una ubicación de método y el desplazamiento en una dirección de memoria.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
HRESULT GetMethodLocationProperty(   
   LPCOLESTR             upstrFullyQualifiedMethodPlusOffset,  
   IDebugSymbolProvider* pSymbolProvider,  
   IDebugAddress*        pAddress,  
   IDebugBinder*         pBinder,  
   IDebugProperty2**     ppProperty  
);  
```  
  
```csharp  
int GetMethodLocationProperty(  
   string               upstrFullyQualifiedMethodPlusOffset,   
   IDebugSymbolProvider pSymbolProvider,   
   IDebugAddress        pAddress,   
   IDebugBinder         pBinder,   
   out IDebugProperty2  ppProperty  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `upstrFullyQualifiedMethodPlusOffset`  
 [in] La ubicación del método y el desplazamiento, expresado como una cadena.  
  
 `pSymbolProvider`  
 [in] El proveedor de símbolos se expresa como un [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md) objeto.  
  
 `pAddress`  
 [in] Una dirección dentro del método, expresado como un [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) objeto.  
  
 `pBinder`  
 [in] El enlazador se expresa como un [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md) objeto.  
  
 `ppProperty`  
 [out] Devuelve un [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) interfaz que representa la dirección de memoria.  
  
## <a name="return-value"></a>Valor devuelto  
 Si es correcto, devuelve `S_OK`; en caso contrario, devuelve un código de error.  
  
## <a name="remarks"></a>Comentarios  
 La dirección devuelta se puede usar para establecer un punto de interrupción, por ejemplo.  
  
 A pesar del nombre `upstrFullyQualifiedMethodPlusOffset`, este parámetro se puede pasar un nombre de método parcial. En ese caso, el método seleccionado es lo que incluye `pAddress`. Cómo se interpreta este parámetro depende de la implementación del evaluador de expresiones y los lenguajes que admite.  
  
## <a name="see-also"></a>Vea también  
 [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)   
 [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)   
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)   
 [IDebugExpressionEvaluator](../../../extensibility/debugger/reference/idebugexpressionevaluator.md)