---
title: "IDebugMethodField::EnumAllLocals | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugMethodField::EnumAllLocals"
helpviewer_keywords: 
  - "IDebugMethodField::EnumAllLocals (método)"
ms.assetid: 0bc7cc13-2628-4bd8-8c06-4d2aa6755ea8
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# IDebugMethodField::EnumAllLocals
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Crea un enumerador para todas las variables locales del método, incluidos los generados internamente por un compilador.  
  
## Sintaxis  
  
```cpp#  
HRESULT EnumAllLocals(   
   IDebugAddress*     pAddress,  
   IEnumDebugFields** ppLocals  
);  
```  
  
```c#  
int EnumAllLocals(  
   IDebugAddress        pAddress,   
   out IEnumDebugFields ppLocals  
);  
```  
  
#### Parámetros  
 `pAddress`  
 \[in\]  Un objeto de [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) que representa una dirección de depuración dentro del método, elija un ámbito o en un contexto determinado.  
  
 `ppLocals`  
 \[out\]  Devuelve un objeto de [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) que representa la lista de todos los valores locales del ámbito especificado; de lo contrario, devuelve un valor NULL que no indica ningún valor local.  
  
## Valor devuelto  
 Si finaliza correctamente, devuelve S\_OK o devuelve S\_FALSE si no hay valores locales.  De lo contrario, devuelve un código de error.  
  
## Comentarios  
 Sólo las variables definido dentro del bloque que contiene la dirección especificada de depuración se enumeran.  Este método incluye cualquier valor local generados.  Si todos necesarios son valores locales definidos explícitamente en el origen, llame al método de [EnumLocals](../../../extensibility/debugger/reference/idebugmethodfield-enumlocals.md) .  
  
 Un método puede contener contextos o los varios bloques de ámbito.  
  
## Vea también  
 [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)   
 [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)   
 [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)   
 [EnumLocals](../../../extensibility/debugger/reference/idebugmethodfield-enumlocals.md)