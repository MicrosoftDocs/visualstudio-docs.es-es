---
title: IActiveScriptAuthor::GetScriptTextAttributes | Documentos de Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IActiveScriptAuthor.GetScriptTextAttributes
apilocation: scrobj.dll
helpviewer_keywords: IActiveScriptAuthor::GetScriptTextAttributes
ms.assetid: a53451de-cc5c-4b53-8e5f-81e196364caf
caps.latest.revision: "11"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6aa96623b4356f0a3d17c8b2631840953dac2d51
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptauthorgetscripttextattributes"></a>IActiveScriptAuthor::GetScriptTextAttributes
Devuelve los atributos de texto de un bloque de script.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
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
 [in, size_is (`cch`)] el texto del bloque de script. Esta cadena no tiene como terminadas en null.  
  
 `cch`  
 [in] El tamaño usado para la `pszCode` y `pattr` parámetros.  
  
 `pszDelimiter`  
 [in] La dirección del delimitador de fin de secuencia de comandos. Cuando `pszCode` se analiza desde una secuencia de texto, el host normalmente usa un delimitador (por ejemplo, dos comillas simples), para detectar el final de la scriptlet. Establezca este parámetro en NULL si no hay ningún delimitador para identificar el final del bloque de script.  
  
 `dwFlags`  
 [in] Los marcadores que están asociados con los atributos de texto del bloque de script. Puede ser una combinación de los siguientes valores:  
  
|Constante|Valor|Descripción|  
|--------------|-----------|-----------------|  
|GETATTRTYPE_DEPSCAN|0 x 0001|Identificar identificadores que tienen el atributo SOURCETEXT_ATTR_IDENTIFIER e identificar los operadores de punto que tienen el atributo SOURCETEXT_ATTR_MEMBERLOOKUP.|  
|GETATTRFLAG_THIS|0 x 0100|Identificar el objeto actual que tiene el atributo SOURCETEXT_ATTR_THIS.|  
|GETATTRFLAG_HUMANTEXT|0 x 8000|Identificar el texto de contenido y un comentario de cadena que tiene el atributo SOURCETEXT_ATTR_HUMANTEXT.|  
  
 `pattr`  
 [entrada, salida, size_is (`cch`)] la información de color para el código del bloque de script.  
  
## <a name="return-value"></a>Valor devuelto  
 Interfaz `HRESULT`. Entre los valores posibles se incluyen los que se indican en la tabla siguiente, entre otros.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`S_OK`|El método se realizó correctamente.|  
  
## <a name="remarks"></a>Comentarios  
  
## <a name="see-also"></a>Vea también  
 [IActiveScriptAuthor (interfaz)](../../winscript/reference/iactivescriptauthor-interface.md)   
 [SOURCE_TEXT_ATTR (Enumeración)](../../winscript/reference/source-text-attr-enumeration.md)