---
title: Number (objeto de JavaScript) | Documentos de Microsoft
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
- Number_JavaScript
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- Number object
ms.assetid: 76e87c37-cf6c-46cc-bafa-04be1fe3d78d
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7cbe58fdc9673a8fffe35b8b15d7edbf86ffa655
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="number-object-javascript"></a>Number (Objeto de JavaScript)
Objeto que representa un número de cualquier tipo. Todos los números de JavaScript son números de punto flotante de 64 bits.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
numObj = new Number(value)  
```  
  
## <a name="parameters"></a>Parámetros  
 `numObj`  
 Obligatorio. Nombre de variable a la que se asigna el objeto `Number`.  
  
 `value`  
 Obligatorio. Valor numérico.  
  
## <a name="remarks"></a>Comentarios  
 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] crea objetos `Number` cuando se establece una variable en un valor numérico, por ejemplo `var num = 255.336;`. Rara vez es necesario crear objetos `Number` explícitamente.  
  
 El objeto `Number` tiene sus propios métodos y propiedades, además de los métodos y propiedades heredados de `Object`. Los números se convierten en cadenas en determinadas circunstancias, por ejemplo, cuando un número se agrega o se concatena con una cadena, así como por medio del método `toString`. Para obtener más información, consulte [operador de suma (+)](../../javascript/reference/addition-operator-decrement-javascript.md).  
  
 JavaScript tiene varias constantes numéricas. Para obtener una lista completa, consulte [constantes numéricas](../../javascript/reference/number-constants-javascript.md).  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="properties"></a>Propiedades  
 En la tabla siguiente se muestran las propiedades del objeto `Number`.  
  
|Propiedad|Descripción|  
|--------------|-----------------|  
|[constructor (Propiedad)](../../javascript/reference/constructor-property-object-javascript.md)|Especifica la función que crea un objeto.|  
|[prototype (Propiedad)](../../javascript/reference/prototype-property-object-javascript.md)|Devuelve una referencia al prototipo correspondiente a una clase de objetos.|  
  
## <a name="functions"></a>Funciones  
 En la tabla siguiente se enumera las funciones de la `Number` objeto.  
  
|Función|Descripción|  
|--------------|-----------------|  
|[Función Number.isFinite](../../javascript/reference/number-isfinite-function-number-javascript.md)|Devuelve un valor booleano que indica si un valor es finito.|  
|[Función Number.isInteger](../../javascript/reference/number-isinteger-function-number-javascript.md)|Devuelve un valor booleano que indica si un valor es un entero.|  
|[Función Number.isNaN](../../javascript/reference/number-isnan-function-number-javascript.md)|Devuelve un valor booleano que indica si un valor es el valor reservado `NaN` (no un número).|  
|[Number.isSafeInteger](../../javascript/reference/number-issafeinteger-number-javascript.md)|Devuelve un valor booleano que indica si un valor puede representarse de forma segura en JavaScript.|  
  
## <a name="methods"></a>Métodos  
 En la tabla siguiente se enumera los métodos de la `Number` objeto.  
  
|Método|Descripción|  
|------------|-----------------|  
|[hasOwnProperty (Método)](../../javascript/reference/hasownproperty-method-object-javascript.md)|Devuelve un valor booleano que indica si un objeto tiene una propiedad con el nombre especificado.|  
|[isPrototypeOf (método)](../../javascript/reference/isprototypeof-method-object-javascript.md)|Devuelve un valor booleano que indica si un objeto existe en la jerarquía de prototipo de otro objeto.|  
|[propertyIsEnumerable (Método)](../../javascript/reference/propertyisenumerable-method-object-javascript.md)|Devuelve un valor booleano que indica si una propiedad especificada forma parte de un objeto y si se puede enumerar.|  
|[toExponential (método)](../../javascript/reference/toexponential-method-number-javascript.md)|Devuelve una cadena que contiene un número representado en notación exponencial.|  
|[toFixed (método)](../../javascript/reference/tofixed-method-number-javascript.md)|Devuelve una cadena que representa un número en notación de punto fijo.|  
|[toLocaleString (método)](../../javascript/reference/tolocalestring-number.md)|Devuelve un objeto convertido en una cadena según la configuración regional actual.|  
|[toPrecision (método)](../../javascript/reference/toprecision-method-number-javascript.md)|Devuelve una cadena que contiene un número representado en notación exponencial o de punto fijo y que tiene un número de dígitos especificado.|  
|[toString (Método)](../../javascript/reference/tostring-method-object-javascript.md)|Devuelve una representación de cadena de un objeto.|  
|[valueOf (Método)](../../javascript/reference/valueof-method-object-javascript.md)|Devuelve el valor primitivo del objeto especificado.|  
  
## <a name="see-also"></a>Vea también  
 [Objetos de JavaScript](../../javascript/reference/javascript-objects.md)   
 [Math (objeto)](../../javascript/reference/math-object-javascript.md)   
 [new (operador)](../../javascript/reference/new-operator-decrementjavascript.md)