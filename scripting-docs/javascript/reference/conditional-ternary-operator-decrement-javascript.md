---
title: Condicional operador ternario (?:) (JavaScript) | Documentos de Microsoft
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
- '?:'
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- conditional operators
- conditional (Ternary) operator
- ternary
ms.assetid: 7399ac32-9324-4a9a-ae76-be9c0f9df81c
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1dc34b5c633cfc02219cb01061e1aaa017e0f7f2
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
ms.locfileid: "24634195"
---
# <a name="conditional-ternary-operator--javascript"></a>Operador condicional ternario (?:) (JavaScript)
Devuelve una de las dos expresiones posibles, dependiendo de una condición.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
test ? expression1 : expression2  
```  
  
## <a name="parameters"></a>Parámetros  
 `test`  
 Cualquier expresión booleana.  
  
 `expression1`  
 Expresión que se devuelve si `test` es `true`. Puede ser una expresión de coma.  
  
 `expression2`  
 Expresión que se devuelve si `test` es `false`. Se puede vincular más de una expresión mediante una expresión de coma.  
  
## <a name="remarks"></a>Comentarios  
 El operador `?:` se puede utilizar como forma abreviada de una instrucción `if...else`. Se utiliza normalmente como parte de una expresión mayor en la que una instrucción `if...else` no sería práctica. Por ejemplo:  
  
```JavaScript  
var now = new Date();  
var greeting = "Good" + ((now.getHours() > 17) ? " evening." : " day.");  
```  
  
 En el ejemplo se crea una cadena que de contiene "Good evening" Si es después de las 6 p.m.. El código equivalente que utiliza una instrucción `if...else` tendría el siguiente aspecto:  
  
```JavaScript  
var now = new Date();  
var greeting = "Good";  
if (now.getHours() > 17)  
   greeting += " evening.";  
else  
   greeting += " day.";  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>Vea también  
 [If... else (instrucción)](../../javascript/reference/if-dot-dot-dot-else-statement-javascript.md)   
 [Precedencia de operadores](../../javascript/operator-subtractprecedence-javascript.md)   
 [Resumen de operadores (JavaScript)](../../javascript/misc/operator-subtractsummary-javascript.md)   
 [Aplicación de ejemplo de Script Junkie configuración widget](http://code.msdn.microsoft.com/Script-Junkie-Configuration-543ece24)