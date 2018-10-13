---
title: IDebugMethodField::EnumAllLocals | Documentos de Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugMethodField::EnumAllLocals
helpviewer_keywords:
- IDebugMethodField::EnumAllLocals method
ms.assetid: 0bc7cc13-2628-4bd8-8c06-4d2aa6755ea8
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: b00145dba853a6f2518bfdb67e8f2feb52f83c1d
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2018
ms.locfileid: "49195265"
---
# <a name="idebugmethodfieldenumalllocals"></a>IDebugMethodField::EnumAllLocals
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Crea un enumerador para todas las variables locales del método, las generadas internamente mediante un compilador incluyendo.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp#  
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
 [in] Un [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) que representa una dirección de depuración dentro del método, que apunta a un ámbito concreto o un contexto del objeto.  
  
 `ppLocals`  
 [out] Devuelve un [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) objeto que representa la lista de todas las variables locales en el ámbito especificado; en caso contrario, devuelve un valor null que indica sin asignaciones locales.  
  
## <a name="return-value"></a>Valor devuelto  
 Si se realiza correctamente, devuelve S_OK o devuelve S_FALSE si no hay ningún variables locales. De lo contrario, devuelve un código de error.  
  
## <a name="remarks"></a>Comentarios  
 Se enumeran solo las variables definidas dentro del bloque que contiene la dirección de depuración especificado. Este método incluye a las variables locales generadas por el compilador. Si todo lo que es necesario son las variables locales definidas explícitamente en el origen, llamada la [EnumLocals](../../../extensibility/debugger/reference/idebugmethodfield-enumlocals.md) método.  
  
 Un método puede contener varios contextos o bloques de ámbito.  
  
## <a name="see-also"></a>Vea también  
 [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)   
 [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)   
 [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)   
 [EnumLocals](../../../extensibility/debugger/reference/idebugmethodfield-enumlocals.md)

