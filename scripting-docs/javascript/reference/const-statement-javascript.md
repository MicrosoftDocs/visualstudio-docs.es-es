---
title: Const (instrucción) (JavaScript) | Documentos de Microsoft
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
- const_JavaScriptKeyword
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- declaring variables, const statement
- const statement
ms.assetid: 3ad0840f-437f-4163-9571-86ecc5ddb987
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 68130cec4f1b1fe89d2fe3e673b28963d79aebde
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
ms.locfileid: "24634105"
---
# <a name="const-statement-javascript"></a>const (Instrucción, JavaScript)
Declara una variable con ámbito de bloque con un valor constante.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
const constant1 = value1  
```  
  
#### <a name="parameters"></a>Parámetros  
 `constant1`  
 El nombre de la variable que se declara.  
  
 `value1`  
 El valor inicial asignado a la variable.  
  
## <a name="remarks"></a>Comentarios  
 Use la `const` instrucción para declarar una variable con un valor constante, el ámbito de los cuales se restringe al bloque en el que se declara. No se puede cambiar el valor de la variable.  
  
 Una variable declarada con `const` debe inicializarse cuando se declara.  
  
## <a name="example"></a>Ejemplo  
 En el siguiente ejemplo se muestra el uso de la instrucción `const`.  
  
```JavaScript  
var c = 10;  
{  
    const c = 2;  
   // At this point, c = 2.  
}  
// At this point, c = 10.  
  
// Additional ways to declare a variable using const.  
const name = "Thomas Jefferson";  
const answer = 42, numpages = 10;  
const myarray = new Array();  
  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]  
  
## <a name="see-also"></a>Vea también  
 [Let (instrucción)](../../javascript/reference/let-statement-javascript.md)   
 [new (Operador, Referencia de C#)](../../javascript/reference/new-operator-decrementjavascript.md)   
 [Array (objeto)](../../javascript/reference/array-object-javascript.md)   
 [Variables](../../javascript/variables-javascript.md)