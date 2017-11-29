---
title: instanceof (operador) (JavaScript) | Documentos de Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: instanceof_JavaScriptKeyword
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords: instanceOf operator
ms.assetid: 92467bdc-56b5-42dc-adbd-a219776454d2
caps.latest.revision: "17"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 672047cb066a812d16edc693638c3d6d8295798b
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="instanceof-operator-javascript"></a>instanceof (Operador de JavaScript)
Devuelve un valor booleano que indica si un objeto es instancia de una clase concreta.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
result = object instanceof class  
```  
  
## <a name="parameters"></a>Parámetros  
 `result`  
 Obligatorio. Cualquier variable.  
  
 `object`  
 Obligatorio. Cualquier expresión de objeto.  
  
 `class`  
 Obligatorio. Cualquier clase de objeto definida.  
  
## <a name="remarks"></a>Comentarios  
 El operador `instanceof` devuelve `true` si `object` es una instancia de `class`. Devuelve `true` si `true` si `class` está presente en la cadena de prototipo del objeto. Devuelve `false` si `object` no es una instancia de `class` o si `object` es `null`.  
  
## <a name="example"></a>Ejemplo  
 En el siguiente ejemplo se muestra cómo usar el operador `instanceof`.  
  
```JavaScript  
function objTest(obj){  
    var i, t, s = "";  
    t = new Array();  
    t["Date"] = Date;  
    t["Object"] = Object;  
    t["Array"] = Array;  
        for (i in t){  
            if (obj instanceof t[i]) {   
                s += "obj is an instance of " + i + "<br/>";  
            }  
            else {  
                s += "obj is not an instance of " + i + "<br/>";  
        }  
    }  
    return(s);  
}  
  
var obj = new Date();  
document.write(objTest(obj));  
  
// Output:   
// obj is an instance of Date  
// obj is an instance of Object  
// obj is not an instance of Array  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv5](../../javascript/reference/includes/jsv5-md.md)]  
  
## <a name="see-also"></a>Vea también  
 [Precedencia de operadores](../../javascript/operator-subtractprecedence-javascript.md)   
 [Resumen de operadores (JavaScript)](../../javascript/misc/operator-subtractsummary-javascript.md)