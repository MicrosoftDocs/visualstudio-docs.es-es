---
title: "MODULE_SYMBOL_SEARCH_INFO | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "MODULE_SYMBOL_SEARCH_INFO"
helpviewer_keywords: 
  - "Estructura MODULE_SYMBOL_SEARCH_INFO"
ms.assetid: 432aff03-08a5-4c5a-b2d5-e212090fc70a
caps.latest.revision: 10
caps.handback.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
---
# MODULE_SYMBOL_SEARCH_INFO
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Contiene información de estado sobre las rutas de acceso de búsqueda de símbolos que se han buscado.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp#  
typedef struct _tagSYMBOL_SEARCH_INFO  
{  
   SYMBOL_SEARCH_INFO_FIELDS dwValidFields;  
   BSTR                      bstrVerboseSearchInfo;  
} MODULE_SYMBOL_SEARCH_INFO;  
```  
  
```c#  
public struct MODULE_SYMBOL_SEARCH_INFO {  
   public uint   dwValidFields;  
   public string bstrVerboseSearchInfo;  
}  
```  
  
#### <a name="parameters"></a>Parámetros  
 `dwValidFields`  
 Una combinación de indicadores de la [SYMBOL_SEARCH_INFO_FIELDS](../../../extensibility/debugger/reference/symbol-search-info-fields.md) enumeración que especifica el tipo de información de búsqueda descrita en esta estructura.  
  
 `bstrVerboseSearchInfo`  
 Ruta de acceso de búsqueda y resultados concatenados en una sola cadena.  
  
## <a name="remarks"></a>Comentarios  
 Esta estructura se devuelve de una llamada a la [GetSymbolInfo](../../../extensibility/debugger/reference/idebugmodule3-getsymbolinfo.md) método.  
  
 Si el `bstrVerboseSearchInfo` campo no está vacío, a continuación, contiene una lista de rutas de búsqueda y los resultados de búsqueda. La lista tiene un formato con una ruta de acceso, seguida de puntos suspensivos ("..."), seguidos por el resultado. Si hay más de un par de resultados de la ruta de acceso, cada par se separa mediante un par de "\r\n" (carro retorno y avance de línea). El patrón tiene el siguiente aspecto:  
  
 \< ruta de acceso>... \< resultado>\r\n \< ruta de acceso>... \< resultado>\r\n \< ruta de acceso>... \< resultados>  
  
 Tenga en cuenta que la última entrada no tiene una secuencia \r\n.  
  
 Esta es una posible `bstrVerboseSearchInfo` cadena que se ha enviado a la salida estándar.  
  
 `c:\symbols\user32.pdb... File not found.`  
  
 `c:\winnt\symbols\user32.pdb... Version does not match.`  
  
 `\\symbols\symbols\user32.dll\0a8sd0ad8ad\user32.pdb... Symbols loaded.`  
  
## <a name="requirements"></a>Requisitos  
 Encabezado: msdbg.h  
  
 Espacio de nombres: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vea también  
 [Estructuras y uniones](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [GetSymbolInfo](../../../extensibility/debugger/reference/idebugmodule3-getsymbolinfo.md)