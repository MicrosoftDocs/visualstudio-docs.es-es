---
title: "IDebugExpressionEvaluator::GetMethodLocationProperty | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugExpressionEvaluator::GetMethodLocationProperty"
helpviewer_keywords: 
  - "IDebugExpressionEvaluator::GetMethodLocationProperty (método)"
ms.assetid: 52c42a2e-f144-476b-8bef-442464c8fe8e
caps.latest.revision: 11
caps.handback.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugExpressionEvaluator::GetMethodLocationProperty
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Este método convierte una ubicación y un desplazamiento de método en una dirección de memoria.  
  
## Sintaxis  
  
```cpp#  
HRESULT GetMethodLocationProperty(   
   LPCOLESTR             upstrFullyQualifiedMethodPlusOffset,  
   IDebugSymbolProvider* pSymbolProvider,  
   IDebugAddress*        pAddress,  
   IDebugBinder*         pBinder,  
   IDebugProperty2**     ppProperty  
);  
```  
  
```c#  
int GetMethodLocationProperty(  
   string               upstrFullyQualifiedMethodPlusOffset,   
   IDebugSymbolProvider pSymbolProvider,   
   IDebugAddress        pAddress,   
   IDebugBinder         pBinder,   
   out IDebugProperty2  ppProperty  
);  
```  
  
#### Parámetros  
 `upstrFullyQualifiedMethodPlusOffset`  
 \[in\]  La ubicación y el desplazamiento del método, expresados como cadena.  
  
 `pSymbolProvider`  
 \[in\]  El proveedor del token expresado como un objeto de [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md) .  
  
 `pAddress`  
 \[in\]  Una dirección dentro del método, expresado como un objeto de [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) .  
  
 `pBinder`  
 \[in\]  El enlazador expresado como un objeto de [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md) .  
  
 `ppProperty`  
 \[out\]  Devuelve una interfaz de [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) que representa la dirección de memoria.  
  
## Valor devuelto  
 Si finaliza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.  
  
## Comentarios  
 La dirección devuelta se puede utilizar para establecer un punto de interrupción, por ejemplo.  
  
 A pesar del nombre`upstrFullyQualifiedMethodPlusOffset`, este parámetro se puede pasar un nombre parcialmente completo del método.  en ese caso, el método seleccionado es el que agrega`pAddress`.  Cómo se interpreta este parámetro depende de la implementación del evaluador de expresiones e idioma que admite.  
  
## Vea también  
 [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)   
 [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)   
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)   
 [IDebugExpressionEvaluator](../../../extensibility/debugger/reference/idebugexpressionevaluator.md)