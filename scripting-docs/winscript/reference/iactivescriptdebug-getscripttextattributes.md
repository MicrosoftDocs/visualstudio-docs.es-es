---
title: IActiveScriptDebug::GetScriptTextAttributes | Documentos de Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- IActiveScriptDebug.GetScriptTextAttributes
apilocation:
- jscript.dll
helpviewer_keywords:
- IActiveScriptDebug::GetScriptTextAttributes
ms.assetid: 2e8bda34-db0c-4b2e-a17f-82c4e0dbbc8c
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c8e9cd76da3e754eabce836b386893043dcd0622
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptdebuggetscripttextattributes"></a>IActiveScriptDebug::GetScriptTextAttributes
Devuelve los atributos de texto de un bloque de texto de la secuencia de comandos arbitrario.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
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
 [in] El texto de bloque de script. Esta cadena no debe terminadas en null.  
  
 `uNumCodeChars`  
 [in] El número de caracteres en el texto de bloque de script.  
  
 `pstrDelimiter`  
 [in] Dirección del delimitador final del bloque de script. Cuando `pstrCode` se analiza desde una secuencia de texto, el host normalmente usa un delimitador, como dos comillas ("), para detectar el final del bloque de script simples. Este parámetro especifica el delimitador que utiliza el host, lo que el motor de scripting proporcionar algunos condicional preprocesamiento primitivos (por ejemplo, reemplace una comilla simple ['] con dos comillas simples para su uso como un delimitador). Exactamente cómo (y si) los usos de motor de scripting en función de esta información en el motor de scripting. Establezca este parámetro en NULL si el host no usó un delimitador para marcar el final del bloque de script.  
  
 `dwFlags`  
 [in] Marcas asociadas con el bloque de script. Puede ser una combinación de estos valores:  
  
|Constante|Valor|Descripción|  
|--------------|-----------|-----------------|  
|GETATTRTYPE_DEPSCAN|0 x 0001|Indica que los identificadores y los operadores de punto deben identificarse con las marcas de SOURCETEXT_ATTR_IDENTIFIER y SOURCETEXT_ATTR_MEMBERLOOKUP, respectivamente.|  
|GETATTRFLAG_THIS|0 x 0100|Indica que el identificador para el objeto actual se debe identificarse con el indicador SOURCETEXT_ATTR_THIS.|  
|GETATTRFLAG_HUMANTEXT|0 x 8000|Indica que el texto de contenido y marque como comentario la cadena debe identificarse con la marca SOURCETEXT_ATTR_HUMANTEXT.|  
  
 `pattr`  
 [entrada, salida] Búfer que contiene los atributos devueltos.  
  
## <a name="return-value"></a>Valor devuelto  
 El método devuelve un objeto `HRESULT`. Entre los valores posibles se incluyen los que se indican en la tabla siguiente, entre otros.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`S_OK`|El método se realizó correctamente.|  
  
## <a name="remarks"></a>Comentarios  
 Un host inteligente que implementa `IDebugDocumentText` interfaz puede usar este método para delegar llamadas a la `IDebugDocumentText::GetText` método.  
  
 Este método para los bloques de script; el `GetScriptletTextAttributes` método es para scriptlets.  
  
## <a name="see-also"></a>Vea también  
 [IActiveScriptDebug (interfaz)](../../winscript/reference/iactivescriptdebug-interface.md)   
 [IActiveScriptDebug::GetScriptletTextAttributes](../../winscript/reference/iactivescriptdebug-getscriptlettextattributes.md)   
 [IDebugDocumentText (interfaz)](../../winscript/reference/idebugdocumenttext-interface.md)   
 [IDebugDocumentText::GetText](../../winscript/reference/idebugdocumenttext-gettext.md)   
 [SOURCE_TEXT_ATTR (Enumeración)](../../winscript/reference/source-text-attr-enumeration.md)