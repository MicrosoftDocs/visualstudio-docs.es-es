---
title: IDebugProperty3::GetStringChars | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugProperty3::GetStringChars
helpviewer_keywords:
- IDebugProperty3::GetStringChars
ms.assetid: 832c37f3-85cb-4227-8ab2-f27a80eafe90
caps.latest.revision: 7
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 661cf6833c292d5ff4015649d494ee3a7d04fdbb
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "63419881"
---
# <a name="idebugproperty3getstringchars"></a>IDebugProperty3::GetStringChars
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

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
  
 [C++ solo], `rgString` es un puntero a un búfer que recibe los caracteres Unicode de la cadena. Este búfer debe ser al menos `buflen` caracteres (no bytes) de tamaño.  
  
 `pceltFetched`  
 [out] Donde se devuelve el número de caracteres que realmente se almacenan en el búfer. (Puede ser `NULL` en C++.)  
  
## <a name="return-value"></a>Valor devuelto  
 Si es correcto, devuelve `S_OK`; en caso contrario, devuelve un código de error.  
  
## <a name="remarks"></a>Comentarios  
 En C++, debe tener cuidado para asegurarse de que el búfer sea al menos `buflen` caracteres Unicode de longitud. Tenga en cuenta que un carácter Unicode es la longitud de 2 bytes.  
  
> [!NOTE]
> En C++, la cadena devuelta no incluye un carácter nulo de terminación. Si no especifica, `pceltFetched` a especificar el número de caracteres en la cadena.  
  
## <a name="example"></a>Ejemplo  
<!-- TODO: review snippet reference  [!CODE [[cpp]]([cpp])]  -->  
  
```  
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
```  
  
<!-- TODO: review snippet reference  [!CODE [}](})]  -->  
  
## <a name="see-also"></a>Vea también  
 [GetStringCharLength](../../../extensibility/debugger/reference/idebugproperty3-getstringcharlength.md)   
 [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)   
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)