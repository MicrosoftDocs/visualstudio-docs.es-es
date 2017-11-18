---
title: "Let (instrucción) (JavaScript) | Documentos de Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: let_JavaScriptKeyword
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- let statement
- declaring variables, let statement
ms.assetid: c7e4f8a9-8f54-47b6-aed2-956959c1ecfd
caps.latest.revision: "7"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c447a1bf0c430771ff146965a592f7e160e2055b
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="let-statement-javascript"></a>let (Instrucción, JavaScript)
Declara una variable con ámbito de bloque.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
let variable1 = value1  
```  
  
#### <a name="parameters"></a>Parámetros  
 `variable1`  
 El nombre de la variable que se declara.  
  
 `value1`  
 El valor inicial asignado a la variable.  
  
## <a name="remarks"></a>Comentarios  
 Use la `let` instrucción para declarar una variable, el ámbito de los cuales se restringe al bloque en el que se declara. Puede asignar valores a las variables al declararlas o más adelante en la secuencia de comandos.  
  
 Una variable declarada con `let` no se puede usar antes de que se producirá un error o su declaración.  
  
 Si no se inicializa la variable en el `let` instrucción, se asigna automáticamente el [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] valor `undefined`.  
  
## <a name="example"></a>Ejemplo  
 En el siguiente ejemplo se muestra el uso de la instrucción `let`.  
  
```JavaScript  
var  l = 10;  
{  
    let l = 2;  
   // At this point, l = 2.  
}  
// At this point, l = 10.  
  
// Additional ways to declare a variable using let.  
let index;  
let name = "Thomas Jefferson";  
let answer = 42, counter, numpages = 10;  
let myarray = new Array();  
  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]  
  
## <a name="see-also"></a>Vea también  
 [Const (instrucción)](../../javascript/reference/const-statement-javascript.md)   
 [new (Operador, Referencia de C#)](../../javascript/reference/new-operator-decrementjavascript.md)   
 [Array (objeto)](../../javascript/reference/array-object-javascript.md)   
 [Variables](../../javascript/variables-javascript.md)