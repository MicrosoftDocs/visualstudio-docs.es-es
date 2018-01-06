---
title: IDebugObject::GetManagedDebugObject | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugObject::GetManagedDebugObject
helpviewer_keywords: IDebugObject::GetManagedDebugObject method
ms.assetid: cb89692e-7657-47ff-846d-311943521951
caps.latest.revision: "9"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: c3b0720aa8757564d06a29de2c51e53b6bb12a1f
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
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
 Esto [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) de objeto debe representar una instancia de la clase de valor administrado, como un `System.Decimal` instancia. Al tener una copia local, la sobrecarga de llamar al método [Evaluate](../../../extensibility/debugger/reference/idebugfunctionobject-evaluate.md) se ha eliminado.  
  
## <a name="see-also"></a>Vea también  
 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)   
 [IDebugManagedObject](../../../extensibility/debugger/reference/idebugmanagedobject.md)