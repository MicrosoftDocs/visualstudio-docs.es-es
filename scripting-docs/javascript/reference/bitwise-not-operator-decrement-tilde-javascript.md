---
title: Bit a bit NOT (operador) (~) (JavaScript) | Documentos de Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: ~
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- NOT operator
- bitwise operators, NOT operator
ms.assetid: 39f92474-fe05-4a8b-9ad8-caca93f82bca
caps.latest.revision: "10"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: aec64b055b260efb7a4b0d952aed9b3a5d7ddc82
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="bitwise-not-operator--javascript"></a>Operador NOT bit a bit (~) (JavaScript)
Realiza una operación NOT bit a bit (negación) en una expresión.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
result = ~ expression  
```  
  
## <a name="parameters"></a>Parámetros  
 *resultado*  
 Cualquier variable.  
  
 *expresión*  
 Cualquier expresión.  
  
## <a name="remarks"></a>Comentarios  
 Todos los operadores unarios, como el `~` , evalúan las expresiones como se indica a continuación:  
  
-   Si se aplica a indefinido o `null` se genera expresiones, un error en tiempo de ejecución.  
  
-   Objetos se convierten en cadenas.  
  
-   Las cadenas se convierten a números si es posible. Si no es así, se produce un error de tiempo de ejecución.  
  
-   Valores booleanos se tratan como números (0 si es false, 1 si es true).  
  
 El operador se aplica al número resultante.  
  
 El `~` operador examina la representación binaria de los valores de la expresión y realiza una operación de negación bit a bit en ella.  
  
 Cualquier dígito que sea un 1 en la expresión se convierte en un valor 0 en el resultado. Cualquier dígito que sea un 0 en la expresión se convierte en un 1 en el resultado.  
  
 En el ejemplo siguiente se muestra el uso de bit a bit NOT (~) (operador).  
  
```  
var temp = ~5;  
```  
  
 El valor resultante es -6, como se muestra en la tabla siguiente.  
  
|Expresión|Valor binario (complemento de dos)|Valor decimal|  
|----------------|---------------------------------------|-------------------|  
|5|00000000 00000000 00000000 00000101|5|  
|~5|11111111 11111111 11111111 11111010|-6|  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>Vea también  
 [Lógico NOT (operador) (!)](../../javascript/reference/logical-not-operator-decrement-exclpt-javascript.md)   
 [Precedencia de operadores](../../javascript/operator-subtractprecedence-javascript.md)   
 [Resumen de operadores (JavaScript)](../../javascript/misc/operator-subtractsummary-javascript.md)