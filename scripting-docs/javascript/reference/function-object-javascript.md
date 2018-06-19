---
title: Función (objeto de JavaScript) | Documentos de Microsoft
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
- function
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- Function object
ms.assetid: d3834767-203c-475e-848c-95c423ba15b6
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 4392fd57967e6312c96af50bdff2415d0f2dcd4d
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
ms.locfileid: "24637375"
---
# <a name="function-object-javascript"></a>Function (Objeto de JavaScript)
Crea una nueva función.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
function functionName([argname1  [, ...[, argnameN]]])  
{  
   body  
}  
```  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
functionName = new Function( [argname1,  [... argnameN,]] body );  
```  
  
## <a name="parameters"></a>Parámetros  
 `functionName`  
 Obligatorio. El nombre de la función recién creada  
  
 `argname1...argnameN`  
 Opcional. Una lista de argumentos de que la función acepta.  
  
 `body`  
 Opcional. Una cadena que contiene el bloque de [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] código que se ejecuta cuando se llama a la función.  
  
## <a name="remarks"></a>Comentarios  
 La función es un tipo de datos básicos en [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]. La sintaxis 1 crea un valor de la función [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] convierte en un `Function` objeto cuando sea necesario. [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]Convierte `Function` objetos creados por la sintaxis 2 en valores de las funciones en el momento en que se llama la función.  
  
 La sintaxis 1 es la manera estándar de crear nuevas funciones en [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]. Sintaxis 2 es una forma alternativa que se utiliza para crear objetos de función explícitamente.  
  
 Por ejemplo, para declarar una función que agrega los dos argumentos pasados a él, puede hacerlo de dos maneras:  
  
## <a name="example-1"></a>Ejemplo 1  
  
```JavaScript  
function add(x, y)  
{  
   return(x + y);  
}  
```  
  
## <a name="example-2"></a>Ejemplo 2  
  
```  
var add = function(x, y) {  
     return(x+y);  
}  
```  
  
 En cualquier caso, llamar a la función con una línea de código similar al siguiente:  
  
```JavaScript  
add(2, 3);  
```  
  
> [!NOTE]
>  Cuando se llama a una función, asegúrese de incluir siempre los paréntesis y los argumentos necesarios. Llamar a una función sin paréntesis hace que la función propia que se devuelvan en lugar del valor devuelto de la función.  
  
## <a name="properties"></a>Propiedades  
 [0... n (propiedades)](../../javascript/reference/0-dot-dot-dot-n-properties-arguments-javascript.md) &#124;[ arguments (propiedad)](../../javascript/reference/arguments-property-function-javascript.md) &#124; [callee (propiedad)](../../javascript/reference/callee-property-arguments-javascript.md) &#124; [caller (propiedad)](../../javascript/reference/caller-property-function-javascript.md) &#124; [constructor (propiedad)](../../javascript/reference/constructor-property-object-javascript.md) &#124; [length (propiedad, Function)](../../javascript/reference/length-property-function-javascript.md) &#124; [prototype (propiedad)](../../javascript/reference/prototype-property-object-javascript.md)  
  
## <a name="methods"></a>Métodos  
 [Apply (método)](../../javascript/reference/apply-method-function-javascript.md) &#124; [bind (método)](../../javascript/reference/bind-method-function-javascript.md) &#124; [llame al método](../../javascript/reference/call-method-function-javascript.md) &#124; [toString (método)](../../javascript/reference/tostring-method-object-javascript.md) &#124; [valueOf (método)](../../javascript/reference/valueof-method-object-javascript.md)  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]  
  
## <a name="see-also"></a>Vea también  
 [Function (instrucción)](../../javascript/reference/function-statement-javascript.md)   
 [new (Operador, Referencia de C#)](../../javascript/reference/new-operator-decrementjavascript.md)   
 [var (Instrucción)](../../javascript/reference/var-statement-javascript.md)