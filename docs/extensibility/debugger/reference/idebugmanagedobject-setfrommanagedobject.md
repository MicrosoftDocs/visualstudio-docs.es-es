---
title: IDebugManagedObject::SetFromManagedObject | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugManagedObject::SetFromManagedObject
helpviewer_keywords: IDebugManagedObject::SetFromManagedObject method
ms.assetid: 8700ee8d-2704-4580-bccc-046837a24edd
caps.latest.revision: "9"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: a3f73236b45edea7a9dea003a1f3604669eb3739
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
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
 Este método se utiliza para cambiar el objeto administrado tal como está representado por la [IDebugManagedObject](../../../extensibility/debugger/reference/idebugmanagedobject.md) objeto.  
  
## <a name="see-also"></a>Vea también  
 [IDebugManagedObject](../../../extensibility/debugger/reference/idebugmanagedobject.md)