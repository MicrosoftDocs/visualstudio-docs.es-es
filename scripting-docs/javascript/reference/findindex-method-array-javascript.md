---
title: Método findIndex (matriz) (JavaScript) | Documentos de Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 3a200cf0-db67-4c7b-89f8-5e9f5dc1a926
caps.latest.revision: 3
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5c8da475b776e1c04e4fe5bfc7062318cfec952c
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
ms.locfileid: "24636585"
---
# <a name="findindex-method-array-javascript"></a>Método findIndex (matriz) (JavaScript)
Devuelve un valor de índice del primer elemento de matriz que cumple los criterios de prueba especificados en una función de devolución de llamada.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
arrayObj.findIndex(callbackfn [, thisArg]);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `arrayObj`  
 Obligatorio. Objeto de matriz.  
  
 `callbackfn`  
 Obligatorio. Función de devolución de llamada que prueba cada elemento de la matriz.  
  
 `thisArg`  
 Opcional. Especifica el objeto `this` de la función de devolución de llamada. Si no se especifica, el objeto `this` es indefinido.  
  
## <a name="remarks"></a>Comentarios  
 `findIndex` llama a la función de devolución de llamada una vez para cada elemento de la matriz en orden ascendente, hasta que un elemento devuelve `true`. En cuanto un elemento devuelve true, `findIndex` devuelve el valor de índice del elemento que devuelve true. Si ningún elemento de la matriz devuelve true, `findIndex` devuelve -1.  
  
 `findIndex` no modifica el objeto de matriz.  
  
## <a name="callback-function-syntax"></a>Sintaxis de la función de devolución de llamada  
 La sintaxis de la función de devolución de llamada es la siguiente:  
  
 `function callbackfn(value, index, thisArg)`  
  
 Puede declarar la función de devolución de llamada con un máximo de hasta tres parámetros.  
  
 Los parámetros de la función de devolución de llamada son los siguientes.  
  
|Argumento de devolución de llamada|Definición|  
|-----------------------|----------------|  
|`value`|Valor del elemento de la matriz.|  
|`index`|Índice numérico del elemento de la matriz.|  
|`arrayObj`|Objeto de matriz que se va a atravesar.|  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente, la función de devolución de llamada comprueba si cada elemento de la matriz es igual a 2.  
  
```JavaScript  
[1,2,3].findIndex(function(x) { x == 2; });  
// Returns an index value of 1.  
  
```  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se usa sintaxis de flecha para probar cada elemento. En este ejemplo, ningún elemento devuelve `true`, y `findIndex` devuelve -1.  
  
```  
[1,2,3].findIndex(x => x == 4);  
// Returns an index value of -1.   
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]