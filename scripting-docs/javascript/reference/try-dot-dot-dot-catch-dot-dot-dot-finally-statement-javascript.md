---
title: try... catch... finally (instrucción) (JavaScript) | Documentos de Microsoft
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
- try_JavaScriptKeyword
- finally_JavaScriptKeyword
- catch_JavaScriptKeyword
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- try-catch exception handling, finally block
- try-catch exception handling, about try-catch exception handling
- try-catch exception handling, catch block
- try-catch exception handling
ms.assetid: b7a0a54e-dfaa-4e41-bf25-bcaa43e601fb
caps.latest.revision: 28
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b05f15e593aeb7cb921f6237fad30b589cfdfe66
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
ms.locfileid: "24641735"
---
# <a name="trycatchfinally-statement-javascript"></a>try...catch...finally (Instrucción de JavaScript)
Configura bloques de código en los que los errores que se producen en un bloque se controlan en otro. Los errores que se producen dentro del bloque `try` se detectan en el bloque `catch`. [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)].  
  
## <a name="syntax"></a>Sintaxis  
  
```  
try {  
    tryStatements  
}  
catch(exception){  
    catchStatements  
}  
finally {  
    finallyStatements  
}  
```  
  
## <a name="parameters"></a>Parámetros  
 `tryStatements`  
 Obligatorio. Instrucciones donde puede producirse un error.  
  
 `exception`  
 Obligatorio. Cualquier nombre de variable. El valor inicial de `exception` es el valor del error producido.  
  
 `catchStatements`  
 Opcional. Instrucciones para controlar los errores que tienen lugar en los argumentos `tryStatements` asociados.  
  
 `finallyStatements`  
 Opcional. Instrucciones que se ejecutan incondicionalmente después de que se hayan procesado todos los demás errores.  
  
## <a name="remarks"></a>Comentarios  
 La instrucción `try...catch...finally` proporciona un medio para controlar una parte o la totalidad de los errores que pueden producirse en un bloque de código determinado, mientras se sigue ejecutando el código. Si se producen errores no controlados, [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] proporciona el mensaje de error normal.  
  
 El bloque `try` contiene código que puede provocar un error, mientras que el bloque `catch` contiene el código que administra todos o algunos de los errores. Si se produce un error en el bloque `try`, el control de programas se pasa al bloque `catch`. El valor inicial de `exception` es el valor del error que se produjo en el bloque `try`. Si no se produce ningún error, no se ejecuta nunca el código del bloque `catch`.  
  
 Puede pasar el error hasta el nivel siguiente mediante la instrucción `throw` para volver a producir el error.  
  
 Después de que se ejecuten todas las instrucciones en el bloque `try` y se haya realizado un control de errores en el bloque `catch`, se ejecutan las instrucciones en el bloque `finally`, con independencia de si se ha controlado o no un error. El código en el `finally` bloque se garantiza que se ejecutará a menos que se produce un error no controlado (por ejemplo, un error en tiempo de ejecución dentro de la **catch** bloque).  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se genera una excepción `ReferenceError` y se muestra el nombre del error y su mensaje.  
  
```JavaScript  
try {  
    addalert("bad call");  
}  
catch(e) {  
    document.write ("Error Message: " + e.message);  
    document.write ("<br />");  
    document.write ("Error Code: ");  
    document.write (e.number & 0xFFFF);  
    document.write ("<br />");  
    document.write ("Error Name: " + e.name);  
}  
  
// Output:  
Error Message: 'addalert' is undefined  
Error Code: 5009  
Error Name: ReferenceError  
  
```  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra cómo volver a producir errores, así como la ejecución de bloques `try...catch` anidados. Cuando el error se produce en el bloque anidado `try`, se pasa al bloque `catch` anidado, que vuelve a producirlo. El bloque `finally` anidado se ejecuta antes que el bloque `catch` externo controle el error y al final se ejecuta el bloque externo `finally`.  
  
```JavaScript  
try {  
    document.write("Outer try running...<br/>");  
  
    try {  
        document.write("Nested try running...<br/>");  
        throw new Error(301, "an error");  
    }  
    catch (e) {  
        document.write ("Nested catch caught " + e.message + "<br/>");  
        throw e;  
    }  
    finally {  
        document.write ("Nested finally is running...<br/>");  
    }  
}  
catch (e) {  
    document.write ("Outer catch caught " + e.message + "<br/>");  
}  
finally {  
    document.write ("Outer finally running");  
}  
  
// Output:  
// Outer try running...  
// Nested try running...  
// Nested catch caught error from nested try  
// Nested finally is running...  
// Outer catch caught error from nested try  
// Outer finally running  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv5](../../javascript/reference/includes/jsv5-md.md)]  
  
> [!NOTE]
>  A partir de modo estándar de Internet Explorer 8, el **catch** bloque ya no es necesario para `finally` a ejecutar.  
  
## <a name="see-also"></a>Vea también  
 [throw (instrucción)](../../javascript/reference/throw-statement-javascript.md)   
 [Aplicación de ejemplo de Asistente para configuración de Script Junkie](http://code.msdn.microsoft.com/Script-Junkie-Configuration-543ece24)