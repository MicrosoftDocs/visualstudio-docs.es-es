---
title: IDebugReference2::SetReferenceType | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugReference2::SetReferenceType
helpviewer_keywords:
- IDebugReference2::SetReferenceType
ms.assetid: 5854a172-ea82-481c-97d9-c7fc16923d44
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: c57ab701ead4a9e60a163c50f4f241fbe60a012b
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="idebugreference2setreferencetype"></a>IDebugReference2::SetReferenceType
Establece el tipo de referencia. Reservado para un uso futuro.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
HRESULT SetReferenceType (   
   REFERENCE_TYPE dwRefType  
);  
```  
  
```csharp  
int SetReferenceType (   
   enum_REFERENCE_TYPE dwRefType  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `dwRefType`  
 [in] Un valor de la [REFERENCE_TYPE](../../../extensibility/debugger/reference/reference-type.md) enumeración que especifica el tipo de referencia.  
  
## <a name="return-value"></a>Valor devuelto  
 Siempre devuelve `E_NOTIMPL`.  
  
## <a name="see-also"></a>Vea también  
 [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)   
 [REFERENCE_TYPE](../../../extensibility/debugger/reference/reference-type.md)