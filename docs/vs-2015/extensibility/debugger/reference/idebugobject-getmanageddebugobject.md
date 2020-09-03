---
title: 'IDebugObject:: GetManagedDebugObject | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugObject::GetManagedDebugObject
helpviewer_keywords:
- IDebugObject::GetManagedDebugObject method
ms.assetid: cb89692e-7657-47ff-846d-311943521951
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 4f2917135f5e25648cf08cd9030e3fdf31aedb52
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "68162474"
---
# <a name="idebugobjectgetmanageddebugobject"></a>IDebugObject::GetManagedDebugObject
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Crea una copia del objeto administrado en el espacio de direcciones del motor de depuración.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp#  
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
 enuncia Devuelve un objeto [IDebugManagedObject](../../../extensibility/debugger/reference/idebugmanagedobject.md) que representa el objeto administrado que se acaba de crear.  
  
## <a name="return-value"></a>Valor devuelto  
 Si se realiza correctamente, Devuelve S_OK; de lo contrario, devuelve un código de error. Devuelve E_FAIL si este [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) no representa una instancia de clase de valor administrado.  
  
## <a name="remarks"></a>Comentarios  
 Este objeto [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) debe representar una instancia de clase de valor administrado, como una `System.Decimal` instancia de. Al tener una copia local, se elimina la sobrecarga que supone llamar a [Evaluate](../../../extensibility/debugger/reference/idebugfunctionobject-evaluate.md) .  
  
## <a name="see-also"></a>Consulte también  
 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)   
 [IDebugManagedObject](../../../extensibility/debugger/reference/idebugmanagedobject.md)
