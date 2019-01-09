---
title: IActiveScriptDebug::GetScriptletTextAttributes | Documentos de Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptDebug.GetScriptletTextAttributes
apilocation:
- jscript.dll
helpviewer_keywords:
- IActiveScriptDebug::GetScriptletTextAttributes
ms.assetid: b3990d86-5fdf-4c9f-9678-3f4b808c7ca8
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 757c56750ee54e7de50f245b8b643cc5983f3149
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/08/2019
ms.locfileid: "54097557"
---
# <a name="iactivescriptdebuggetscriptlettextattributes"></a>IActiveScriptDebug::GetScriptletTextAttributes
Devuelve los atributos de texto para un scriptlet arbitrario.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
HRESULT GetScriptletTextAttributes(  
   LPCOLESTR          pstrCode,  
   ULONG              uNumCodeChars,  
   LPCOLESTR          pstrDelimiter,  
   DWORD              dwFlags,  
   SOURCE_TEXT_ATTR*  pattr  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `pstrCode`  
 [in] El texto de scriptlet. Esta cadena no debe ser terminado en null.  
  
 `uNumCodeChars`  
 [in] El número de caracteres del texto de scriptlet.  
  
 `pstrDelimiter`  
 [in] Dirección del delimitador final de scriptlet. Cuando `pstrCode` se analiza desde una secuencia de texto, el host normalmente utiliza un delimitador, como dos comillas ("), para detectar el final de scriptlet. Este parámetro especifica el delimitador que utiliza el host, lo que permite el motor de scripting proporcione algún preprocesamiento primitivo condicional (por ejemplo, que reemplaza una comilla sencilla ['] con dos comillas simples para su uso como un delimitador). Exactamente cómo (y si) utiliza el motor de scripting, esta información depende del motor de scripting. Establezca este parámetro en NULL si el host no utilizó un delimitador para marcar el final de scriptlet.  
  
 `dwFlags`  
 [in] Marcas asociadas al scriptlet. Puede ser una combinación de estos valores:  
  
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
  
 Esta llamada se proporciona ya scriptlets tienden a ser expresiones y puede tener una sintaxis diferente a un bloque de script. Si tienen la misma sintaxis, la implementación de este método debe ser idéntica a la implementación de la `GetScriptTextAttributes` método.  
  
## <a name="see-also"></a>Vea también  
 [IActiveScriptDebug (interfaz)](../../winscript/reference/iactivescriptdebug-interface.md)   
 [IActiveScriptDebug::GetScriptTextAttributes](../../winscript/reference/iactivescriptdebug-getscripttextattributes.md)   
 [IDebugDocumentText (interfaz)](../../winscript/reference/idebugdocumenttext-interface.md)   
 [IDebugDocumentText::GetText](../../winscript/reference/idebugdocumenttext-gettext.md)   
 [SOURCE_TEXT_ATTR (Enumeración)](../../winscript/reference/source-text-attr-enumeration.md)