---
title: "IDebugModule3::GetSymbolInfo | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugModule3::GetSymbolInfo"
helpviewer_keywords: 
  - "Método GetSymbolInfo"
  - "IDebugModule3::GetSymbolInfo (método)"
ms.assetid: dda5e8e1-6878-4aa9-9ee4-e7d0dcc11210
caps.latest.revision: 17
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 17
---
# IDebugModule3::GetSymbolInfo
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Recupera una lista de rutas de acceso que se buscan los símbolos, así como los resultados de la búsqueda de cada ruta de acceso.  
  
## Sintaxis  
  
```cpp#  
HRESULT GetSymbolInfo(  
   SYMBOL_SEARCH_INFO_FIELDS  dwFields,  
   MODULE_SYMBOL_SEARCH_INFO* pInfo  
);  
```  
  
```c#  
int GetSymbolInfo(  
   enum_SYMBOL_SEARCH_INFO_FIELDS dwFields,   
   MODULE_SYMBOL_SEARCH_INFO[]    pinfo  
);  
  
```  
  
#### Parámetros  
 `dwFields`  
 \[in\] Una combinación de indicadores de la [SYMBOL\_SEARCH\_INFO\_FIELDS](../../../extensibility/debugger/reference/symbol-search-info-fields.md) enumeración especifica qué campos de `pInfo` deben rellenarse.  
  
 `pInfo`  
 \[out\] Un [MODULE\_SYMBOL\_SEARCH\_INFO](../../../extensibility/debugger/reference/module-symbol-search-info.md) estructura cuyos miembros se rellenará con la información especificada. Si es un valor null, este método devuelve `E_INVALIDARG`.  
  
## Valor devuelto  
 Si el método se ejecuta correctamente, devuelve `S_OK`; en caso contrario, devuelve un código de error.  
  
> [!NOTE]
>  La cadena devuelta \(en el `MODULE_SYMBOL_SEARCH_INFO` estructura\) puede estar vacía aunque `S_OK` se devuelve. En este caso, no había ninguna información de búsqueda para devolver.  
  
## Comentarios  
 Si el `bstrVerboseSearchInfo` campo de la `MODULE_SYMBOL_SEARCH_INFO` estructura no está vacía, contiene una lista de rutas de acceso que se buscan y los resultados de la búsqueda. La lista tiene un formato con una ruta de acceso, seguida de puntos suspensivos \("..."\), seguidos por el resultado. Si hay más de un par de resultados de la ruta de acceso, cada par se separa mediante un par de "\\r\\n" \(carro retorno y avance de línea\). El patrón tiene el siguiente aspecto:  
  
 \< rutaDeAcceso \>... \< resultado \> \\r\\n \< rutaDeAcceso \>... \< resultado \> \\r\\n \< rutaDeAcceso \>... \< resultado \>  
  
 Tenga en cuenta que la última entrada no tiene una secuencia \\r\\n.  
  
## Ejemplo  
 En este ejemplo, este método devuelve tres rutas con tres resultados diferentes. Cada línea se termina con un par de retorno de carro\/avance de línea. La salida de ejemplo sólo imprime los resultados de búsqueda como una sola cadena.  
  
> [!NOTE]
>  Un resultado de estado es todo lo que sigue inmediatamente "..." hasta el final de la línea.  
  
```cpp#  
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
  
 **c:\\symbols\\user32.pdb... No se encontró el archivo. c:\\winnt\\symbols\\user32.pdb... Versión no coincide. \\\\symbols\\symbols\\user32.dll\\0a8sd0ad8ad\\user32.pdb... Cargar los símbolos.**   
## Vea también  
 [SYMBOL\_SEARCH\_INFO\_FIELDS](../../../extensibility/debugger/reference/symbol-search-info-fields.md)   
 [MODULE\_SYMBOL\_SEARCH\_INFO](../../../extensibility/debugger/reference/module-symbol-search-info.md)   
 [IDebugModule3](../../../extensibility/debugger/reference/idebugmodule3.md)