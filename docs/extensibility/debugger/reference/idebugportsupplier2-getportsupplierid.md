---
title: IDebugPortSupplier2::GetPortSupplierId | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugPortSupplier2::GetPortSupplierId
helpviewer_keywords:
- IDebugPortSupplier2::GetPortSupplierId
ms.assetid: 741d0829-0943-49bf-b56e-61e836043006
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 3d22ab3bd39ab5604ecd7a5446d394f5d24d4369
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/02/2019
ms.locfileid: "53947379"
---
# <a name="idebugportsupplier2getportsupplierid"></a>IDebugPortSupplier2::GetPortSupplierId
Obtiene el identificador de proveedor del puerto.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
HRESULT GetPortSupplierId(   
   GUID* pguidPortSupplier  
);  
```  
  
```csharp  
HRESULT GetPortSupplierId(   
   out Guid pguidPortSupplier  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `pguidPortSupplier`  
 [out] Devuelve el GUID del proveedor del puerto.  
  
## <a name="return-value"></a>Valor devuelto  
 Si es correcto, devuelve `S_OK`; en caso contrario, devuelve un código de error.  
  
## <a name="see-also"></a>Vea también  
 [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md)