---
title: IEnumDebugFields::Skip | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IEnumDebugFields::Skip
helpviewer_keywords:
- IEnumDebugFields::Skip method
ms.assetid: b3bc51c4-21ae-4913-800c-c2ca9dc18443
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 0e5704f741883a3d676b0428b358e14debfa7599
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/02/2019
ms.locfileid: "53917061"
---
# <a name="ienumdebugfieldsskip"></a>IEnumDebugFields::Skip
Este método omite el número especificado de elementos.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
HRESULT Skip(  
   ULONG celt  
);  
```  
  
```csharp  
int Skip(  
   uint celt  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `celt`  
 [in] Número de elementos que se van a omitir.  
  
## <a name="return-value"></a>Valor devuelto  
 Si es correcto, devuelve `S_OK`. Devuelve `S_FALSE` si `celt` es mayor que el número de elementos restantes; en caso contrario, devuelve un código de error.  
  
## <a name="remarks"></a>Comentarios  
 Si `celt` especifica un valor mayor que el número de elementos restantes, la enumeración se establece en el extremo y `S_FALSE` se devuelve.  
  
## <a name="see-also"></a>Vea también  
 [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)