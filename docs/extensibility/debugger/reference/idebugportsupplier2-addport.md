---
title: IDebugPortSupplier2::AddPort | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugPortSupplier2::AddPort
helpviewer_keywords:
- IDebugPortSupplier2::AddPort
ms.assetid: df491161-6bf3-4fcc-b478-b9ec88ec995f
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: ab6348739feba7006e5c18eee6f7dc5f301242d9
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
ms.locfileid: "31114435"
---
# <a name="idebugportsupplier2addport"></a>IDebugPortSupplier2::AddPort
Agrega un puerto.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
HRESULT AddPort(   
   IDebugPortRequest2* pRequest,  
   IDebugPort2**       ppPort  
);  
```  
  
```csharp  
int AddPort(   
   IDebugPortRequest2 pRequest,  
   out IDebugPort2    ppPort  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `pRequest`  
 [in] Un [IDebugPortRequest2](../../../extensibility/debugger/reference/idebugportrequest2.md) objeto que describe el puerto que se va a agregar.  
  
 `ppPort`  
 [out] Devuelve un [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md) objeto que representa el puerto.  
  
## <a name="return-value"></a>Valor devuelto  
 Si se realiza correctamente, devuelve `S_OK`; en caso contrario, devuelve un código de error.  
  
## <a name="remarks"></a>Comentarios  
 Este método crea realmente el puerto solicitado, así como éste se agrega a la lista interna del proveedor de puerto de puertos activos. El [CanAddPort](../../../extensibility/debugger/reference/idebugportsupplier2-canaddport.md) método puede llamarse en primer lugar para evitar posibles retrasos que consumen muchos recursos.  
  
## <a name="see-also"></a>Vea también  
 [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md)   
 [IDebugPortRequest2](../../../extensibility/debugger/reference/idebugportrequest2.md)   
 [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)   
 [CanAddPort](../../../extensibility/debugger/reference/idebugportsupplier2-canaddport.md)