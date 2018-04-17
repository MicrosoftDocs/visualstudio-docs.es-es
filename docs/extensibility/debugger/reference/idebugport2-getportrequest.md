---
title: IDebugPort2::GetPortRequest | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugPort2::GetPortRequest
helpviewer_keywords:
- IDebugPort2::GetPortRequest
ms.assetid: 14abf847-0675-4fa8-872e-971e00c84224
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 6897c3085f14be785e4baaace0de7a4e92fea9ae
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="idebugport2getportrequest"></a>IDebugPort2::GetPortRequest
Obtiene la descripción de un puerto que se había utilizado previamente para crear el puerto (si está disponible).  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
HRESULT GetPortRequest(   
   IDebugPortRequest2** ppRequest  
);  
```  
  
```csharp  
int GetPortRequest(   
   out IDebugPortRequest2 ppRequest  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `ppRequest`  
 [out] Devuelve un [IDebugPortRequest2](../../../extensibility/debugger/reference/idebugportrequest2.md) objeto que representa la solicitud que se usó para crear el puerto.  
  
## <a name="return-value"></a>Valor devuelto  
 Si se realiza correctamente, devuelve `S_OK`; en caso contrario, devuelve un código de error.  Devuelve `E_PORT_NO_REQUEST` si un puerto no se creó con una [IDebugPortRequest2](../../../extensibility/debugger/reference/idebugportrequest2.md) solicitud de puerto.  
  
## <a name="see-also"></a>Vea también  
 [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)   
 [IDebugPortRequest2](../../../extensibility/debugger/reference/idebugportrequest2.md)   
 [Agregar puerto](../../../extensibility/debugger/reference/idebugportsupplier2-addport.md)