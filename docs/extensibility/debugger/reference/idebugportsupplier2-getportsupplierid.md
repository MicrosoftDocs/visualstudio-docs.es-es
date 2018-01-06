---
title: IDebugPortSupplier2::GetPortSupplierId | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugPortSupplier2::GetPortSupplierId
helpviewer_keywords: IDebugPortSupplier2::GetPortSupplierId
ms.assetid: 741d0829-0943-49bf-b56e-61e836043006
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: d21654ac535ea897aedcabf8d4f7c18ed11e849a
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
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
 Si se realiza correctamente, devuelve `S_OK`; en caso contrario, devuelve un código de error.  
  
## <a name="see-also"></a>Vea también  
 [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md)