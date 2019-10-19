---
title: 'IDebugDocumentHost:: GetScriptTextAttributes | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugDocumentHost.GetScriptTextAttributes
apilocation:
- scrobj.dll
helpviewer_keywords:
- IDebugDocumentHost::GetScriptTextAttributes
ms.assetid: fe459d0d-937f-4176-be81-99d5cca121a1
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3b18f4f49fa157b78e4f1fd6c7766e929890a6c6
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/18/2019
ms.locfileid: "72569205"
---
# <a name="idebugdocumenthostgetscripttextattributes"></a>IDebugDocumentHost::GetScriptTextAttributes
Devuelve los atributos de texto para un bloque de texto del documento.  
  
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
 de Texto del bloque de script. No es necesario que esta cadena termine en NULL.  
  
 `uNumCodeChars`  
 de Número de caracteres del texto del bloque de script.  
  
 `pstrDelimiter`  
 de Dirección del delimitador de bloque de script final. Cuando `pstrCode` se analiza desde un flujo de texto, el host normalmente usa un delimitador, como dos comillas simples (' '), para detectar el final del bloque de script. Este parámetro especifica el delimitador utilizado por el host, lo que permite que el motor de scripting proporcione algún preprocesamiento primitivo condicional (por ejemplo, reemplazando una comilla simple ['] con dos comillas simples para su uso como delimitador). Exactamente cómo (y si) el motor de scripting utiliza esta información depende del motor de scripting. Establezca este parámetro en NULL si el host no ha utilizado un delimitador para marcar el final del bloque de script.  
  
 `dwFlags`  
 de Marcas asociadas al bloque de script. Puede ser una combinación de estos valores:  
  
|Constante|Valor|Descripción|  
|--------------|-----------|-----------------|  
|GETATTRTYPE_DEPSCAN|0x0001|Indica que los identificadores y los operadores de punto se deben identificar con las marcas SOURCETEXT_ATTR_IDENTIFIER y SOURCETEXT_ATTR_MEMBERLOOKUP, respectivamente.|  
|GETATTRFLAG_THIS|0x0100|Indica que el identificador del objeto actual debe identificarse con la marca SOURCETEXT_ATTR_THIS.|  
|GETATTRFLAG_HUMANTEXT|0x8000|Indica que el contenido de la cadena y el texto del comentario deben identificarse con la marca SOURCETEXT_ATTR_HUMANTEXT.|  
  
 `pattr`  
 [in, out] Búfer que va a contener los atributos devueltos.  
  
## <a name="return-value"></a>Valor devuelto  
 El método devuelve un objeto `HRESULT`. Entre los valores posibles se incluyen los que se indican en la tabla siguiente, entre otros.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`S_OK`|El método se realizó correctamente.|  
|`E_NOTIMPL`|El host solo usa atributos predeterminados.|  
  
## <a name="remarks"></a>Comentarios  
 Este método devuelve los atributos de texto de un bloque arbitrario de texto del documento. Es aceptable que los hosts devuelvan `E_NOTIMPL`, en cuyo caso se utilizan los atributos predeterminados.  
  
## <a name="see-also"></a>Vea también  
 @No__t_1 de la [interfaz IDebugDocumentHost](../../winscript/reference/idebugdocumenthost-interface.md)  
 [SOURCE_TEXT_ATTR (Enumeración)](../../winscript/reference/source-text-attr-enumeration.md)