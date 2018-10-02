---
title: MODULE_SYMBOL_SEARCH_INFO | Documentos de Microsoft
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- MODULE_SYMBOL_SEARCH_INFO
helpviewer_keywords:
- MODULE_SYMBOL_SEARCH_INFO structure
ms.assetid: 432aff03-08a5-4c5a-b2d5-e212090fc70a
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 074e837a1c0449420d7042539fb4c8dfa0396fe6
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "47578671"
---
# <a name="modulesymbolsearchinfo"></a>MODULE_SYMBOL_SEARCH_INFO
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

La versión más reciente de este tema puede encontrarse en [MODULE_SYMBOL_SEARCH_INFO](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/module-symbol-search-info).  
  
Contiene información de estado sobre las rutas de acceso de búsqueda de símbolos que se ha buscado.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp#  
typedef struct _tagSYMBOL_SEARCH_INFO  
{  
   SYMBOL_SEARCH_INFO_FIELDS dwValidFields;  
   BSTR                      bstrVerboseSearchInfo;  
} MODULE_SYMBOL_SEARCH_INFO;  
```  
  
```csharp  
public struct MODULE_SYMBOL_SEARCH_INFO {  
   public uint   dwValidFields;  
   public string bstrVerboseSearchInfo;  
}  
```  
  
#### <a name="parameters"></a>Parámetros  
 `dwValidFields`  
 Una combinación de marcas de la [SYMBOL_SEARCH_INFO_FIELDS](../../../extensibility/debugger/reference/symbol-search-info-fields.md) enumeración que especifica el tipo de información de búsqueda descrito en esta estructura.  
  
 `bstrVerboseSearchInfo`  
 Ruta de acceso de búsqueda y resultados concatenados en una sola cadena.  
  
## <a name="remarks"></a>Comentarios  
 Esta estructura se devuelve desde una llamada a la [GetSymbolInfo](../../../extensibility/debugger/reference/idebugmodule3-getsymbolinfo.md) método.  
  
 Si el `bstrVerboseSearchInfo` campo no está vacío, a continuación, contiene una lista de rutas de acceso que buscará y los resultados de la búsqueda. La lista está formateada con una ruta de acceso, seguido de puntos suspensivos ("..."), seguidos por el resultado. Si hay más de un par de resultados de la ruta de acceso, cada par se separa mediante un par de "\r\n" (carro retorno/avance de línea). El patrón tiene este aspecto:  
  
 \<ruta de acceso >... \<resultado > \r\n\<ruta de acceso >... \<resultado > \r\n\<ruta de acceso >... \<resultado >  
  
 Tenga en cuenta que la última entrada no tiene una secuencia \r\n.  
  
 Este es un posible `bstrVerboseSearchInfo` cadena que se ha enviado a la salida estándar.  
  
 `c:\symbols\user32.pdb... File not found.`  
  
 `c:\winnt\symbols\user32.pdb... Version does not match.`  
  
 `\\symbols\symbols\user32.dll\0a8sd0ad8ad\user32.pdb... Symbols loaded.`  
  
## <a name="requirements"></a>Requisitos  
 Encabezado: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vea también  
 [Estructuras y uniones](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [GetSymbolInfo](../../../extensibility/debugger/reference/idebugmodule3-getsymbolinfo.md)

