---
title: IDebugDocumentContext2::GetName ? Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDocumentContext2::GetName
helpviewer_keywords:
- IDebugDocumentContext2::GetName
ms.assetid: 546c5b2e-f166-4edb-9e61-57d797ca98a1
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 253ef509a60e8bb2ce177235f4b93b370e66f484
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80731808"
---
# <a name="idebugdocumentcontext2getname"></a>IDebugDocumentContext2::GetName
Obtiene el nombre que se puede mostrar del documento que contiene este contexto de documento.

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT GetName(
    GETNAME_TYPE gnType,
    BSTR*        pbstrFileName
);
```

```csharp
int GetName(
    enum_GETNAME_TYPE  gnType,
    out string         pbstrFileName
);
```

## <a name="parameters"></a>Parámetros
`gnType`\
[en] Valor de la [enumeración GETNAME_TYPE](../../../extensibility/debugger/reference/getname-type.md) que especifica el tipo de nombre que se va a devolver.

`pbstrFileName`\
[out] Devuelve el nombre del archivo.

## <a name="return-value"></a>Valor devuelto
Si la operación se realiza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.

## <a name="remarks"></a>Observaciones
Este método normalmente reenvía la llamada a la [GetName](../../../extensibility/debugger/reference/idebugdocument2-getname.md) método, a menos que el contexto del documento se escribe para almacenar el propio nombre del documento (como se muestra en el ejemplo).

## <a name="example"></a>Ejemplo
En el ejemplo siguiente se muestra `CDebugContext` cómo implementar este método para un objeto simple que expone el [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md) interfaz.

```cpp
HRESULT CDebugContext::GetName(GETNAME_TYPE gnType, BSTR* pbstrFileName)
{
    HRESULT hr;

    // Check for a valid file name argument.
    if (pbstrFileName)
    {
        *pbstrFileName = NULL;

        switch (gnType)
        {
            case GN_NAME:
            case GN_FILENAME:
            {
                // Copy the member file name into the local file name.
                *pbstrFileName = SysAllocString(m_sbstrFileName);
                // Check for successful copy.
                hr = (*pbstrFileName) ? S_OK : E_OUTOFMEMORY;
                break;
            }
            default:
            {
                hr = E_FAIL;
                break;
            }
        }
    }
    else
    {
        hr = E_INVALIDARG;
    }

    return hr;
}
```

## <a name="see-also"></a>Vea también
- [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)
- [GETNAME_TYPE](../../../extensibility/debugger/reference/getname-type.md)
