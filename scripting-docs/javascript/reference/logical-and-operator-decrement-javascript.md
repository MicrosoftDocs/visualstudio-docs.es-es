---
title: Operador lógico AND (&amp;&amp;) (JavaScript) | Documentos de Microsoft
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
- '&&'
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- logical AND operator
- '&& operator'
ms.assetid: 4714dea9-1999-444a-8acd-72f0851e4f65
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2107eb89c5ca964cf08172050b49307cb150590f
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
ms.locfileid: "24638285"
---
# <a name="logical-and-operator-ampamp-javascript"></a>Operador lógico AND (&amp;&amp;) (JavaScript)
Realiza una conjunción lógica de dos expresiones.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
result = expression1 && expression2   
```  
  
## <a name="parameters"></a>Parámetros  
 `result`  
 Cualquier variable.  
  
 `expression1`  
 Cualquier expresión.  
  
 `expression2`  
 Cualquier expresión.  
  
## <a name="remarks"></a>Comentarios  
 Si `expression1` se evalúa como `false`, `result` es `expression1`. En caso contrario, `result` es `expression2`. Por consiguiente, la operación devuelve `true` si ambos operandos son true; de lo contrario, devuelve `false`.  
  
 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] usa las reglas siguientes para convertir valores no booleanos en valores booleanos:  
  
-   Todos los objetos se consideran `true`.  
  
-   Las cadenas se consideran `false` si están vacías.  
  
-   `null` y `undefined` se consideran `false`.  
  
-   Un número es `false` si es cero.  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>Vea también  
 [Precedencia de operadores](../../javascript/operator-subtractprecedence-javascript.md)   
 [Resumen de operadores (JavaScript)](../../javascript/misc/operator-subtractsummary-javascript.md)