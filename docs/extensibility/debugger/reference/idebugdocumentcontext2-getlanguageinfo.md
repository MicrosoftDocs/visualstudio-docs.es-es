---
title: IDebugDocumentContext2::GetLanguageInfo ? Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDocumentContext2::GetLanguageInfo
helpviewer_keywords:
- IDebugDocumentContext2::GetLanguageInfo
ms.assetid: 6a212ee5-414c-4eb5-ab11-19db1786943d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 9d139029bf65149ae59fb037434f6e7d6298f1d5
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80731860"
---
# <a name="idebugdocumentcontext2getlanguageinfo"></a>IDebugDocumentContext2::GetLanguageInfo
Obtiene el idioma asociado a este contexto de documento.

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT GetLanguageInfo(
    BSTR* pbstrLanguage,
    GUID* pguidLanguage
);
```

```csharp
int GetLanguageInfo(
    out string pbstrLanguage,
    out Guid   pguidLanguage
);
```

## <a name="parameters"></a>Parámetros
`pbstrLanguage`\
[fuera] Devuelve el nombre del lenguaje que implementa el código en este contexto de documento.

`pguidLanguage`\
[fuera] Devuelve el GUID del lenguaje que implementa el código en este contexto de documento. Por ejemplo, `guidVBScriptLang` o `guidCPPLang`. Este GUID no se limita [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)]a los idiomas proporcionados por .

## <a name="return-value"></a>Valor devuelto
Si la operación se realiza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.

## <a name="example"></a>Ejemplo
En el ejemplo siguiente se muestra `CDebugContext` cómo implementar este método para un objeto simple que expone el [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md) interfaz.

```cpp
HRESULT CDebugContext::GetLanguageInfo(BSTR* pbstrLanguage, GUID* pguidLanguage)
{
    HRESULT hr;

    // Check for a valid language argument pointers.
    if (pbstrLanguage && pguidLanguage)
    {
        *pguidLanguage = GUID_NULL;
        *pbstrLanguage = SysAllocString(L"Batch File");
        if (*pbstrLanguage)
        {
            *pguidLanguage = guidBatLang;
            hr = S_OK;
        }
        else
        {
            hr = E_OUTOFMEMORY;
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
