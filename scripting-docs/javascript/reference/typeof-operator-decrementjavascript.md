---
title: typeof (operador) (JavaScript) | Documentos de Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: typeof_JavaScriptKeyword
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords: typeof operator
ms.assetid: ee8a1036-119f-486f-b034-b07bdba87f0c
caps.latest.revision: "11"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c79c69e6c447b14e61fa67ccb8600d5d83bebd2b
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="typeof-operator-javascript"></a>typeof (Operador de JavaScript)
Devuelve una cadena que identifica el tipo de datos de una expresión.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
typeof[(]expression[)] ;  
```  
  
## <a name="remarks"></a>Comentarios  
 El *expresión* argumento es cualquier expresión de tipo que se busca información.  
  
 El `typeof` operador devuelve información de tipo como una cadena. Hay seis posibles valores que `typeof` devuelve: "number", "cadena", "boolean", "object", "function" y "undefined".  
  
 Los paréntesis son opcionales en el `typeof` sintaxis.  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se comprueba el tipo de datos de variables.  
  
```JavaScript  
var index = 5;  
var result = (typeof index === 'number');  
// Output: true  
  
var description = "abc";  
var result = (typeof description === 'string');  
// Output: true  
```  
  
## <a name="example"></a>Ejemplo  
 El siguiente ejemplo se prueba para un tipo de datos de `undefined` para las variables declaradas y no declaradas.  
  
```JavaScript  
var declared;  
var result = (declared === undefined);  
// Output: true  
  
var result = (typeof declared === 'undefined');  
// Output: true  
  
var result = (typeof notDeclared === 'undefined')  
// Output: true  
  
var obj = {};  
var result = (typeof obj.propNotDeclared === 'undefined');  
// Output: true  
  
// An undeclared variable cannot be used in a comparison without  
// the typeof operator, so the next line generates an error.  
//  var result = (notDeclared === undefined);  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>Vea también  
 [Array.isArray (función)](../../javascript/reference/array-isarray-function-javascript.md)   
 [Object.getPrototypeOf (función)](../../javascript/reference/object-getprototypeof-function-javascript.md)   
 [undefined (constante)](../../javascript/reference/undefined-constant-javascript.md)   
 [Operadores de comparación](../../javascript/reference/comparison-operators-javascript.md)   
 [Tipos de datos](../../javascript/data-types-javascript.md)   
 [Precedencia de operadores](../../javascript/operator-subtractprecedence-javascript.md)   
 [Resumen de operadores (JavaScript)](../../javascript/misc/operator-subtractsummary-javascript.md)