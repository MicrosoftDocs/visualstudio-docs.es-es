---
title: while (instrucción) (JavaScript) | Documentos de Microsoft
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
- while_JavaScriptKeyword
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- loop structures, while statements
- while statement
ms.assetid: d63777cf-0e1a-4555-8d3a-334381001f48
caps.latest.revision: 13
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: de64bf9181a0fc86a528fa7af21216b99530f217
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
ms.locfileid: "24641255"
---
# <a name="while-statement-javascript"></a>while (Instrucción de JavaScript)
Ejecuta una instrucción o una serie de instrucciones hasta que una condición especificada sea `false`.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
while (expression) {  
    statements  
}   
```  
  
## <a name="parameters"></a>Parámetros  
 `expression`  
 Obligatorio. Una expresión booleana que se comprueba antes de cada iteración del bucle. Si `expression` es `true`, se ejecuta el bucle. Si `expression` es `false`, se termina el bucle.  
  
 `statements`  
 Opcional. Una o más instrucciones que se ejecutarán si `expression` es `true`.  
  
## <a name="remarks"></a>Comentarios  
 El `while` instrucción comprobaciones `expression` antes de que un bucle se ejecuta primero. Si `expression` es `false` en este momento, el bucle nunca se ejecuta.  
  
## <a name="example"></a>Ejemplo  
 En el siguiente ejemplo se muestra el uso de la instrucción `while`.  
  
```JavaScript  
var i = 0;  
var j = 10;  
while (i < 100) {  
    if (i == j)  
        break;  
    i++;  
}  
document.write(i);  
  
// Output: 10  
  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>Vea también  
 [break (Instrucción)](../../javascript/reference/break-statement-javascript.md)   
 [Continue (instrucción)](../../javascript/reference/continue-statement-javascript.md)   
 [Instrucción while](../../javascript/reference/do-dot-dot-dot-while-statement-javascript.md)   
 [para la instrucción](../../javascript/reference/for-statement-javascript.md)   
 [for...in (Instrucción)](../../javascript/reference/for-dot-dot-dot-in-statement-javascript.md)