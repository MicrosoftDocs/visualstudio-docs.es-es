---
title: "toFixed (método, Number) (JavaScript) | Documentos de Microsoft"
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
- toFixed
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- toFixed method
ms.assetid: b5f03400-865e-4ab2-818c-f734c0f6d6f0
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: dd51dd67632f4e6417fee72fd19575025423bbf1
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="tofixed-method-number-javascript"></a>toFixed (Método, Number de JavaScript)
Representa un número en notación de punto fijo.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
numObj.toFixed([fractionDigits])  
```  
  
## <a name="parameters"></a>Parámetros  
 `numObj`  
 Requiere un `Number` objeto.  
  
 `fractionDigits`  
 Opcional. El número de dígitos después del separador decimal. Debe estar en el intervalo 0 - 20, ambos inclusive.  
  
## <a name="return-value"></a>Valor devuelto  
 Devuelve una representación de cadena de un número en notación de punto fijo, que contiene `fractionDigits` dígitos después del separador decimal.  
  
 Si `fractionDigits` no se proporciona o **indefinido**, el valor predeterminado es cero.  
  
## <a name="example"></a>Ejemplo  
 En el siguiente código se muestra cómo usar `toFixed`:  
  
```JavaScript  
var num = new Number(123);  
var fix = num.toFixed();  
document.write(fix);  
document.write("<br/>");  
  
num = new Number(123.456);  
fix = num.toFixed(5);  
document.write(fix);  
  
// Output:  
// 123  
123.45600  
  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
 **Se aplica a**: [número de objeto](../../javascript/reference/number-object-javascript.md)  
  
## <a name="see-also"></a>Vea también  
 [toExponential (método, Number)](../../javascript/reference/toexponential-method-number-javascript.md)   
 [toPrecision (Método, Number)](../../javascript/reference/toprecision-method-number-javascript.md)