---
title: IDebugCustomAttributeQuery2::IsCustomAttributeDefined | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugCustomAttributeQuery2::IsCustomAttributeDefined
helpviewer_keywords:
- IDebugCustomAttributeQuery2::IsCustomAttributeDefined
ms.assetid: 5c07cc52-6d2d-42df-9d76-9f1f769641db
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 4e5340f3a8bacdb8ac9c3cdd8be21c09aa1274ac
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/02/2019
ms.locfileid: "53841452"
---
# <a name="idebugcustomattributequery2iscustomattributedefined"></a>IDebugCustomAttributeQuery2::IsCustomAttributeDefined
Determina si existe un atributo personalizado por su nombre.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
HRESULT IsCustomAttributeDefined(   
   LPCOLESTR pszCustomAttributeName  
);  
```  
  
```csharp  
int IsCustomAttributeDefined(  
   [In] string pszCustomAttributeName  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `pszCustomAttributeName`  
 [in] Una cadena que contiene el nombre del atributo personalizado para buscar.  
  
## <a name="return-value"></a>Valor devuelto  
 Devuelve que S_OK si el atributo personalizado se define en este campo, en caso contrario, devuelve S_FALSE.  
  
## <a name="remarks"></a>Comentarios  
 Para obtener los bytes del atributo asociados con el atributo personalizado, llame a la [GetCustomAttributeByName](../../../extensibility/debugger/reference/idebugcustomattributequery2-getcustomattributebyname.md) método.  
  
## <a name="see-also"></a>Vea también  
 [IDebugCustomAttributeQuery2](../../../extensibility/debugger/reference/idebugcustomattributequery2.md)