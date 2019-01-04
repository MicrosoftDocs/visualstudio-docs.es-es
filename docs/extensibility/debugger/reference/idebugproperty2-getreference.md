---
title: IDebugProperty2::GetReference | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugProperty2::GetReference
helpviewer_keywords:
- IDebugProperty2::GetReference method
ms.assetid: 2fa97d9b-c3d7-478e-ba5a-a933f40a0103
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 79cc459248e0a6ac507b357914d94e3fbfbfd8cb
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/02/2019
ms.locfileid: "53857084"
---
# <a name="idebugproperty2getreference"></a>IDebugProperty2::GetReference
Devuelve una referencia al valor de la propiedad.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
HRESULT GetReference(  
   IDebugReference2** ppReference  
);  
```  
  
```csharp  
int GetReference(  
   out IDebugReference2 ppReference  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `ppRererence`  
 [out] Devuelve un [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md) objeto que representa una referencia al valor de la propiedad.  
  
## <a name="return-value"></a>Valor devuelto  
 Si es correcto, devuelve `S_OK`; en caso contrario, devuelve un código de error, normalmente `E_NOTIMPL` o `E_GETREFERENCE_NO_REFERENCE`.  
  
## <a name="see-also"></a>Vea también  
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)   
 [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)