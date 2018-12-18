---
title: IDebugObject::GetManagedDebugObject | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugObject::GetManagedDebugObject
helpviewer_keywords:
- IDebugObject::GetManagedDebugObject method
ms.assetid: cb89692e-7657-47ff-846d-311943521951
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: e1c0b636c88c2c2e23efcc01b01eec1e421317e0
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49831105"
---
# <a name="idebugobjectgetmanageddebugobject"></a>IDebugObject::GetManagedDebugObject
Crea una copia del objeto administrado en el espacio de direcciones del motor de depuración.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
HRESULT GetManagedDebugObject(   
   IDebugManagedObject** ppObject  
);  
```  
  
```csharp  
int GetManagedDebugObject(  
   out IDebugManagedObject ppObject  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `ppObject`  
 [out] Devuelve un [IDebugManagedObject](../../../extensibility/debugger/reference/idebugmanagedobject.md) objeto que representa el objeto administrado recién creado.  
  
## <a name="return-value"></a>Valor devuelto  
 Si se realiza correctamente, devuelve S_OK; en caso contrario, devuelve un código de error. Devuelve E_FAIL si este [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) no representa una instancia de la clase de valor administrado.  
  
## <a name="remarks"></a>Comentarios  
 Esto [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) de objeto debe representar una instancia de la clase de valor administrado, como un `System.Decimal` instancia. Al tener una copia local, la sobrecarga de la llamada a [Evaluate](../../../extensibility/debugger/reference/idebugfunctionobject-evaluate.md) se ha eliminado.  
  
## <a name="see-also"></a>Vea también  
 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)   
 [IDebugManagedObject](../../../extensibility/debugger/reference/idebugmanagedobject.md)