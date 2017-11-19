---
title: IDebugCustomAttributeQuery2::IsCustomAttributeDefined | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugCustomAttributeQuery2::IsCustomAttributeDefined
helpviewer_keywords: IDebugCustomAttributeQuery2::IsCustomAttributeDefined
ms.assetid: 5c07cc52-6d2d-42df-9d76-9f1f769641db
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 2f1311beccfb36364bb8039f75bbe2955cbc9fca
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
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