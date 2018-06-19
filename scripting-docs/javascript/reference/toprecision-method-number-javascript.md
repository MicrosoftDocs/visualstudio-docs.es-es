---
title: toPrecision (método) (número) (JavaScript) | Documentos de Microsoft
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
- toPrecision
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- toPrecision method
ms.assetid: ac13c82f-1038-447a-823f-f755bba535ca
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: eeab7642dcd88677d1b5a7102e3cf342d7ee1d29
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
ms.locfileid: "24640725"
---
# <a name="toprecision-method-number-javascript"></a>toPrecision (Método, Number de JavaScript)
Representa un número en notación exponencial o de punto fijo con un número especificado de dígitos.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
numObj.toPrecision([precision])  
```  
  
## <a name="parameters"></a>Parámetros  
 `numObj`  
 Obligatorio. Objeto `Number`.  
  
 `precision`  
 Opcional. El número de dígitos significativos. Debe estar en el intervalo 1-21, ambos inclusive.  
  
## <a name="return-value"></a>Valor devuelto  
 Para los números en notación exponencial, `precision` - 1 se devuelven los dígitos después del separador decimal. Para los números representados en notación fija, `precision` se devuelven los dígitos significativos.  
  
 Si `precision` no se proporciona o es **indefinido**, **toString** en su lugar, se llama al método.  
  
## <a name="example"></a>Ejemplo  
 En el siguiente código se muestra cómo usar `toPrecision`:  
  
```JavaScript  
var num = new Number(123);  
var prec = num.toPrecision();  
document.write(prec);  
document.write("<br/>");  
  
num = new Number(123.456);  
prec = num.toPrecision(5);  
document.write(prec);  
  
// Output:  
// 123  
// 123.46  
  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
 **Se aplica a**: [número de objeto](../../javascript/reference/number-object-javascript.md)  
  
## <a name="see-also"></a>Vea también  
 [toFixed (método, Number)](../../javascript/reference/tofixed-method-number-javascript.md)   
 [toExponential (Método, Number)](../../javascript/reference/toexponential-method-number-javascript.md)