---
title: IDebugManagedObject::SetFromManagedObject | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugManagedObject::SetFromManagedObject
helpviewer_keywords:
- IDebugManagedObject::SetFromManagedObject method
ms.assetid: 8700ee8d-2704-4580-bccc-046837a24edd
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: afe3431e282a8cd48ea33851cef00fba116e389a
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49833946"
---
# <a name="idebugmanagedobjectsetfrommanagedobject"></a>IDebugManagedObject::SetFromManagedObject
Establece el valor de la instancia del objeto de clase de valor de la instancia de la clase de valor que se proporciona como un parámetro.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
HRESULT SetFromManagedObject(   
   IUnknown* pManagedObject  
);  
```  
  
```csharp  
int SetFromManagedObject(  
   object pManagedObject  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `pManagedObject`  
 [in] Una interfaz que representa el objeto administrado que contiene el nuevo valor.  
  
## <a name="return-value"></a>Valor devuelto  
 Si se realiza correctamente, devuelve S_OK; en caso contrario, devuelve un código de error.  
  
## <a name="remarks"></a>Comentarios  
 Este método se utiliza para cambiar el objeto administrado, tal como está representada por la [IDebugManagedObject](../../../extensibility/debugger/reference/idebugmanagedobject.md) objeto.  
  
## <a name="see-also"></a>Vea también  
 [IDebugManagedObject](../../../extensibility/debugger/reference/idebugmanagedobject.md)