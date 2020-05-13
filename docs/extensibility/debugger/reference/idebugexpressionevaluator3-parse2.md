---
title: IDebugExpressionEvaluator3::Parse2 ? Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugExpressionEvaluator3::Parse2
ms.assetid: 78099628-d600-4f76-b7c8-ee07c864af1e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 5254d30ed1a656bfd357fca822efa554d895807e
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80729133"
---
# <a name="idebugexpressionevaluator3parse2"></a>IDebugExpressionEvaluator3::Parse2
Convierte una cadena de expresión en una expresión analizada dado el proveedor de símbolos y la dirección del marco de evaluación.

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT Parse2 (
    LPCOLESTR                upstrExpression,
    PARSEFLAGS               dwFlags,
    UINT                     nRadix,
    IDebugSymbolProvider*    pSymbolProvider,
    IDebugAddress*           pAddress,
    BSTR*                    pbstrError,
    UINT*                    pichError,
    IDebugParsedExpression** ppParsedExpression
);
```

```csharp
HRESULT Parse2 (
    string                     upstrExpression,
    enum_PARSEFLAGS            dwFlags,
    uint                       nRadix,
    IDebugSymbolProvider       pSymbolProvider,
    IDebugAddress              pAddress,
    out string                 pbstrError,
    out uint                   pichError,
    out IDebugParsedExpression ppParsedExpression
);
```

## <a name="parameters"></a>Parámetros
`upstrExpression`\
[en] La cadena de expresión que se va a analizar.

`dwFlags`\
[en] Colección de constantes [PARSEFLAGS](../../../extensibility/debugger/reference/parseflags.md) que determinan cómo se va a analizar la expresión.

`nRadix`\
[en] Radix que se utilizará para interpretar cualquier información numérica.

`pSymbolProvider`\
[en] Interfaz del proveedor de símbolos.

`pAddress`\
[en] Dirección del marco de evaluación.

`pbstrError`\
[fuera] Devuelve el error como texto legible.

`pichError`\
[fuera] Devuelve la posición del carácter del inicio del error en la cadena de expresión.

`ppParsedExpression`\
[fuera] Devuelve la expresión analizada en un [IDebugParsedExpression](../../../extensibility/debugger/reference/idebugparsedexpression.md) objeto.

## <a name="return-value"></a>Valor devuelto
Si la operación se realiza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.

## <a name="remarks"></a>Observaciones
Este método genera una expresión analizada, no un valor real. Una expresión analizada está lista para evaluarse, es decir, convertirse en un valor.

## <a name="example"></a>Ejemplo
En el ejemplo siguiente se muestra cómo implementar este método para un OBJETO **CEE** que expone la interfaz [IDebugExpressionEvaluator3.](../../../extensibility/debugger/reference/idebugexpressionevaluator3.md)

```cpp
HRESULT CEE::Parse2 ( LPCOLESTR in_szExprText,
  PARSEFLAGS in_FLAGS,
  UINT in_RADIX,
  IDebugSymbolProvider *pSymbolProvider,
  IDebugAddress *pAddress,
  BSTR* out_pbstrError,
  UINT* inout_pichError,
  IDebugParsedExpression** out_ppParsedExpression )
{
    // precondition
    REQUIRE( NULL != in_szExprText );
    //REQUIRE( NULL != out_pbstrError );
    REQUIRE( NULL != inout_pichError );
    REQUIRE( NULL != out_ppParsedExpression );

    if (NULL == in_szExprText)
        return E_INVALIDARG;

    if (NULL == inout_pichError)
        return E_POINTER;

    if (NULL == out_ppParsedExpression)
        return E_POINTER;

    if (out_pbstrError)
        *out_pbstrError = NULL;

    *out_ppParsedExpression = NULL;

    INVARIANT( this );

    if (!this->ClassInvariant())
        return E_UNEXPECTED;

    // function body
    EEDomain::fParseExpression DomainVal =
    {
        this,                   // CEE*
        in_szExprText,          // LPCOLESTR
        in_FLAGS,               // EVALFLAGS
        in_RADIX,               // RADIX
        out_pbstrError,         // BSTR*
        inout_pichError,        // UINT*
        pSymbolProvider,
        out_ppParsedExpression  // Output
    };

    return (*m_LanguageSpecificUseCases.pfParseExpression)(DomainVal);
}
```

## <a name="see-also"></a>Vea también
- [IDebugExpressionEvaluator3](../../../extensibility/debugger/reference/idebugexpressionevaluator3.md)
