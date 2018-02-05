---
title: "Sort (método) (matriz) (JavaScript) | Documentos de Microsoft"
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
- sort
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- Sort method
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0462e60e623b99af458beb61eb7ef4215fe8ef41
ms.sourcegitcommit: b01406355e3b97547b7cbf8ce3960f101b165cec
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/05/2018
---
# <a name="sort-method-array-javascript"></a>sort (Método, Array de JavaScript)
Ordena un `Array`.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
arrayobj.sort(sortFunction)   
```  
  
## <a name="parameters"></a>Parámetros  
 `arrayObj`  
 Requerido. Cualquier objeto `Array`.  
  
 `sortFunction`  
 Opcional. El nombre de la función que se usa para determinar el orden de los elementos. Si se omite, los elementos se ordenan en orden ascendente, orden de los caracteres ASCII.  
  
## <a name="return-value"></a>Valor devuelto  
 La matriz ordenada.  
  
## <a name="remarks"></a>Comentarios  
 El `sort` método ordena la `Array` objeto in situ; no nuevos `Array` objeto se crea durante la ejecución.  
  
 `sortFunction`toma dos argumentos y debe devolver uno de los siguientes valores:  
  
-   Un valor negativo (menor que 0) si el primer argumento pasado es menor que el segundo argumento.  Se ordena el primer argumento para un índice más bajo.
  
-   Cero (0) si los dos argumentos son equivalentes.  Los dos argumentos se ordenan con respecto a otros elementos de la matriz, pero no se ordenan con respecto a entre sí.
  
-   Un valor positivo (mayor que 0) si el primer argumento es mayor que el segundo argumento.  El segundo argumento está ordenado en un índice más bajo.
  
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