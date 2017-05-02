---
title: "SOURCE_TEXT_ATTR (Enumeraci&#243;n) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "SOURCE_TEXT_ATTR (constantes)"
ms.assetid: 459384b0-1463-4841-a2b3-a993207163bf
caps.latest.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 10
---
# SOURCE_TEXT_ATTR (Enumeraci&#243;n)
Describe los atributos de un carácter individual del texto original.  
  
## Sintaxis  
  
```cpp  
enum enum_SOURCE_TEXT_ATTR  
{  
    SOURCETEXT_ATTR_KEYWORD    = 0x0001,  
    SOURCETEXT_ATTR_COMMENT    = 0x0002,  
    SOURCETEXT_ATTR_NONSOURCE    = 0x0004,  
    SOURCETEXT_ATTR_OPERATOR   = 0x0008,  
    SOURCETEXT_ATTR_NUMBER    = 0x0010,  
    SOURCETEXT_ATTR_STRING    = 0x0020,  
    SOURCETEXT_ATTR_FUNCTION_START  = 0x0040  
};  
  
```  
  
## Members  
  
|Miembro|Valor|Descripción|  
|-------------|-----------|-----------------|  
|SOURCETEXT\_ATTR\_KEYWORD|0x0001|El carácter forma parte de una palabra clave de lenguaje, por ejemplo, la palabra clave `While`de VBScript.|  
|SOURCETEXT\_ATTR\_COMMENT|0x0002|El carácter es parte de un bloque de comentario.|  
|SOURCETEXT\_ATTR\_NONSOURCE|0x0004|El carácter no es parte de texto original compilado del lenguaje.  Por ejemplo, HTML que rodea a un bloque de script.|  
|SOURCETEXT\_ATTR\_OPERATOR|0x0008|El carácter es parte de un operador del lenguaje.  Por ejemplo: , el operador aritmético **\+**.|  
|SOURCETEXT\_ATTR\_NUMBER|0x0010|El carácter forma parte de una constante numérica del lenguaje.  Por ejemplo, 3,14159 constantes.|  
|SOURCETEXT\_ATTR\_STRING|0x0020|El carácter forma parte de una constante de cadena de idioma.  Por ejemplo, la cadena “Hello World”.|  
|SOURCETEXT\_ATTR\_FUNCTION\_START|0x0040|El carácter indica el inicio de un bloque de función|  
  
## Comentarios  
 Normalmente, `IDebugDocumentHost::GetScriptTextAttributes`, `IActiveScriptDebug::GetScriptletTextAttributes`, y los métodos de `IActiveScriptDebug::GetScriptTextAttributes` devuelven un atributo de texto por el carácter, a menos que:  
  
-   Se establece la marca de GETATTRTYPE\_DEPSCAN, en cuyo caso el método puede devolver los marcadores de SOURCETEXT\_ATTR\_IDENTIFIER y de SOURCETEXT\_ATTR\_MEMBERLOOKUP,  
  
-   Se establece la marca de GETATTRFLAG\_THIS, en cuyo caso el método puede devolver el indicador de SOURCETEXT\_ATTR\_THIS,  
  
-   Se establece la marca de GETATTRFLAG\_HUMANTEXT, en cuyo caso el método puede devolver el indicador de SOURCETEXT\_ATTR\_HUMANTEXT.  
  
## Vea también  
 [Active Script Debugger \(Constantes, enumeraciones y estructuras\)](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)