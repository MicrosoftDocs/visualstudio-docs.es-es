---
title: IDebugModule3::GetSymbolInfo | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugModule3::GetSymbolInfo
helpviewer_keywords:
- GetSymbolInfo method
- IDebugModule3::GetSymbolInfo method
ms.assetid: dda5e8e1-6878-4aa9-9ee4-e7d0dcc11210
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 53d84b9ef6cdabc12c88e30fc65d506cad673a26
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="idebugmodule3getsymbolinfo"></a>IDebugModule3::GetSymbolInfo
Recupera una lista de rutas de acceso que se buscan los símbolos, así como los resultados de búsqueda de cada ruta de acceso.  
  
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
 [in] Una combinación de indicadores de la [SYMBOL_SEARCH_INFO_FIELDS](../../../extensibility/debugger/reference/symbol-search-info-fields.md) enumeración que especifica qué campos de `pInfo` deben rellenarse.  
  
 `pInfo`  
 [out] A [MODULE_SYMBOL_SEARCH_INFO](../../../extensibility/debugger/reference/module-symbol-search-info.md) estructura cuyos miembros son que debe rellenarse con la información especificada. Si este es un valor null, este método devuelve `E_INVALIDARG`.  
  
## <a name="return-value"></a>Valor devuelto  
 Si el método se realiza correctamente, devuelve `S_OK`; en caso contrario, devuelve un código de error.  
  
> [!NOTE]
>  La cadena devuelta (en el `MODULE_SYMBOL_SEARCH_INFO` estructura) podría estar vacío aunque `S_OK` se devuelve. En este caso, no había ninguna información de búsqueda para devolver.  
  
## <a name="remarks"></a>Comentarios  
 Si el `bstrVerboseSearchInfo` campo de la `MODULE_SYMBOL_SEARCH_INFO` estructura no está vacía, a continuación, contiene una lista de rutas de búsqueda y los resultados de búsqueda. La lista está formateada con una ruta de acceso, seguido de un botón de puntos suspensivos ("..."), seguido por el resultado. Si hay más de un par de resultados de la ruta de acceso, cada par se separa con un par de "\r\n" (carro retorno/avance de línea). El patrón tiene el siguiente aspecto:  
  
 \<ruta de acceso >... \<resultado > \r\n\<ruta de acceso >... \<resultado > \r\n\<ruta de acceso >... \<resultado >  
  
 Tenga en cuenta que la última entrada no tiene una secuencia \r\n.  
  
## <a name="example"></a>Ejemplo  
 En este ejemplo, este método devuelve tres rutas de acceso con tres resultados diferentes. Cada línea se termina con un par de retorno de carro/avance de línea. El resultado del ejemplo se limita a imprimir los resultados de búsqueda como una sola cadena.  
  
> [!NOTE]
>  Un resultado de estado es todo lo inmediatamente después de "..." hasta el final de la línea.  
  
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
**\\\symbols\symbols\user32.dll\0a8sd0ad8ad\user32.pdb... Símbolos cargados.**   
## <a name="see-also"></a>Vea también  
 [SYMBOL_SEARCH_INFO_FIELDS](../../../extensibility/debugger/reference/symbol-search-info-fields.md)   
 [MODULE_SYMBOL_SEARCH_INFO](../../../extensibility/debugger/reference/module-symbol-search-info.md)   
 [IDebugModule3](../../../extensibility/debugger/reference/idebugmodule3.md)