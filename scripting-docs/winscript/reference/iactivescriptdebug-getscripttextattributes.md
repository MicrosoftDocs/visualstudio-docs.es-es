---
title: IActiveScriptDebug::GetScriptTextAttributes | Documentos de Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptDebug.GetScriptTextAttributes
apilocation:
- jscript.dll
helpviewer_keywords:
- IActiveScriptDebug::GetScriptTextAttributes
ms.assetid: 2e8bda34-db0c-4b2e-a17f-82c4e0dbbc8c
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 01218ba46de39dd8351ad82068ca4b34b52b0d46
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/08/2019
ms.locfileid: "54097393"
---
# <a name="iactivescriptdebuggetscripttextattributes"></a>IActiveScriptDebug::GetScriptTextAttributes
Devuelve los atributos de texto de un bloque de texto de la secuencia de comandos arbitrario.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
HRESULT GetScriptTextAttributes(  
   LPCOLESTR          pstrCode,  
   ULONG              uNumCodeChars,  
   LPCOLESTR          pstrDelimiter,  
   DWORD              dwFlags,  
   SOURCE_TEXT_ATTR*  pattr  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `pstrCode`  
 [in] El texto del bloque de script. Esta cadena no debe ser terminado en null.  
  
 `uNumCodeChars`  
 [in] El número de caracteres en el texto del bloque de script.  
  
 `pstrDelimiter`  
 [in] Dirección del delimitador final del bloque de script. Cuando `pstrCode` se analiza desde una secuencia de texto, el host normalmente utiliza un delimitador, como dos comillas ("), para detectar el final del bloque de script. Este parámetro especifica el delimitador que utiliza el host, lo que permite el motor de scripting proporcione algún preprocesamiento primitivo condicional (por ejemplo, que reemplaza una comilla sencilla ['] con dos comillas simples para su uso como un delimitador). Exactamente cómo (y si) utiliza el motor de scripting, esta información depende del motor de scripting. Establezca este parámetro en NULL si el host no utilizó un delimitador para marcar el final del bloque de script.  
  
 `dwFlags`  
 [in] Marcas asociadas al bloque de script. Puede ser una combinación de estos valores:  
  
|Constante|Valor|Descripción|  
|--------------|-----------|-----------------|  
|GETATTRTYPE_DEPSCAN|0 x 0001|Indica que los identificadores y los operadores dot deben identificarse con los indicadores SOURCETEXT_ATTR_IDENTIFIER y SOURCETEXT_ATTR_MEMBERLOOKUP, respectivamente.|  
|GETATTRFLAG_THIS|0 x 0100|Indica que se debe identificar el identificador para el objeto actual con la marca SOURCETEXT_ATTR_THIS.|  
|GETATTRFLAG_HUMANTEXT|0 x 8000|Indica que el texto de comentario y el contenido de cadena debe identificarse con el indicador SOURCETEXT_ATTR_HUMANTEXT.|  
  
 `pattr`  
 [in, out] Búfer que contiene los atributos devueltos.  
  
## <a name="return-value"></a>Valor devuelto  
 El método devuelve un objeto `HRESULT`. Entre los valores posibles se incluyen los que se indican en la tabla siguiente, entre otros.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`S_OK`|El método se realizó correctamente.|  
  
## <a name="remarks"></a>Comentarios  
 Un host inteligente que implementa `IDebugDocumentText` interfaz puede usar este método para delegar las llamadas a la `IDebugDocumentText::GetText` método.  
  
 Este método para bloques de scripts; el `GetScriptletTextAttributes` método está destinado a scriptlets.  
  
## <a name="see-also"></a>Vea también  
 [IActiveScriptDebug (interfaz)](../../winscript/reference/iactivescriptdebug-interface.md)   
 [IActiveScriptDebug::GetScriptletTextAttributes](../../winscript/reference/iactivescriptdebug-getscriptlettextattributes.md)   
 [IDebugDocumentText (interfaz)](../../winscript/reference/idebugdocumenttext-interface.md)   
 [IDebugDocumentText::GetText](../../winscript/reference/idebugdocumenttext-gettext.md)   
 [SOURCE_TEXT_ATTR (Enumeración)](../../winscript/reference/source-text-attr-enumeration.md)