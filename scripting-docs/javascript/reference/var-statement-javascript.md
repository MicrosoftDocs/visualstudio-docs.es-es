---
title: "var (instrucción) (JavaScript) | Documentos de Microsoft"
ms.custom: 
ms.date: 01/22/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: var_JavaScriptKeyword
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- declaring variables, var statement
- var statement
ms.assetid: 56f900af-a5c4-4667-9664-5956d30f0aae
caps.latest.revision: "18"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 839b6904fa59b6f4ea9a5c4d8e00213cd351517a
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="var-statement-javascript"></a>var (Instrucción de JavaScript)
Declara una variable.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
var variable1 = value1  
```  
  
## <a name="parameters"></a>Parámetros  
 `variable1`  
 El nombre de la variable que se declara.  
  
 `value1`  
 El valor inicial asignado a la variable.  
  
## <a name="remarks"></a>Comentarios  
 Use la `var` instrucción para declarar las variables. Puede asignar valores a las variables al declararlas o más adelante en la secuencia de comandos.  
  
 Una variable se declara la primera vez aparece en la secuencia de comandos.  
  
 Puede declarar una variable sin utilizar la `var` (palabra clave) y asignar un valor a él. Esto se conoce como un *declaración implícita*, y no se recomienda. Una declaración implícita proporciona el ámbito de la variable global. Cuando se declara una variable en el nivel de procedimiento, sin embargo, normalmente no desea que tienen ámbito global. Para evitar que proporciona el ámbito de la variable global, se debe utilizar el `var` palabra clave en la declaración de variables.  
  
 Si no se inicializa la variable en el `var` instrucción, se asigna automáticamente el [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] valor `undefined`.  
  
## <a name="example"></a>Ejemplo  
 Los siguientes ejemplos ilustran el uso de la `var` instrucción.  
  
```JavaScript  
var index;  
var name = "Thomas Jefferson";  
var answer = 42, counter, numpages = 10;  
var myarray = new Array();  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>Vea también  
 [Function (instrucción)](../../javascript/reference/function-statement-javascript.md)   
 [new (Operador, Referencia de C#)](../../javascript/reference/new-operator-decrementjavascript.md)   
 [Array (objeto)](../../javascript/reference/array-object-javascript.md)   
 [Variables](../../javascript/variables-javascript.md)