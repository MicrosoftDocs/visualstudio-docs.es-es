---
title: 'IDebugExpressionEvaluator:: GetMethodLocationProperty | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugExpressionEvaluator::GetMethodLocationProperty
helpviewer_keywords:
- IDebugExpressionEvaluator::GetMethodLocationProperty method
ms.assetid: 52c42a2e-f144-476b-8bef-442464c8fe8e
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: d82b002d9253b2d48f78e74fdf964cf42d241d9a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "68144392"
---
# <a name="idebugexpressionevaluatorgetmethodlocationproperty"></a>IDebugExpressionEvaluator::GetMethodLocationProperty
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Este método convierte una ubicación de método y el desplazamiento en una dirección de memoria.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp#  
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
 de Ubicación y desplazamiento del método, expresado como una cadena.  
  
 `pSymbolProvider`  
 de El proveedor de símbolos expresado como un objeto [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md) .  
  
 `pAddress`  
 de Una dirección dentro del método, expresada como un objeto [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) .  
  
 `pBinder`  
 de El enlazador expresado como un objeto [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md) .  
  
 `ppProperty`  
 enuncia Devuelve una interfaz [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) que representa la dirección de memoria.  
  
## <a name="return-value"></a>Valor devuelto  
 Si la operación se realiza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.  
  
## <a name="remarks"></a>Comentarios  
 La dirección devuelta se puede utilizar para establecer un punto de interrupción, por ejemplo.  
  
 A pesar del nombre `upstrFullyQualifiedMethodPlusOffset` , este parámetro se puede pasar a un nombre de método parcialmente calificado. En ese caso, el método seleccionado es el que se incluye `pAddress` . La forma en que se interpreta este parámetro depende de la implementación del evaluador de expresiones y del lenguaje que admite.  
  
## <a name="see-also"></a>Consulte también  
 [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)   
 [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)   
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)   
 [IDebugExpressionEvaluator](../../../extensibility/debugger/reference/idebugexpressionevaluator.md)
