---
title: IDebugAddress::GetAddress | Documentos de Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugAddress::GetAddress
helpviewer_keywords:
- IDebugAddress:GetAddress method
ms.assetid: 2590387b-5d36-4116-9a75-737957b8898e
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 8d4a40da82f77f3eb04317fcb936e7a10c5351e8
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/02/2019
ms.locfileid: "53863714"
---
# <a name="idebugaddressgetaddress"></a>IDebugAddress::GetAddress
Devuelve una estructura que describe un objeto y su ubicación dentro de su ámbito o el contenedor.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
HRESULT GetAddress (  
   DEBUG_ADDRESS * pAddress  
);  
```  
  
```csharp  
int GetAddress(  
   DEBUG_ADDRESS[] pAddress  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `pAddress`  
 [in, out] Un [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md) estructura que se rellena mediante este método.  
  
## <a name="return-value"></a>Valor devuelto  
 Si se realiza correctamente, devuelve S_OK; en caso contrario, devuelve un código de error.  
  
## <a name="remarks"></a>Comentarios  
 El [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md) estructura se pasa a este método, que, a continuación, se rellena con la información adecuada. Cómo se interpreta esta información depende del tipo de información que se devuelve como el propio controlador de símbolos. Consulte [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md) para obtener más detalles.  
  
## <a name="see-also"></a>Vea también  
 [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md)