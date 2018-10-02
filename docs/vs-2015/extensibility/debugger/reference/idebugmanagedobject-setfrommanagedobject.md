---
title: IDebugManagedObject::SetFromManagedObject | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugManagedObject::SetFromManagedObject
helpviewer_keywords:
- IDebugManagedObject::SetFromManagedObject method
ms.assetid: 8700ee8d-2704-4580-bccc-046837a24edd
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: c452225290136cd168b655f2ed3196ca91961168
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "47574058"
---
# <a name="idebugmanagedobjectsetfrommanagedobject"></a>IDebugManagedObject::SetFromManagedObject
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

La versión más reciente de este tema puede encontrarse en [IDebugManagedObject::SetFromManagedObject](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugmanagedobject-setfrommanagedobject).  
  
Establece el valor de la instancia del objeto de clase de valor de la instancia de la clase de valor que se proporciona como un parámetro.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp#  
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

