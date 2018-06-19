---
title: Operador de suma (+) (JavaScript) | Documentos de Microsoft
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
- +
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- arithmetic operators, addition
- strings [Visual Studio], concatenating
- concatenation operators, vs. addition operator
- addition operator
- + operator
ms.assetid: ec1237d3-e78b-4e77-bd7d-c0204cf03acd
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 70ff02b1f234da7b88d28e66da82262ccef7bfaf
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
ms.locfileid: "24633265"
---
# <a name="addition-operator--javascript"></a>Operador de suma (+) (JavaScript)
Agrega el valor de una expresión numérica a otra o concatena dos cadenas.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
result = expression1 + expression2  
```  
  
## <a name="parameters"></a>Parámetros  
 `result`  
 Cualquier variable.  
  
 `expression1`  
 Cualquier expresión.  
  
 `expression2`  
 Cualquier expresión.  
  
## <a name="remarks"></a>Comentarios  
 Los tipos de las dos expresiones determinan el comportamiento de la  **+**  operador.  
  
|Si|A continuación|  
|--------|----------|  
|Ambas expresiones son numéricos o booleanos|Agregar|  
|Ambas expresiones son cadenas|Concatenar|  
|Una expresión es numérica y la otra es una cadena|Concatenar|  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>Vea también  
 [Operador de asignación de suma (+=)](../../javascript/reference/addition-assignment-operator-decrement-equal-javascript.md)   
 [Precedencia de operadores](../../javascript/operator-subtractprecedence-javascript.md)   
 [Resumen de operadores (JavaScript)](../../javascript/misc/operator-subtractsummary-javascript.md)