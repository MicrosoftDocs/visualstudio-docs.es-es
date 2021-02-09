---
title: 'IDebugProperty3:: GetStringChars | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProperty3::GetStringChars
helpviewer_keywords:
- IDebugProperty3::GetStringChars
ms.assetid: 832c37f3-85cb-4227-8ab2-f27a80eafe90
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 8b188b386dea7279530e186073847e26915af63d
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99897286"
---
# <a name="idebugproperty3getstringchars"></a>IDebugProperty3::GetStringChars
Recupera la cadena asociada a esta propiedad y la almacena en un búfer proporcionado por el usuario.

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

## <a name="parameters"></a>Parámetros
`buflen`\
de Número máximo de caracteres que puede contener el búfer proporcionado por el usuario.

`rgString`\
enuncia Devuelve la cadena.

 [Solo C++], `rgString` es un puntero a un búfer que recibe los caracteres Unicode de la cadena. Este búfer debe tener un `buflen` tamaño mínimo de caracteres (no de bytes).

`pceltFetched`\
enuncia Donde se devuelve el número de caracteres almacenados realmente en el búfer. (Puede estar `NULL` en C++).

## <a name="return-value"></a>Valor devuelto
Si es correcto, devuelve `S_OK` ; de lo contrario, devuelve un código de error.

## <a name="remarks"></a>Notas
En C++, se debe tener cuidado para asegurarse de que el búfer tiene al menos `buflen` caracteres Unicode. Tenga en cuenta que un carácter Unicode tiene una longitud de 2 bytes.

> [!NOTE]
> En C++, la cadena devuelta no incluye un carácter nulo de terminación. Si se especifica, `pceltFetched` especificará el número de caracteres de la cadena.

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
- [GetStringCharLength](../../../extensibility/debugger/reference/idebugproperty3-getstringcharlength.md)
- [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
