---
title: instrucción ' Return ' fuera de la función | Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: reference
f1_keywords:
- VS.WebClient.Help.SCRIPT1018
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 03568f9f-5f4f-4a10-a738-9a73f3832b9e
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a90af6de8e2c238e3660111b19d13c1eaf628c9e
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/18/2019
ms.locfileid: "72573685"
---
# <a name="return-statement-outside-of-function"></a>'return' instrucción fuera de función
Usó una instrucción `return` en el ámbito global del código. La instrucción `return` solo debe aparecer dentro del cuerpo de una función.  
  
 La invocación de una función con el operador `()` es una expresión. Todas las expresiones tienen valores; la instrucción `return` se utiliza para especificar el valor devuelto por una función. El formato general es:  
  
```js
  
return [ expression ];  
```  
  
 Cuando se ejecuta la instrucción `return`, *Expression* se evalúa y se devuelve como el valor de la función. Si no hay ninguna expresión, se devuelve **undefined** .  
  
 La ejecución de la función se detiene cuando se ejecuta la instrucción `return`, incluso si todavía quedan otras instrucciones en el cuerpo de la función. La excepción a esta regla es si la instrucción **Return** se produce dentro de un bloque **try** y hay un bloque **Finally** correspondiente, el código del bloque **Finally** se ejecutará antes de que se devuelva la función.  
  
 Si una función devuelve porque alcanza el final del cuerpo de la función sin ejecutar una instrucción `return`, el valor devuelto es el valor **indefinido** (esto significa que el resultado de la función no se puede usar como parte de una expresión mayor).  
  
### <a name="to-correct-this-error"></a>Para corregir este error  
  
- Quite la instrucción `return` del cuerpo principal del código (ámbito global).  
  
## <a name="see-also"></a>Vea también  
 [Return (instrucción)](../../javascript/reference/return-statement-javascript.md)   
 [Objeto de función](../../javascript/reference/function-object-javascript.md)   
 [caller (Propiedad, Function)](../../javascript/reference/caller-property-function-javascript.md)