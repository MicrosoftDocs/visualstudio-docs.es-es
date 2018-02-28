---
title: "Eval (función) (JavaScript) | Documentos de Microsoft"
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
- eval
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- eval function
- parsing, code
- parser
ms.assetid: 85587e39-9325-4b75-b9f9-9d7d475a2120
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 388e486f58bb70fd192701060a5faefaed8bd98e
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="eval-function-javascript"></a>eval (Función de JavaScript)
Se evalúa como [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] de código y lo ejecuta.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
eval(codeString)   
```  
  
## <a name="parameters"></a>Parámetros  
 `codeString`  
 Obligatorio. A `String` valor que contiene válido [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] código.  
  
## <a name="remarks"></a>Comentarios  
 El `eval` función permite la ejecución dinámica de [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] el código fuente.  
  
 El `codeString` cadena se analiza el [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] analizador y ejecuta.  
  
 El código ha pasado a la `eval` función se ejecuta en el mismo contexto que la llamada a la `eval` (función).  
  
 Siempre que sea posible, utilice la [JSON.parse (función)](../../javascript/reference/json-parse-function-javascript.md) deserializar texto JavaScript Object Notation (JSON). El `JSON.parse` función es más seguro y se ejecuta más rápido que el `eval` función.  
  
## <a name="example"></a>Ejemplo  
 El código siguiente inicializa la variable `myDate` a una fecha de prueba.  
  
```JavaScript  
var dateFn = "Date(1971,3,8)";  
var myDate;  
eval("myDate = new " + dateFn + ";");  
  
document.write(myDate);  
  
// Output: Thu Apr 8 00:00:00 PDT 1971  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **Se aplica a**: [Global (objeto)](../../javascript/reference/global-object-javascript.md)  
  
## <a name="see-also"></a>Vea también  
 [String (Objeto)](../../javascript/reference/string-object-javascript.md)