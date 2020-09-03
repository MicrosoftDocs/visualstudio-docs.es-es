---
title: 'IDebugModule3:: GetSymbolInfo | Microsoft Docs'
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "80726891"
---
# <a name="idebugmodule3getsymbolinfo"></a>IDebugModule3::GetSymbolInfo
Recupera una lista de rutas de acceso en las que se buscan símbolos, así como los resultados de buscar en cada ruta.

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
de Combinación de marcas de la enumeración [SYMBOL_SEARCH_INFO_FIELDS](../../../extensibility/debugger/reference/symbol-search-info-fields.md) que especifica los campos de que se van `pInfo` a rellenar.

`pInfo`\
enuncia Estructura de [MODULE_SYMBOL_SEARCH_INFO](../../../extensibility/debugger/reference/module-symbol-search-info.md) cuyos miembros se van a rellenar con la información especificada. Si es un valor null, este método devuelve `E_INVALIDARG` .

## <a name="return-value"></a>Valor devuelto
Si el método se ejecuta correctamente, devuelve `S_OK` ; de lo contrario, devuelve un código de error.

> [!NOTE]
> La cadena devuelta (en la `MODULE_SYMBOL_SEARCH_INFO` estructura) puede estar vacía aunque `S_OK` se devuelva. En este caso, no había información de búsqueda para devolver.

## <a name="remarks"></a>Observaciones
Si el `bstrVerboseSearchInfo` campo de la `MODULE_SYMBOL_SEARCH_INFO` estructura no está vacío, contiene una lista de rutas de acceso de búsqueda y los resultados de esa búsqueda. Se da formato a la lista con una ruta de acceso, seguida de un botón de puntos suspensivos ("..."), seguido del resultado. Si hay más de un par de resultados de ruta de acceso, cada par está separado por un par "\r\n" (retorno de carro/avance de bits). El patrón tiene el siguiente aspecto:

\<path>...\<result> \r\n \<path> ... \<result> \r\n \<path> ...\<result>

Tenga en cuenta que la última entrada no tiene una secuencia \r\n.

## <a name="example"></a>Ejemplo
En este ejemplo, este método devuelve tres rutas de acceso con tres resultados de búsqueda diferentes. Cada línea finaliza con un par de retorno de carro/avance de línea. La salida del ejemplo solo imprime los resultados de la búsqueda como una sola cadena.

> [!NOTE]
> Un resultado de estado es todo lo que sigue inmediatamente A "..." hasta el final de la línea.

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

**c:\symbols\user32.pdb... No se encontró el archivo.** 
 **c:\winnt\symbols\user32.pdb... La versión no coincide.** 
 ** \\\symbols\symbols\user32.dll \0a8sd0ad8ad\user32.pdb... Símbolos cargados.**

## <a name="see-also"></a>Vea también

- [SYMBOL_SEARCH_INFO_FIELDS](../../../extensibility/debugger/reference/symbol-search-info-fields.md)
- [MODULE_SYMBOL_SEARCH_INFO](../../../extensibility/debugger/reference/module-symbol-search-info.md)
- [IDebugModule3](../../../extensibility/debugger/reference/idebugmodule3.md)
