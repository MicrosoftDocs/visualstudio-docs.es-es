---
title: IDebugManagedObject::GetManagedObject | Documentos de Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugManagedObject::GetManagedObject
helpviewer_keywords:
- IDebugManagedObject::GetManagedObject method
ms.assetid: 6abe1402-6aad-41e6-8ec1-ae12d5945992
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 583a62b98d29f1be7626443cd2e1b069cf388d5c
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/16/2018
ms.locfileid: "51770777"
---
# <a name="idebugmanagedobjectgetmanagedobject"></a>IDebugManagedObject::GetManagedObject
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Devuelve una interfaz que representa el objeto administrado.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp#  
HRESULT GetManagedObject(   
   IUnknown** ppManagedObject  
);  
```  
  
```cpp#  
int GetManagedObject(  
   out object ppManagedObject  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `ppManagedObject`  
 [out] Devuelve una interfaz que representa el objeto administrado.  
  
## <a name="return-value"></a>Valor devuelto  
 Si se realiza correctamente, devuelve S_OK; en caso contrario, devuelve un código de error.  
  
## <a name="remarks"></a>Comentarios  
 La interfaz devuelta por este método se puede consultar para cualquier interfaz implementada por la clase administrada, lo que permite llamar a sus métodos.  
  
## <a name="see-also"></a>Vea también  
 [IDebugManagedObject](../../../extensibility/debugger/reference/idebugmanagedobject.md)

