---
title: IDebugProperty2::GetReference | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugProperty2::GetReference
helpviewer_keywords:
- IDebugProperty2::GetReference method
ms.assetid: 2fa97d9b-c3d7-478e-ba5a-a933f40a0103
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 73f6bb556c3f18c8327985ac7c46b77a3a6d2c01
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "68193472"
---
# <a name="idebugproperty2getreference"></a>IDebugProperty2::GetReference
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Devuelve una referencia al valor de la propiedad.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp#  
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
