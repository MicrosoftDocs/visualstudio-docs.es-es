---
title: "Operador de asignación de suma (+=) (JavaScript) | Documentos de Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: +=
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- addition assignment operator (+=)
- += operator
- assignment operators, JavaScript
ms.assetid: 8517d05c-38b0-4107-bea4-253eb420f438
caps.latest.revision: "10"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 38d86c537dda90dd7f44923b97384b3609dad5ba
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="addition-assignment-operator--javascript"></a>Operador de asignación y suma (+=) (JavaScript)
Agrega el valor de una expresión al valor de una variable y asigna el resultado a la variable.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
result += expression   
```  
  
## <a name="parameters"></a>Parámetros  
 `result`  
 Cualquier variable.  
  
 `expression`  
 Cualquier expresión.  
  
## <a name="remarks"></a>Comentarios  
 Utilizar este operador es exactamente lo mismo que especificar: `result = result + expression`.  
  
 Los tipos de las dos expresiones determinan el comportamiento de la `+=` operador.  
  
|Si|A continuación|  
|--------|----------|  
|Ambas expresiones son numéricos o booleanos|Agregar|  
|Ambas expresiones son cadenas|Concatenar|  
|Una expresión es numérica y la otra es una cadena|Concatenar|  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>Vea también  
 [Operador de suma (+)](../../javascript/reference/addition-operator-decrement-javascript.md)   
 [Precedencia de operadores](../../javascript/operator-subtractprecedence-javascript.md)   
 [Resumen de operadores (JavaScript)](../../javascript/misc/operator-subtractsummary-javascript.md)