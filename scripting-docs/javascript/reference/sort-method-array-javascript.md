---
title: "Sort (método) (matriz) (JavaScript) | Documentos de Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: sort
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords: Sort method
ms.assetid: 9bd8b54a-c838-4806-85c8-62eebe6bc48c
caps.latest.revision: "15"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2d098b47591ca7bbb4e3e8da5e5c14f8c0e9b255
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="sort-method-array-javascript"></a>sort (Método, Array de JavaScript)
Ordena un `Array`.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
arrayobj.sort(sortFunction)   
```  
  
## <a name="parameters"></a>Parámetros  
 `arrayObj`  
 Obligatorio. Cualquier objeto `Array`.  
  
 `sortFunction`  
 Opcional. El nombre de la función que se usa para determinar el orden de los elementos. Si se omite, los elementos se ordenan en orden ascendente, orden de los caracteres ASCII.  
  
## <a name="return-value"></a>Valor devuelto  
 La matriz ordenada.  
  
## <a name="remarks"></a>Comentarios  
 El `sort` método ordena la `Array` objeto in situ; no nuevos `Array` objeto se crea durante la ejecución.  
  
 Si proporciona una función en la `sortFunction` argumento, debe devolver uno de los siguientes valores:  
  
-   Un valor negativo si el primer argumento pasado es menor que el segundo argumento.  
  
-   Cero si los dos argumentos son equivalentes.  
  
-   Un valor positivo si el primer argumento es mayor que el segundo argumento.  
  
## <a name="example"></a>Ejemplo  
 En el siguiente ejemplo, se muestra cómo utilizar el método `sort`.  
  
```JavaScript  
var a = new Array(4, 11, 2, 10, 3, 1);  
  
var b = a.sort();  
document.write(b);  
document.write("<br/>");  
  
// This is ASCII character order.  
// Output: 1,10,11,2,3,4)  
  
// Sort the array elements with a function that compares array elements.  
b = a.sort(CompareForSort);  
document.write(b);  
document.write("<br/>");  
// Output: 1,2,3,4,10,11.  
  
// Sorts array elements in ascending order numerically.  
function CompareForSort(first, second)  
{  
    if (first == second)  
        return 0;  
    if (first < second)  
        return -1;  
    else  
        return 1;   
}  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]