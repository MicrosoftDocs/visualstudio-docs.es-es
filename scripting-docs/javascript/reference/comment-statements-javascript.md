---
title: Comentario de instrucciones (JavaScript) | Documentos de Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- Comment_JavaScript
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- comments, ignoring
- comment statements
ms.assetid: b604824f-ac17-49d3-bcdb-2a893ab5fff8
caps.latest.revision: 13
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c270379725550e116928bbecd69e6be51c34992f
ms.sourcegitcommit: 3b692c9bf332b7b9150901e16daf99a64b599fee
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/10/2018
---
# <a name="comment-statements-javascript"></a>Instrucciones Comment (JavaScript)
Hace que el analizador de [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] pase por alto los comentarios.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
Single-line Comment:  
// comment   
```  
  
```  
Multiline Comment:  
/*  
comment  
*/  
```  
  
```  
Comments with conditional compilation:  
//@CondStatement   
  
/*@  
condStatement  
@*/  
```  
  
## <a name="remarks"></a>Comentarios  
 El argumento `comment` es el texto de cualquier comentario que desee incluir en el script. El argumento `condStatement` debe usarse si se activa la compilación condicional. Si se usan comentarios de una sola línea, no puede haber espacios entre los caracteres "//" y "@".  
  
 Use los comentarios para evitar que el analizador de [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] lea partes de un script. Puede usar los comentarios para incluir notas explicativas en un programa.  
  
 Si se usan comentarios de una sola línea, el analizador pasa por alto cualquier texto comprendido entre el marcador de comentario y el final de la línea. Si se usan comentarios de varias líneas, el analizador pasa por alto cualquier texto comprendido entre el marcador de inicio y de final.  
  
 Los comentarios se usan para permitir la compilación condicional conservando la compatibilidad con exploradores que no admiten esta característica. Estos exploradores tratan estas formas de comentarios como comentarios de una sola línea o de varias líneas respectivamente.  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestran los usos más comunes de los comentarios.  
  
```JavaScript  
/* This is a multiline comment that  
    can span as many lines as necessary.  */  
function myfunction(arg1, arg2){  
    var r;  
    // This is a single line comment.  
    r = arg1 + arg2  
    return(r);  
}  
```  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra cómo usar la compilación condicional. En este ejemplo se utilizan delimitadores de comentario especiales que solo se emplean si la compilación condicional se activa mediante la instrucción `@cc_on`. Los motores de scripting que no admiten la compilación condicional solo ven el mensaje que indica que la compilación condicional no se admite.  
  
```JavaScript  
/*@cc_on @*/  
/*@if (@_jscript_version >= 4)  
    alert("JavaScript version 4 or better");  
    @else @*/  
    alert("Conditional compilation not supported by this scripting engine.");  
/*@end @*/  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]