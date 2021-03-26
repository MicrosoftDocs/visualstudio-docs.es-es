---
description: Recupera una lista de todos los contextos de código asociados a este contexto de documento.
title: 'IDebugDocumentContext2:: EnumCodeContexts | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDocumentContext2::EnumCodeContexts
helpviewer_keywords:
- IDebugDocumentContext2::EnumCodeContexts
ms.assetid: 627af69c-5cce-4e1d-8233-5f4d8dbc62e5
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 99f60cd99a694c6f2610982a2b85fe2dbce1282b
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/25/2021
ms.locfileid: "105066703"
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

## <a name="remarks"></a>Observaciones
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

## <a name="see-also"></a>Consulte también
- [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)
- [IEnumDebugCodeContexts2](../../../extensibility/debugger/reference/ienumdebugcodecontexts2.md)
