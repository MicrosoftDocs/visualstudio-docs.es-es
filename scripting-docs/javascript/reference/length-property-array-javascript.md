---
title: Length (propiedad, Array) (JavaScript) | Documentos de Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: length Property
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- Array object
- Length property
- length property (array)
ms.assetid: e1c6377c-2e84-440a-9660-f1f512e4a938
caps.latest.revision: "11"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6e69fd5387b1d7430491b1693dec07581f165cc9
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="length-property-array-javascript"></a>length (Propiedad, Array de JavaScript)
Obtiene o establece la longitud de la matriz. Se trata de un número que supera en uno al elemento mayor definido en una matriz.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
numVar = arrayObj.length   
```  
  
## <a name="parameters"></a>Parámetros  
 `numVar`  
 Obligatorio. Cualquier número.  
  
 `arrayObj`  
 Obligatorio. Cualquier objeto `Array`.  
  
## <a name="remarks"></a>Comentarios  
 En JavaScript, las matrices son dispersas y los elementos de una matriz no tienen que ser contiguos. La propiedad `length` no es necesariamente el número de elementos de la matriz. Por ejemplo, en la siguiente definición de matriz, `my_array.length` contiene 7, no 2:  
  
```JavaScript  
var my_array = new Array( );  
my_array[0] = "Test";  
my_array[6] = "Another Test";  
```  
  
 Si hace que la propiedad `length` sea menor que su valor anterior, la matriz se trunca y se pierden los elementos con índices de matriz iguales o mayores que el nuevo valor de la propiedad `length`.  
  
 Si hace que la propiedad length sea mayor que su valor anterior, la matriz se expande y los elementos nuevos creados tienen el valor `undefined`.  
  
 En el ejemplo siguiente se muestra el uso de la propiedad `length`.  
  
```JavaScript  
var a;  
a = new Array(0,1,2,3,4);  
document.write(a.length);  
  
// Output  
// 5  
  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]  
  
> [!NOTE]
>  A partir del modo estándar de Internet Explorer 9, las comas finales incluidas en la inicialización de una matriz se controlan de forma diferente.