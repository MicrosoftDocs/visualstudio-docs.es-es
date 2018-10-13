---
title: IDebugEnumField::GetValueFromStringCaseInsensitive | Documentos de Microsoft
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
- IDebugEnumField::GetValueFromStringCaseInsensitive
helpviewer_keywords:
- IDebugEnumField::GetValueFromStringCaseInsensitive method
ms.assetid: ef95b38e-d9b2-4fb5-a166-7c2e14641dc7
caps.latest.revision: 9
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: a89e2ccfadd9585fcf5de4e4e7c97198829c34ee
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2018
ms.locfileid: "49211478"
---
# <a name="idebugenumfieldgetvaluefromstringcaseinsensitive"></a>IDebugEnumField::GetValueFromStringCaseInsensitive
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Este método usa una búsqueda de mayúsculas y minúsculas para devolver el valor asociado con el nombre de una constante de enumeración.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp#  
HRESULT GetValueFromStringCaseInsensitive(  
   LPCOLESTR  pszValue,  
   ULONGLONG* pvalue  
);  
```  
  
```csharp  
int GetValueFromStringCaseInsensitive(  
   string    pszValue,   
   out ulong pValue  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `pszValue`  
 [in] Cadena que especifica el nombre para el que se va a obtener el valor. Tenga en cuenta que en C++, esto es una cadena de caracteres anchos.  
  
 `pValue`  
 [out] Devuelve el valor numérico asociado.  
  
## <a name="return-value"></a>Valor devuelto  
 Si es correcto, devuelve `S_OK`; en caso contrario, devuelve `S_FALSE`, si el nombre no es parte de la enumeración o un código de error.  
  
## <a name="remarks"></a>Comentarios  
 Este método distingue mayúsculas de minúsculas. Si es necesaria una búsqueda distingue mayúsculas de minúsculas (por ejemplo, en un lenguaje como C++, donde los nombres distinguen mayúsculas de minúsculas), utilice [GetValueFromString](../../../extensibility/debugger/reference/idebugenumfield-getvaluefromstring.md).  
  
## <a name="see-also"></a>Vea también  
 [IDebugEnumField](../../../extensibility/debugger/reference/idebugenumfield.md)   
 [GetValueFromString](../../../extensibility/debugger/reference/idebugenumfield-getvaluefromstring.md)

