---
title: IDebugProperty3::GetStringChars | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugProperty3::GetStringChars
helpviewer_keywords:
- IDebugProperty3::GetStringChars
ms.assetid: 832c37f3-85cb-4227-8ab2-f27a80eafe90
caps.latest.revision: 7
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
ms.openlocfilehash: f84c744eef8dab863ec9a91aec621764dfa3c266
ms.contentlocale: es-es
ms.lasthandoff: 09/26/2017

---
# <a name="idebugproperty3getstringchars"></a>IDebugProperty3::GetStringChars
Recupera la cadena asociada a esta propiedad y lo almacena en un búfer proporcionado por el usuario.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
HRESULT GetStringChars(  
   ULONG  buflen,  
   WCHAR* rgString,  
   ULONG* pceltFetched  
);  
```  
  
```csharp  
int GetStringChars(  
   uint       buflen,   
   out string rgString,   
   out uint   pceltFetched  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `buflen`  
 [in] Número máximo de caracteres que puede contener el búfer proporcionado por el usuario.  
  
 `rgString`  
 [out] Devuelve la cadena.  
  
 [Solo en C++], `rgString` es un puntero a un búfer que recibe los caracteres Unicode de la cadena. Este búfer debe ser al menos `buflen` caracteres (no bytes) de tamaño.  
  
 `pceltFetched`  
 [out] Donde se devuelve el número de caracteres que se almacenan en realidad en el búfer. (Puede ser `NULL` en C++.)  
  
## <a name="return-value"></a>Valor devuelto  
 Si se realiza correctamente, devuelve `S_OK`; en caso contrario, devuelve un código de error.  
  
## <a name="remarks"></a>Comentarios  
 En C++, debe tener cuidado para asegurarse de que el búfer sea al menos `buflen` caracteres Unicode de longitud. Tenga en cuenta que un carácter Unicode es una longitud de 2 bytes.  
  
> [!NOTE]
>  En C++, la cadena devuelta no incluye un carácter nulo de terminación. Si no especifica, `pceltFetched` especificará el número de caracteres en la cadena.  
  
## <a name="example"></a>Ejemplo  
 
```cpp  
CStringW RetrievePropertyString(IDebugProperty2 *pPropInfo)  
{  
    CStringW returnString = L"";  
    CComQIPtr<IDebugProperty3> pProp3 = pPropInfo->pProperty;  
    If (pProp3 != NULL) {  
        ULONG dwStrLen = 0;  
        HRESULT hr;  
        hr = pProp3->GetStringCharLength(&dwStrLen);  
        if (SUCCEEDED(hr) && dwStrLen > 0) {  
            ULONG dwRead;  
            CStrBufW buf(returnString,dwStrLen,CStrBuf::SET_LENGTH);  
            hr = pProp3->GetStringChars(dwStrLen,  
                                        reinterpret_cast<WCHAR*>(static_cast<CStringW::PXSTR>(buf)),  
                                        &dwRead);  
        }  
    }  
    return(returnString);
}
```    
  
## <a name="see-also"></a>Vea también  
 [GetStringCharLength](../../../extensibility/debugger/reference/idebugproperty3-getstringcharlength.md)   
 [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)   
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
