---
title: IDebugModule3::GetSymbolInfo ? Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugModule3::GetSymbolInfo
helpviewer_keywords:
- GetSymbolInfo method
- IDebugModule3::GetSymbolInfo method
ms.assetid: dda5e8e1-6878-4aa9-9ee4-e7d0dcc11210
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 3aafb28715f58eaba4499b47a2e1dee15b82ed14
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80726891"
---
# <a name="idebugmodule3getsymbolinfo"></a>IDebugModule3::GetSymbolInfo
Recupera una lista de rutas que se buscan símbolos, así como los resultados de buscar en cada ruta.

## <a name="syntax"></a>Sintaxis

```cpp
HRESULT GetSymbolInfo(
    SYMBOL_SEARCH_INFO_FIELDS  dwFields,
    MODULE_SYMBOL_SEARCH_INFO* pInfo
);
```

```csharp
int GetSymbolInfo(
    enum_SYMBOL_SEARCH_INFO_FIELDS dwFields,
    MODULE_SYMBOL_SEARCH_INFO[]    pinfo
);
```

## <a name="parameters"></a>Parámetros
`dwFields`\
[en] Una combinación de [SYMBOL_SEARCH_INFO_FIELDS](../../../extensibility/debugger/reference/symbol-search-info-fields.md) indicadores de la `pInfo` SYMBOL_SEARCH_INFO_FIELDS enumeración especificando qué campos de se deben rellenar.

`pInfo`\
[fuera] Una [estructura MODULE_SYMBOL_SEARCH_INFO](../../../extensibility/debugger/reference/module-symbol-search-info.md) cuyos miembros deben rellenarse con la información especificada. Si se trata de un `E_INVALIDARG`valor nulo, este método devuelve .

## <a name="return-value"></a>Valor devuelto
Si el método se `S_OK`realiza correctamente, devuelve ; de lo contrario, devuelve un código de error.

> [!NOTE]
> La cadena devuelta `MODULE_SYMBOL_SEARCH_INFO` (en la estructura) podría estar vacía incluso si `S_OK` se devuelve. En este caso, no había información de búsqueda para devolver.

## <a name="remarks"></a>Observaciones
Si `bstrVerboseSearchInfo` el campo `MODULE_SYMBOL_SEARCH_INFO` de la estructura no está vacío, contiene una lista de rutas de acceso buscadas y los resultados de esa búsqueda. La lista tiene un formato con una ruta de acceso, seguida de puntos suspensivos ("..."), seguido del resultado. Si hay más de un par de resultados de ruta de acceso, cada par está separado por un par de "-r-n" (carriage-return/linefeed). El patrón tiene este aspecto:

\<camino>... \<> ruta de\<acceso de>>... \<resultado>>\<de ruta de acceso... \<resultado>

Tenga en cuenta que la última entrada no tiene una secuencia de la lista.

## <a name="example"></a>Ejemplo
En este ejemplo, este método devuelve tres rutas de acceso con tres resultados de búsqueda diferentes. Cada línea se termina con un par de retorno de carro/alimentación de línea. La salida de ejemplo solo imprime los resultados de la búsqueda como una sola cadena.

> [!NOTE]
> Un resultado de estado es todo lo que sigue inmediatamente a la "..." hasta el final de la línea.

```cpp
void ShowSymbolSearchResults(IDebugModule3 *pIDebugModule3)
{
    MODULE_SYMBOL_SEARCH_INFO ssi = { 0 };
    HRESULT hr;
    hr = pIDebugModule3->GetSymbolInfo(SSIF_VERBOSE_SEARCH_INFO,&ssi);
    if (SUCCEEDED(hr)) {
        CComBSTR searchInfo = ssi.bstrVerboseSearchInfo;
        if (searchInfo.Length() != 0) {
            std::wcout << (wchar_t *)(BSTR)searchInfo;
            std::wcout << std::endl;
        }
    }
}
```

**c:-símbolos-user32.pdb... Archivo no encontrado.** 
 **c:'winnt'symbols'user32.pdb... La versión no coincide.** 
 **•símbolos, símbolos, user32.dll, 0a8sd0ad8ad, user32.pdb... \\ Símbolos cargados.**

## <a name="see-also"></a>Vea también

- [SYMBOL_SEARCH_INFO_FIELDS](../../../extensibility/debugger/reference/symbol-search-info-fields.md)
- [MODULE_SYMBOL_SEARCH_INFO](../../../extensibility/debugger/reference/module-symbol-search-info.md)
- [IDebugModule3](../../../extensibility/debugger/reference/idebugmodule3.md)
