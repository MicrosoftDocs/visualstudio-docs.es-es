---
title: IActiveScriptAuthor::GetScriptletTextAttributes | Documentos de Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- IActiveScriptAuthor.GetScriptletTextAttributes
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptAuthor::GetScriptletTextAttributes
ms.assetid: 082edfce-6c5b-4e5e-b942-31b423a4fa1d
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b01fba7d0e8eb80fed51b1ff0ebd3a8816bacb01
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptauthorgetscriptlettextattributes"></a>IActiveScriptAuthor::GetScriptletTextAttributes
Devuelve los atributos de texto de un Subscript.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
HRESULT GetScriptletTextAttributes(  
   LPCOLESTR pszCode,  
   ULONG cch,  
   LPCOLESTR pszDelimiter,  
   DWORD dwFlags,  
   SOURCE_TEXT_ATTR *pattr  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `pszCode`  
 [in, size_is (`cch`)] el texto scriptlet. Esta cadena no tiene como terminadas en null.  
  
 `cch`  
 [in] El tamaño usado para la `pszCode` y `pattr` parámetros.  
  
 `pszDelimiter`  
 [in] La dirección del extremo de scriptlet delimitador. Cuando `pszCode` se analiza desde una secuencia de texto, el host normalmente usa un delimitador (por ejemplo, dos comillas simples), para detectar el final de la scriptlet. Establezca este parámetro en NULL si no hay delimitador se usa para identificar el final de la scriptlet.  
  
 `dwFlags`  
 [in] Los marcadores que están asociados con los atributos de texto de la scriptlet. Puede ser una combinación de los valores siguientes.  
  
|Constante|Valor|Descripción|  
|--------------|-----------|-----------------|  
|GETATTRTYPE_DEPSCAN|0 x 0001|Identificar identificadores que tienen el atributo SOURCETEXT_ATTR_IDENTIFIER e identificar los operadores de punto que tienen el atributo SOURCETEXT_ATTR_MEMBERLOOKUP.|  
|GETATTRFLAG_THIS|0 x 0100|Identificar el objeto actual que tiene el atributo SOURCETEXT_ATTR_THIS.|  
|GETATTRFLAG_HUMANTEXT|0 x 8000|Identificar el texto de contenido y un comentario de cadena que tiene el atributo SOURCETEXT_ATTR_HUMANTEXT.|  
  
 `pattr`  
 [entrada, salida, size_is (`cch`)] la información de color para el código de scriptlet.  
  
## <a name="return-value"></a>Valor devuelto  
 Interfaz `HRESULT`. Entre los valores posibles se incluyen los que se indican en la tabla siguiente, entre otros.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`S_OK`|El método se realizó correctamente.|  
  
## <a name="remarks"></a>Comentarios  
  
## <a name="see-also"></a>Vea también  
 [IActiveScriptAuthor (interfaz)](../../winscript/reference/iactivescriptauthor-interface.md)   
 [IActiveScriptAuthor::GetScriptTextAttributes](../../winscript/reference/iactivescriptauthor-getscripttextattributes.md)   
 [SOURCE_TEXT_ATTR (Enumeración)](../../winscript/reference/source-text-attr-enumeration.md)