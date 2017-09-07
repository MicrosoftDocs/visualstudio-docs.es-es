---
title: IDebugEnumField::GetValueFromStringCaseInsensitive | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugEnumField::GetValueFromStringCaseInsensitive
helpviewer_keywords:
- IDebugEnumField::GetValueFromStringCaseInsensitive method
ms.assetid: ef95b38e-d9b2-4fb5-a166-7c2e14641dc7
caps.latest.revision: 8
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: MT
ms.sourcegitcommit: 4a36302d80f4bc397128e3838c9abf858a0b5fe8
ms.openlocfilehash: 68a5f199f389cb5bc24f0e648bb4719c1ad79545
ms.contentlocale: es-es
ms.lasthandoff: 09/06/2017

---
# <a name="idebugenumfieldgetvaluefromstringcaseinsensitive"></a>IDebugEnumField::GetValueFromStringCaseInsensitive
Este método usa una búsqueda entre mayúsculas y minúsculas para devolver el valor asociado con el nombre de una constante de enumeración.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
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
 [in] Cadena que especifica el nombre para el que se va a obtener el valor. Tenga en cuenta que en C++, es una cadena de caracteres anchos.  
  
 `pValue`  
 [out] Devuelve el valor numérico asociado.  
  
## <a name="return-value"></a>Valor devuelto  
 Si se realiza correctamente, devuelve `S_OK`; en caso contrario, devuelve `S_FALSE`, si el nombre no es parte de la enumeración o un código de error.  
  
## <a name="remarks"></a>Comentarios  
 Este método distingue mayúsculas de minúsculas. Si se requiere una búsqueda entre mayúsculas y minúsculas (por ejemplo, en un lenguaje como C++ donde nombres distinguen mayúsculas de minúsculas), utilice [GetValueFromString](../../../extensibility/debugger/reference/idebugenumfield-getvaluefromstring.md).  
  
## <a name="see-also"></a>Vea también  
 [IDebugEnumField](../../../extensibility/debugger/reference/idebugenumfield.md)   
 [GetValueFromString](../../../extensibility/debugger/reference/idebugenumfield-getvaluefromstring.md)
