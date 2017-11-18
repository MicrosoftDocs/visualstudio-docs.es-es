---
title: "Función Array.From (matriz) (JavaScript) | Documentos de Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 1bf59a99-f860-4c4d-b4c6-d5f1f946a490
caps.latest.revision: "3"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a240cb439942bfeb6b4c9a1febb4d24cef1c5c18
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="arrayfrom-function-array-javascript"></a>Función Array.from (matriz) (JavaScript)
Devuelve una matriz de un objeto iterable o similar a una matriz.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
Array.from (arrayLike [ , mapfn [ , thisArg ] ] );  
```  
  
#### <a name="parameters"></a>Parámetros  
 `arrayLike`  
 Obligatorio. Objeto iterable o similar a una matriz.  
  
 `mapfn`  
 Opcional. Función de asignación para llamar a cada elemento de `arrayLike`.  
  
 `thisArg`  
 Opcional. Especifica el objeto `this` de la función de asignación.  
  
## <a name="remarks"></a>Comentarios  
 El parámetro `arrayLike` debe ser un objeto con elementos indizados y una propiedad `length` o un objeto iterable, como un objeto `Set`.  
  
 Se llama a la función de asignación opcional en cada elemento de la matriz.  
  
## <a name="example"></a>Ejemplo  
 El ejemplo siguiente devuelve una matriz de una colección de nodos de elemento DOM.  
  
```JavaScript  
var elemArr = Array.from(document.querySelectorAll('*'));  
var elem = elemArr[0]; // elem contains a reference to the first DOM element  
  
```  
  
## <a name="example"></a>Ejemplo  
 El ejemplo siguiente devuelve una matriz de caracteres.  
  
```JavaScript  
var charArr = Array.from("abc");  
// charArr[0] == "a";  
```  
  
## <a name="example"></a>Ejemplo  
 El ejemplo siguiente devuelve una matriz de objetos contenidos en la colección.  
  
```JavaScript  
var setObj = new Set("a", "b", "c");  
var objArr = Array.from(setObj);  
// objArr[1] == "b";   
```  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra el uso de la sintaxis de flecha y una función de asignación para cambiar el valor de los elementos.  
  
```JavaScript  
var arr = Array.from([1, 2, 3], x => x * 10);  
// arr[0] == 10;  
// arr[1] == 20;  
// arr[2] == 30;  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]