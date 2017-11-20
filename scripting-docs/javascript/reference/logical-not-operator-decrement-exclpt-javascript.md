---
title: "Lógico NOT (operador) (!) (JavaScript) | Documentos de Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: '!'
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- Logical NOT operator
- '! operator'
- '! operator, about ! operator'
ms.assetid: 68c3dc71-ae95-4293-9155-67405846d71d
caps.latest.revision: "7"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 29c27b9cd670989eb2112de5067e68bd09d76903
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="logical-not-operator--javascript"></a>Operador lógico NOT (!) (JavaScript)
Realiza una negación lógica en una expresión.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
result = !expression  
```  
  
## <a name="parameters"></a>Parámetros  
 *resultado*  
 Cualquier variable.  
  
 *expresión*  
 Cualquier expresión.  
  
## <a name="remarks"></a>Comentarios  
 La tabla siguiente se muestra cómo *resultado* viene determinado.  
  
|Si `expression` es|A continuación, `result` es|  
|------------------------|----------------------|  
|True|False|  
|False|True|  
  
 Todos los operadores unarios, como el **!** evalúan las expresiones como se indica a continuación:  
  
-   Si se aplica a indefinido o `null` se genera expresiones, un error en tiempo de ejecución.  
  
-   Objetos se convierten en cadenas.  
  
-   Las cadenas se convierten a números si es posible. Si no es así, se produce un error de tiempo de ejecución.  
  
-   Valores booleanos se tratan como números (0 si es false, 1 si es true).  
  
 El operador se aplica al número resultante.  
  
 Para el **!** operador, si *expresión* es distinto de cero, *resultado* es cero. Si *expresión* es cero, *resultado* es 1.  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>Vea también  
 [Bit a bit NOT (operador) (~)](../../javascript/reference/bitwise-not-operator-decrement-tilde-javascript.md)   
 [Precedencia de operadores](../../javascript/operator-subtractprecedence-javascript.md)   
 [Resumen de operadores (JavaScript)](../../javascript/misc/operator-subtractsummary-javascript.md)