---
title: IDebugMethodField::EnumAllLocals | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugMethodField::EnumAllLocals
helpviewer_keywords: IDebugMethodField::EnumAllLocals method
ms.assetid: 0bc7cc13-2628-4bd8-8c06-4d2aa6755ea8
caps.latest.revision: "9"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 4910f5b0daa5b474be4061d73c8600c388884451
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="idebugmethodfieldenumalllocals"></a>IDebugMethodField::EnumAllLocals
Crea un enumerador para todas las variables locales del método, los que genera internamente mediante un compilador incluidos.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
HRESULT EnumAllLocals(   
   IDebugAddress*     pAddress,  
   IEnumDebugFields** ppLocals  
);  
```  
  
```csharp  
int EnumAllLocals(  
   IDebugAddress        pAddress,   
   out IEnumDebugFields ppLocals  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `pAddress`  
 [in] Un [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) objeto que representa una dirección de depuración dentro del método, que señala a un ámbito concreto o un contexto.  
  
 `ppLocals`  
 [out] Devuelve un [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) el objeto que representa la lista de todas las variables locales del ámbito especificado; en caso contrario, devuelve un valor null que indica sin variables locales.  
  
## <a name="return-value"></a>Valor devuelto  
 Si se realiza correctamente, devuelve S_OK o devuelva S_FALSE si no hay ningún variables locales. De lo contrario, devuelve un código de error.  
  
## <a name="remarks"></a>Comentarios  
 Se enumeran solo las variables definidas dentro del bloque que contiene la dirección de depuración especificado. Este método incluye a las variables locales generadas por el compilador. Si todo lo que se necesita son las variables locales definidas explícitamente en el origen, llamada la [EnumLocals](../../../extensibility/debugger/reference/idebugmethodfield-enumlocals.md) método.  
  
 Un método puede contener varios contextos o bloques de ámbito.  
  
## <a name="see-also"></a>Vea también  
 [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)   
 [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)   
 [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)   
 [EnumLocals](../../../extensibility/debugger/reference/idebugmethodfield-enumlocals.md)