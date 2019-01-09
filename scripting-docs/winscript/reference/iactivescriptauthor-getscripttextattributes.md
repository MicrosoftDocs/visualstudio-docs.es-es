---
title: IActiveScriptAuthor::GetScriptTextAttributes | Documentos de Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptAuthor.GetScriptTextAttributes
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptAuthor::GetScriptTextAttributes
ms.assetid: a53451de-cc5c-4b53-8e5f-81e196364caf
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 57513e51248e26e39f95871e0dad329e8cc2f82c
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/08/2019
ms.locfileid: "54094710"
---
# <a name="iactivescriptauthorgetscripttextattributes"></a>IActiveScriptAuthor::GetScriptTextAttributes
Devuelve los atributos de texto de un bloque de script.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
HRESULT GetScriptTextAttributes(  
    LPCOLESTR        pszCode,  
    ULONG            cch,  
    LPCOLESTR        pszDelimiter,  
    DWORD            dwFlags,  
    SOURCE_TEXT_ATTR *pattr);  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `pszCode`  
 [in, size_is (`cch`)] el texto del bloque de script. Esta cadena no tiene que estar terminado en null.  
  
 `cch`  
 [in] El tamaño usado para la `pszCode` y `pattr` parámetros.  
  
 `pszDelimiter`  
 [in] La dirección del delimitador de fin de secuencia de comandos. Cuando `pszCode` se analiza desde una secuencia de texto, el host normalmente utiliza un delimitador (por ejemplo, dos comillas simples), para detectar el final del scriptlet. Establezca este parámetro en NULL si no hay ningún delimitador para identificar el final del bloque de script.  
  
 `dwFlags`  
 [in] Marcas que están asociadas con los atributos de texto del bloque de script. Puede ser una combinación de los siguientes valores:  
  
|Constante|Valor|Descripción|  
|--------------|-----------|-----------------|  
|GETATTRTYPE_DEPSCAN|0 x 0001|Identificar los identificadores que tienen el atributo SOURCETEXT_ATTR_IDENTIFIER e identificar los operadores de puntos que tienen el atributo SOURCETEXT_ATTR_MEMBERLOOKUP.|  
|GETATTRFLAG_THIS|0 x 0100|Identificar el objeto actual que tiene el atributo SOURCETEXT_ATTR_THIS.|  
|GETATTRFLAG_HUMANTEXT|0 x 8000|Identificar el texto de comentario y el contenido de cadena que tiene el atributo SOURCETEXT_ATTR_HUMANTEXT.|  
  
 `pattr`  
 [in, out, size_is (`cch`)] la información de color para el código del bloque de script.  
  
## <a name="return-value"></a>Valor devuelto  
 Una clase `HRESULT`. Entre los valores posibles se incluyen los que se indican en la tabla siguiente, entre otros.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`S_OK`|El método se realizó correctamente.|  
  
## <a name="remarks"></a>Comentarios  
  
## <a name="see-also"></a>Vea también  
 [IActiveScriptAuthor (interfaz)](../../winscript/reference/iactivescriptauthor-interface.md)   
 [SOURCE_TEXT_ATTR (Enumeración)](../../winscript/reference/source-text-attr-enumeration.md)