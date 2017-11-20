---
title: "@if(Instrucción de JavaScript) | Documentos de Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: '@if_JavaScriptKeyword'
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- elif statement
- conditional statements, if
- if statement, @if
- else statement
- '@if statement'
ms.assetid: ff11b29d-c06a-4276-b11d-db73e2da98ac
caps.latest.revision: "18"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 87cfc157ab16b183ccf687fa221393be4ab74757
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="if-statement-javascript"></a>@if(Instrucción de JavaScript)
Ejecuta condicionalmente un grupo de instrucciones en función del valor de una expresión.  
  
> [!WARNING]
>  La compilación condicional no se admite en el modo estándar de Internet Explorer 11 ni en las aplicaciones [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)]. En cambio, sí se admite en el modo estándar de Internet Explorer 10 y en las versiones anteriores.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
      @if (  
   condition1  
)  
   text1  
[@elif (  
   condition2  
)  
   text2]  
[@else  
   text3]  
@end   
```  
  
## <a name="parameters"></a>Parámetros  
 *condition1, condition2*  
 Opcional. Expresión que puede convertirse en una expresión booleana.  
  
 `text1`  
 Opcional. Texto que se va a analizar si `condition1` es **true**.  
  
 `text2`  
 Opcional. Texto que se va a analizar si `condition1` es **false** y `condition2` es **true**.  
  
 `text3`  
 Opcional. Texto que se va a analizar si ambos `condition1` y `condition2` son **false**.  
  
## <a name="remarks"></a>Comentarios  
 Cuando se escribe una instrucción `@if`, no es necesario colocar cada cláusula en una línea independiente. Puede usar varios  **@elif**  cláusulas. Sin embargo, todos los  **@elif**  deben preceder a las cláusulas un  **@else**  cláusula.  
  
 La instrucción `@if` se suele usar para determinar qué texto, entre varias opciones, se debe emplear para el resultado.  
  
 No es muy común usar variables de compilación condicional en scripts escritos para páginas de ASP o ASP.NET o programas de línea de comandos. Esto se debe a que las funciones de los compiladores se pueden determinar mediante otros métodos.  
  
 Cuando se escribe un script para una página web, se ha de agregar siempre el código de compilación condicional entre delimitadores de comentario. De esta forma, los hosts que no admitan la compilación condicional podrán omitir este código.  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra el uso de la  **@if...@elif... @else... @end**  instrucción.  
  
```JavaScript  
/*@cc_on @*/  
/*@  
    document.write("JavaScript version: " + @_jscript_version + ".");  
    document.write("<br />");  
    @if (@_win32)  
        document.write("Running on a 32-bit version of Windows.");  
    @elif (@_win16)  
        document.write("Running on a 16-bit version of Windows.");  
    @else  
        document.write("Running on a different operating system.");  
    @end  
@*/  
```  
  
## <a name="requirements"></a>Requisitos  
 Se admite en todas las versiones de Internet Explorer, pero no en las aplicaciones de [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)].  
  
## <a name="see-also"></a>Vea también  
 [Compilación condicional](../../javascript/advanced/conditional-compilation-javascript.md)   
 [Variables de compilación condicional](../../javascript/advanced/conditional-compilation-variables-javascript.md)   
 [@cc_onInstrucción](../../javascript/reference/at-cc-on-statement-javascript.md)   
 [@set Instrucción](../../javascript/reference/at-set-statement-javascript.md)