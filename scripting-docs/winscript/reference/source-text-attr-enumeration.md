---
title: Enumeración SOURCE_TEXT_ATTR | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- SOURCE_TEXT_ATTR constants
ms.assetid: 459384b0-1463-4841-a2b3-a993207163bf
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1dd0bbf08b6ddfdcfbffa494fdda9842004839b0
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/18/2019
ms.locfileid: "72573002"
---
# <a name="source_text_attr-enumeration"></a>SOURCE_TEXT_ATTR (Enumeración)
Describen los atributos de un carácter individual del texto de origen.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
enum enum_SOURCE_TEXT_ATTR{    SOURCETEXT_ATTR_KEYWORD    = 0x0001,    SOURCETEXT_ATTR_COMMENT    = 0x0002,    SOURCETEXT_ATTR_NONSOURCE    = 0x0004,    SOURCETEXT_ATTR_OPERATOR   = 0x0008,    SOURCETEXT_ATTR_NUMBER    = 0x0010,    SOURCETEXT_ATTR_STRING    = 0x0020,    SOURCETEXT_ATTR_FUNCTION_START  = 0x0040};  
```  
  
## <a name="members"></a>Miembros  
  
|Miembro|Valor|Descripción|  
|------------|-----------|-----------------|  
|SOURCETEXT_ATTR_KEYWORD|0x0001|El carácter es parte de una palabra clave del lenguaje; por ejemplo, la palabra clave de VBScript `While`.|  
|SOURCETEXT_ATTR_COMMENT|0x0002|El carácter forma parte de un bloque de comentario.|  
|SOURCETEXT_ATTR_NONSOURCE|0x0004|El carácter no forma parte del texto de origen del lenguaje compilado. Por ejemplo, el código HTML que rodea un bloque de script.|  
|SOURCETEXT_ATTR_OPERATOR|0x0008|El carácter forma parte de un operador de lenguaje. Por ejemplo:, el operador aritmético **+** .|  
|SOURCETEXT_ATTR_NUMBER|0x0010|El carácter es parte de una constante numérica de idioma.  Por ejemplo, la constante 3,14159.|  
|SOURCETEXT_ATTR_STRING|0x0020|El carácter forma parte de una constante de cadena de idioma. Por ejemplo, la cadena "Hola mundo".|  
|SOURCETEXT_ATTR_FUNCTION_START|0x0040|El carácter indica el inicio de un bloque de función|  
  
## <a name="remarks"></a>Comentarios  
 Normalmente, los métodos `IDebugDocumentHost::GetScriptTextAttributes`, `IActiveScriptDebug::GetScriptletTextAttributes` y `IActiveScriptDebug::GetScriptTextAttributes` devuelven un atributo de texto por carácter, a menos que:  
  
- Se establece la marca GETATTRTYPE_DEPSCAN, en cuyo caso el método puede devolver las marcas SOURCETEXT_ATTR_IDENTIFIER y SOURCETEXT_ATTR_MEMBERLOOKUP.  
  
- Se establece la marca GETATTRFLAG_THIS, en cuyo caso el método puede devolver la marca SOURCETEXT_ATTR_THIS.  
  
- Se establece la marca GETATTRFLAG_HUMANTEXT, en cuyo caso el método puede devolver la marca SOURCETEXT_ATTR_HUMANTEXT.  
  
## <a name="see-also"></a>Vea también  
 [Active Script Debugger (Constantes, Enumeraciones y Estructuras)](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)