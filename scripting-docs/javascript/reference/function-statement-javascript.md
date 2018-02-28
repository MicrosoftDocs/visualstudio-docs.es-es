---
title: "función (instrucción de JavaScript) | Documentos de Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- function_JavaScriptKeyword
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- new operator
- declaring functions, syntax
- function statement
- declaring functions
ms.assetid: cc9cfd43-1305-41c8-ad67-545d20f4fafe
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e5fac3647e9374a9c909a420b73b86354cac69b6
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="function-statement-javascript"></a>function (Instrucción de JavaScript)
Declara una nueva función.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
function functionname ([arg1 [, arg2 [,...[, argN]]]]) {  
    statements  
}   
```  
  
## <a name="parameters"></a>Parámetros  
 `functionname`  
 Obligatorio. Nombre de la función.  
  
 `arg1...argN`  
 Opcional. Lista opcional separada por comas de los argumentos que la función entiende.  
  
 `statements`  
 Opcional. Uno o más[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] las instrucciones.  
  
## <a name="remarks"></a>Comentarios  
 Utilice la `function` instrucción para declarar una función para su uso posterior. El código que se encuentra en `statements` no se ejecuta hasta que se llama a la función de en otro lugar en el script.  
  
 El [devolver](../../javascript/reference/return-statement-javascript.md) instrucción se utiliza para devolver un valor de la función. No es necesario usar un `return` instrucción; el programa devolverá cuando llega al final de la función. Si no hay ningún `return` instrucción se ejecuta en la función, o si la `return` instrucción no tiene ninguna expresión, la función devuelve el valor `undefined`.  
  
> [!NOTE]
>  Cuando se llama a una función, no olvide incluir los paréntesis y los argumentos necesarios. Llamar a una función sin paréntesis devuelve una referencia a la función, no los resultados de la función.  
  
## <a name="example"></a>Ejemplo  
 En el siguiente ejemplo se muestra el uso de la instrucción `function`.  
  
```JavaScript  
function myfunction (arg1, arg2) {  
    var r = arg1 * arg2;  
    return(r);  
}  
```  
  
## <a name="example"></a>Ejemplo  
 Una función puede asignarse a una variable. Esto se muestra en el ejemplo siguiente.  
  
```JavaScript  
function AddFive(x) {  
    return x + 5;  
}  
  
function AddTen(x) {  
    return x + 10;  
}  
  
var condition = false;  
  
var MyFunc;  
if (condition) {  
    MyFunc = AddFive;  
}  
else {  
    MyFunc = AddTen;  
}  
  
var result = MyFunc(123);  
// Output: 133  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>Vea también  
 [new (operador)](../../javascript/reference/new-operator-decrementjavascript.md)