---
title: IActiveScriptAuthor::GetScriptletTextAttributes | Documentos de Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptAuthor.GetScriptletTextAttributes
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptAuthor::GetScriptletTextAttributes
ms.assetid: 082edfce-6c5b-4e5e-b942-31b423a4fa1d
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: cb8f1b5aac6df8d8659fa323f3f1efcb7721d97f
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/19/2019
ms.locfileid: "58155857"
---
# <a name="iactivescriptauthorgetscriptlettextattributes"></a>IActiveScriptAuthor::GetScriptletTextAttributes
Devuelve los atributos de texto de scriptlet.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
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
 [in, size_is (`cch`)] el texto de scriptlet. Esta cadena no tiene que estar terminado en null.  
  
 `cch`  
 [in] El tamaño usado para la `pszCode` y `pattr` parámetros.  
  
 `pszDelimiter`  
 [in] La dirección del delimitador final de scriptlet. Cuando `pszCode` se analiza desde una secuencia de texto, el host normalmente utiliza un delimitador (por ejemplo, dos comillas simples), para detectar el final del scriptlet. Establezca este parámetro en NULL si no hay delimitador se utiliza para identificar el final de scriptlet.  
  
 `dwFlags`  
 [in] Marcas que están asociadas con los atributos de texto del scriptlet. Puede ser una combinación de los siguientes valores.  
  
|Constante|Valor|Descripción|  
|--------------|-----------|-----------------|  
|GETATTRTYPE_DEPSCAN|0x0001|Identificar los identificadores que tienen el atributo SOURCETEXT_ATTR_IDENTIFIER e identificar los operadores de puntos que tienen el atributo SOURCETEXT_ATTR_MEMBERLOOKUP.|  
|GETATTRFLAG_THIS|0x0100|Identificar el objeto actual que tiene el atributo SOURCETEXT_ATTR_THIS.|  
|GETATTRFLAG_HUMANTEXT|0x8000|Identificar el texto de comentario y el contenido de cadena que tiene el atributo SOURCETEXT_ATTR_HUMANTEXT.|  
  
 `pattr`  
 [in, out, size_is (`cch`)] la información de color para el código de scriptlet.  
  
## <a name="return-value"></a>Valor devuelto  
 Una clase `HRESULT`. Entre los valores posibles se incluyen los que se indican en la tabla siguiente, entre otros.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`S_OK`|El método se realizó correctamente.|  
  
## <a name="remarks"></a>Comentarios  
  
## <a name="see-also"></a>Vea también  
 [IActiveScriptAuthor (interfaz)](../../winscript/reference/iactivescriptauthor-interface.md)   
 [IActiveScriptAuthor::GetScriptTextAttributes](../../winscript/reference/iactivescriptauthor-getscripttextattributes.md)   
 [SOURCE_TEXT_ATTR (Enumeración)](../../winscript/reference/source-text-attr-enumeration.md)