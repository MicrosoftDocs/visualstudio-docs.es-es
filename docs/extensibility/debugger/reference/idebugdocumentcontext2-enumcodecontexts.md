---
title: 'IDebugDocumentContext2:: EnumCodeContexts | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDocumentContext2::EnumCodeContexts
helpviewer_keywords:
- IDebugDocumentContext2::EnumCodeContexts
ms.assetid: 627af69c-5cce-4e1d-8233-5f4d8dbc62e5
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 089122a4a4d7ff3d6a8828ba0c251efd3729c101
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99933549"
---
# <a name="idebugdocumentcontext2enumcodecontexts"></a>IDebugDocumentContext2::EnumCodeContexts
Recupera una lista de todos los contextos de código asociados a este contexto de documento.

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT EnumCodeContexts(
    IEnumDebugCodeContexts2** ppEnumCodeCxts
);
```

```csharp
int EnumCodeContexts(
    out IEnumDebugCodeContexts2 ppEnumCodeCxts
);
```

## <a name="parameters"></a>Parámetros
`ppEnumCodeCxts`\

## <a name="return-value"></a>Valor devuelto
Si la operación se realiza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.

## <a name="remarks"></a>Notas
Un único contexto de documento puede generar varios contextos de código cuando el documento usa plantillas o archivos de inclusión.

## <a name="example"></a>Ejemplo
En el ejemplo siguiente se muestra cómo implementar este método para un `CDebugContext` objeto simple que expone la interfaz [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md) .

```cpp
HRESULT CDebugContext::EnumCodeContexts(IEnumDebugCodeContexts2 **ppEnumCodeCxts)
{
    HRESULT hr;

    // Check for a valid IEnumDebugCodeContexts2 interface pointer.
    if (ppEnumCodeCxts)
    {
        *ppEnumCodeCxts = NULL;

        // Create a CEnumDebugCodeContexts object.
        CComObject<CEnumDebugCodeContexts>* pEnum;
        hr = CComObject<CEnumDebugCodeContexts>::CreateInstance(&pEnum);
        assert(hr == S_OK);
        if (hr == S_OK)
        {
            // Get an IID_IDebugCodeContext2 interface.
            CComPtr<IDebugCodeContext2> spCodeCxt;
            hr = QueryInterface(IID_IDebugCodeContext2,
                                (void**)&spCodeCxt);
            assert(hr == S_OK);
            if (hr == S_OK)
            {
                // Initialize the code context enumerator with the
                // IDebugCodeContext2 information.
                IDebugCodeContext2* rgpCodeContext[] = { spCodeCxt.p };
                hr = pEnum->Init(rgpCodeContext,
                                 &(rgpCodeContext[1]),
                                 NULL,
                                 AtlFlagCopy);
                assert(hr == S_OK);
                if (hr == S_OK)
                {
                // Set the passed IEnumDebugCodeContexts2 pointer equal to the pointer
                // value of the created CEnumDebugCodeContexts object.
                hr = pEnum->QueryInterface(ppEnumCodeCxts);
                assert(hr == S_OK);
                }
            }

            // Otherwise, delete the CEnumDebugCodeContexts object.
            if (FAILED(hr))
            {
                delete pEnum;
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
- [IEnumDebugCodeContexts2](../../../extensibility/debugger/reference/ienumdebugcodecontexts2.md)
