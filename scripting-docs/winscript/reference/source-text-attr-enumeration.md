---
title: SOURCE_TEXT_ATTR (enumeración) | Microsoft Docs
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
ms.openlocfilehash: f34121ca50ae2467addb29809e7a3792063642ec
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62840127"
---
# <a name="sourcetextattr-enumeration"></a>SOURCE_TEXT_ATTR (Enumeración)
Describen los atributos de un carácter individual del texto de origen.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
enum enum_SOURCE_TEXT_ATTR{    SOURCETEXT_ATTR_KEYWORD    = 0x0001,    SOURCETEXT_ATTR_COMMENT    = 0x0002,    SOURCETEXT_ATTR_NONSOURCE    = 0x0004,    SOURCETEXT_ATTR_OPERATOR   = 0x0008,    SOURCETEXT_ATTR_NUMBER    = 0x0010,    SOURCETEXT_ATTR_STRING    = 0x0020,    SOURCETEXT_ATTR_FUNCTION_START  = 0x0040};  
```  
  
## <a name="members"></a>Miembros  
  
|Miembro|Valor|Descripción|  
|------------|-----------|-----------------|  
|SOURCETEXT_ATTR_KEYWORD|0x0001|El carácter es parte de una palabra clave del lenguaje, por ejemplo, la palabra clave de VBScript `While`.|  
|SOURCETEXT_ATTR_COMMENT|0x0002|El carácter es parte de un bloque de comentario.|  
|SOURCETEXT_ATTR_NONSOURCE|0x0004|El carácter no es parte del texto de origen del lenguaje compilado. Por ejemplo, el código HTML que rodea a un bloque de script.|  
|SOURCETEXT_ATTR_OPERATOR|0x0008|El carácter es parte de un operador de lenguaje. Por ejemplo:, el operador aritmético **+**.|  
|SOURCETEXT_ATTR_NUMBER|0x0010|El carácter es parte de una constante numérica de lenguaje.  Por ejemplo, la constante 3,14159.|  
|SOURCETEXT_ATTR_STRING|0x0020|El carácter es parte de una constante de cadena de lenguaje. Por ejemplo, la cadena "Hello World".|  
|SOURCETEXT_ATTR_FUNCTION_START|0x0040|El carácter indica el inicio de un bloque de función|  
  
## <a name="remarks"></a>Comentarios  
 Normalmente, el `IDebugDocumentHost::GetScriptTextAttributes`, `IActiveScriptDebug::GetScriptletTextAttributes`, y `IActiveScriptDebug::GetScriptTextAttributes` métodos devuelven un atributo de texto por carácter, a menos que:  
  
- Se establece la marca GETATTRTYPE_DEPSCAN, en cuyo caso el método puede devolver las marcas de SOURCETEXT_ATTR_IDENTIFIER y SOURCETEXT_ATTR_MEMBERLOOKUP  
  
- Se establece la marca GETATTRFLAG_THIS, en cuyo caso el método puede devolver la marca SOURCETEXT_ATTR_THIS,  
  
- Se establece la marca GETATTRFLAG_HUMANTEXT, en cuyo caso el método puede devolver la marca SOURCETEXT_ATTR_HUMANTEXT.  
  
## <a name="see-also"></a>Vea también  
 [Active Script Debugger (Constantes, Enumeraciones y Estructuras)](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)