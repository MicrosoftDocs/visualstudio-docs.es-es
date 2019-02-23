---
title: IDebugExpressionEvaluator3::Parse2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugExpressionEvaluator3::Parse2
ms.assetid: 78099628-d600-4f76-b7c8-ee07c864af1e
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 626911d4eb9f23655ad2808e1e79ec6635cb8b00
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/22/2019
ms.locfileid: "56678610"
---
# <a name="idebugexpressionevaluator3parse2"></a>IDebugExpressionEvaluator3::Parse2
Convierte una cadena de expresión en una expresión analizada según el proveedor de símbolos y la dirección del marco de evaluación.

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

#### <a name="parameters"></a>Parámetros
`upstrExpression`

 [in] La cadena de expresión que se va a analizar.

`dwFlags`

 [in] Una colección de [PARSEFLAGS](../../../extensibility/debugger/reference/parseflags.md) constantes que determinan cómo se puede analizar la expresión.

`nRadix`

 [in] Base que se usará para interpretar toda la información numérica.

`pSymbolProvider`

 [in] Interfaz del proveedor de símbolos.

`pAddress`

 [in] Dirección del marco de evaluación.

`pbstrError`

 [out] Devuelve el error como texto legible.

`pichError`

 [out] Devuelve la posición del carácter de inicio del error en la cadena de expresión.

`ppParsedExpression`

 [out] Devuelve la expresión analizada en un [IDebugParsedExpression](../../../extensibility/debugger/reference/idebugparsedexpression.md) objeto.

## <a name="return-value"></a>Valor devuelto
Si es correcto, devuelve `S_OK`; en caso contrario, devuelve un código de error.

## <a name="remarks"></a>Comentarios
Este método produce una expresión analizada, no un valor real. Una expresión analizada está lista para ser evaluada, es decir, convertir en un valor.

## <a name="example"></a>Ejemplo
El ejemplo siguiente muestra cómo implementar este método para un **CEE** objeto que expone el [IDebugExpressionEvaluator3](../../../extensibility/debugger/reference/idebugexpressionevaluator3.md) interfaz.

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
