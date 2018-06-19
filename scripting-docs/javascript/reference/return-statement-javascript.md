---
title: return (instrucción) (JavaScript) | Documentos de Microsoft
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
- return_JavaScriptKeyword
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- terminating execution
- return statement
- function statement
- return statement, syntax
- return statement, exiting functions in script
ms.assetid: a9130d90-11fb-43f5-a819-7e5435f74c05
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2c28f17bed2dfff021ea1aea268bb7a2eb3f3e58
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
ms.locfileid: "24639335"
---
# <a name="return-statement-javascript"></a>return (Instrucción de JavaScript)
Sale de la función actual y devuelve un valor desde esa función.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
return[(][expression][)];   
```  
  
## <a name="remarks"></a>Comentarios  
 Opcional *expresión* argumento es el valor devuelto de la función. Si se omite, la función no devuelve un valor.  
  
 Usa el `return` instrucción para detener la ejecución de una función y devolver el valor de *expresión*. Si *expresión* se omite, o ninguna `return` instrucción se ejecuta desde dentro de la función, la expresión que llamó la función actual se asigna el valor sin definir.  
  
## <a name="example"></a>Ejemplo  
 En el siguiente ejemplo se muestra el uso de la instrucción `return`.  
  
```JavaScript  
function myfunction(arg1, arg2){  
   var r;  
   r = arg1 * arg2;  
   return(r);  
}  
```  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra el uso de la `return` instrucción para devolver una función.  
  
```JavaScript  
function doWork() {  
    return function calculate(y) { return y + 1; };  
}  
  
var func = doWork();  
var x = func(5);  
document.write(x);  
  
// Output: 6  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>Vea también  
 [function (Instrucción)](../../javascript/reference/function-statement-javascript.md)