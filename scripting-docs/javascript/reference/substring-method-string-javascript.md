---
title: "substring (método, String) (JavaScript) | Documentos de Microsoft"
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
- substring
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- substrings
- substring method
ms.assetid: 9cf9a005-cbe3-42fd-828b-57a39f54224c
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 15ebaadc7b24fa97f531a22f6deb1453ff52b3e7
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="substring-method-string-javascript"></a>substring (Método, String de JavaScript)
Devuelve la subcadena en la ubicación especificada dentro de un `String` objeto.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
      strVariable. substring(start [, end])  
"String Literal".substring(start [, end])   
```  
  
## <a name="parameters"></a>Parámetros  
 `start`  
 Obligatorio. Valor entero del índice de base cero que indica el principio de la subcadena.  
  
 `end`  
 Opcional. Valor entero del índice de base cero que indica el final de la subcadena. La subcadena incluye los caracteres hasta, pero sin incluir, el carácter indicado por `end`.  
  
 Si `end` se omite, los caracteres de `start` hasta el final de la cadena original se devuelven.  
  
## <a name="remarks"></a>Comentarios  
 El `substring` método devuelve una cadena que contiene la subcadena desde `start` hacia arriba, pero no incluyen `end`.  
  
 El **subcadena** método usa el valor más bajo de `start` y `end` como punto inicial de la subcadena. Por ejemplo, strvar.substring (0, 3**)** y strvar.substring (3, 0) devuelven la misma subcadena.  
  
 Si el valor `start` o `end` es `NaN` o negativo, se reemplazan por cero.  
  
 La longitud de la subcadena es igual al valor absoluto de la diferencia entre `start` y `end`. Por ejemplo, la longitud de la subcadena devuelta en strvar.substring (0, 3) y strvar.substring (3, 0) es tres.  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra el uso de la **subcadena** método.  
  
```JavaScript  
var s = "The quick brown fox jumps over the lazy dog.";  
var ss = s.substring(10, 15);  
document.write(ss);  
  
// Output:  
// brown  
  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>Vea también  
 [substr (Método, String)](../../javascript/reference/substr-method-string-javascript.md)