---
title: Operador Spread (...) (JavaScript) | Documentos de Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 10263a4c-bd27-4d87-9917-fb4b6bf373db
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a07d480360441906c445faa196f6d7771f97d75d
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
ms.locfileid: "24640235"
---
# <a name="spread-operator--javascript"></a>Operador Spread (...) (JavaScript)
Permite que partes de una matriz literal se inicialicen desde una expresión iterable (como, por ejemplo, otra matriz literal) o permite que una expresión se expanda a varios argumentos (en llamadas a funciones).  
  
## <a name="syntax"></a>Sintaxis  
  
```  
var array = [[arg0ToN ,] ...iterable [, arg0ToN]]  
func([args ,] ...iterable [, args | ...iterable])  
  
```  
  
## <a name="parameters"></a>Parámetros  
 `iterable`  
 Obligatorio. Un objeto iterable.  
  
 `arg0ToN`  
 Opcional. Uno o más elementos de un literal de matriz.  
  
 `args`  
 Opcional. Uno o más argumentos a una función.  
  
## <a name="remarks"></a>Comentarios  
 Para obtener más información sobre los iteradores, vea [iteradores y generadores](../../javascript/advanced/iterators-and-generators-javascript.md). Para obtener más información sobre cómo utilizar el operador spread como un parámetro de rest, consulte [funciones](../../javascript/functions-javascript.md).  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo de código mostrado a continuación, el uso del operador spread se contrasta con el uso del método `concat`.  
  
```JavaScript  
var a, b, c, d, e;  
a = [1,2,3];  
b = "dog";  
c = [42, "cat"];  
  
// Using the concat method.  
d = a.concat(b, c);  
  
// Using the spread operator.  
e = [...a, b, ...c];  
  
console.log(d);  
console.log(e);  
  
// Output:  
// 1, 2, 3, "dog", 42, "cat"  
// 1, 2, 3, "dog", 42, "cat"  
```  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo de código mostrado a continuación se indica cómo utilizar el operador spread en una llamada de función. En este ejemplo dos literales de matriz se pasan a la función mediante el operador spread y las matrices se expanden a varios argumentos.  
  
```JavaScript  
function f(a, b, c, x, y, z) {  
  return a + b + c + x + y + z;  
}  
  
var args = [1, 2, 3];  
console.log(f(...args, 4, ...[5, 6]));  
  
// Output:  
// 21  
  
```  
  
## <a name="example"></a>Ejemplo  
 Con los operadores spread, puede simplificar código que anteriormente requería el uso de `apply`.  
  
```JavaScript  
function f(x, y, z) {  
    return x + y + z;  
}  
  
var args = [1, 2, 3];  
  
// Old method  
f.apply(this, args);  
// New method  
f(...args);  
  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]  
  
## <a name="see-also"></a>Vea también  
 [Precedencia de operadores](../../javascript/operator-subtractprecedence-javascript.md)   
 [Resumen de operadores (JavaScript)](../../javascript/misc/operator-subtractsummary-javascript.md)