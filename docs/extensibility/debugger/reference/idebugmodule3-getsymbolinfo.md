---
title: IDebugModule3::GetSymbolInfo | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugModule3::GetSymbolInfo
helpviewer_keywords:
- GetSymbolInfo method
- IDebugModule3::GetSymbolInfo method
ms.assetid: dda5e8e1-6878-4aa9-9ee4-e7d0dcc11210
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8273a8111eb087202a1b97ec042e8d1bd21f637a
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/25/2019
ms.locfileid: "54992833"
---
# <a name="idebugmodule3getsymbolinfo"></a>IDebugModule3::GetSymbolInfo
Recupera una lista de rutas de acceso que se buscan los símbolos, así como los resultados de búsqueda en cada ruta de acceso.  
  
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
  
#### <a name="parameters"></a>Parámetros  
 `dwFields`  
 [in] Una combinación de marcas de la [SYMBOL_SEARCH_INFO_FIELDS](../../../extensibility/debugger/reference/symbol-search-info-fields.md) enumeración que especifica qué campos de `pInfo` deben rellenarse.  
  
 `pInfo`  
 [out] Un [MODULE_SYMBOL_SEARCH_INFO](../../../extensibility/debugger/reference/module-symbol-search-info.md) estructura cuyos miembros se va a rellenar con la información especificada. Si este es un valor null, este método devuelve `E_INVALIDARG`.  
  
## <a name="return-value"></a>Valor devuelto  
 Si el método se realiza correctamente, devuelve `S_OK`; en caso contrario, devuelve un código de error.  
  
> [!NOTE]
>  La cadena devuelta (en el `MODULE_SYMBOL_SEARCH_INFO` estructura) pueden estar vacíos aunque `S_OK` se devuelve. En este caso, no hubo ninguna información de búsqueda que devolver.  
  
## <a name="remarks"></a>Comentarios  
 Si el `bstrVerboseSearchInfo` campo de la `MODULE_SYMBOL_SEARCH_INFO` estructura no está vacía y, después, contiene una lista de rutas de acceso que buscará y los resultados de la búsqueda. La lista está formateada con una ruta de acceso, seguido de puntos suspensivos ("..."), seguido por el resultado. Si hay más de un par de resultados de la ruta de acceso, cada par se separa mediante un par de "\r\n" (carro retorno/avance de línea). El patrón tiene este aspecto:  
  
 \<ruta de acceso >... \<resultado > \r\n\<ruta de acceso >... \<resultado > \r\n\<ruta de acceso >... \<resultado >  
  
 Tenga en cuenta que la última entrada no tiene una secuencia \r\n.  
  
## <a name="example"></a>Ejemplo  
 En este ejemplo, este método devuelve tres rutas de acceso con tres resultados diferentes. Cada línea se termina con un par de retorno de carro/avance de línea. La salida de ejemplo sólo imprime los resultados de búsqueda como una sola cadena.  
  
> [!NOTE]
>  Un resultado de estado es todo lo que sigue inmediatamente "..." hasta el final de la línea.  
  
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
**c:\winnt\symbols\user32.pdb... Versión no coincide.**  
**\\\symbols\symbols\user32.dll\0a8sd0ad8ad\user32.pdb... Símbolos cargados.**   
## <a name="see-also"></a>Vea también  
 [SYMBOL_SEARCH_INFO_FIELDS](../../../extensibility/debugger/reference/symbol-search-info-fields.md)   
 [MODULE_SYMBOL_SEARCH_INFO](../../../extensibility/debugger/reference/module-symbol-search-info.md)   
 [IDebugModule3](../../../extensibility/debugger/reference/idebugmodule3.md)