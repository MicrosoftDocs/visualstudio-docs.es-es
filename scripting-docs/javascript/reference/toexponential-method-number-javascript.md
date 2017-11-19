---
title: "toExponential (método) (número) (JavaScript) | Documentos de Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: toExponential
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords: toExponential method
ms.assetid: 7c4a6d84-3c1f-4cc4-a67d-7753e5d4ed66
caps.latest.revision: "9"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: fff2f2bc0c443fa9308c8d01dcea42a3cec9ff04
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="toexponential-method-number-javascript"></a>toExponential (Método, Number de JavaScript)
Representa un número en notación exponencial.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
numObj. toExponential([fractionDigits])  
```  
  
## <a name="parameters"></a>Parámetros  
 `numObj`  
 Obligatorio. A **número** objeto.  
  
 `fractionDigits`  
 Opcional. El número de dígitos después del separador decimal. Debe estar en el intervalo 0 - 20, ambos inclusive.  
  
## <a name="return-value"></a>Valor devuelto  
 Devuelve una representación de cadena de un número en notación exponencial. La cadena contiene un dígito delante del separador decimal y puede contener `fractionDigits` dígitos después de él.  
  
 Si `fractionDigits` no se proporciona, el `toExponential` método devuelve todos los dígitos necesarios para especificar el número de forma única.  
  
## <a name="example"></a>Ejemplo  
  
```JavaScript  
var num = new Number(123);  
var exp = num.toExponential();  
document.write(exp);  
document.write("<br/>");  
  
num = new Number(123.456);  
exp = num.toExponential(5);  
document.write(exp);  
  
// Output:   
// 1.23e+2  
// 1.23456e+2  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
 **Se aplica a**: [número de objeto](../../javascript/reference/number-object-javascript.md)  
  
## <a name="see-also"></a>Vea también  
 [toFixed (método, Number)](../../javascript/reference/tofixed-method-number-javascript.md)   
 [toPrecision (Método, Number)](../../javascript/reference/toprecision-method-number-javascript.md)