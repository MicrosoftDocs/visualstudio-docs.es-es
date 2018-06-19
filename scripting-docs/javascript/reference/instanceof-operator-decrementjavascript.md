---
title: instanceof (operador) (JavaScript) | Documentos de Microsoft
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
- instanceof_JavaScriptKeyword
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- instanceOf operator
ms.assetid: 92467bdc-56b5-42dc-adbd-a219776454d2
caps.latest.revision: 17
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b2124fe815c89c3c157be3ea729fa7edb9d96b39
ms.sourcegitcommit: f89ed5fc2e5078213e30a6ade4604e34df48181f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/13/2018
ms.locfileid: "27799592"
---
# <a name="instanceof-operator-javascript"></a>instanceof (Operador de JavaScript)
Devuelve un valor booleano que indica si un objeto es instancia de una clase concreta.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
result = object instanceof class  
```  
  
## <a name="parameters"></a>Parámetros  
 `result`  
 Requerido. Cualquier variable.  
  
 `object`  
 Requerido. Cualquier expresión de objeto.  
  
 `class`  
 Requerido. Cualquier clase de objeto definida.  
  
## <a name="remarks"></a>Comentarios  
 El operador `instanceof` devuelve `true` si `object` es una instancia de `class`. Devuelve `true` si `class` está presente en la cadena de prototipo del objeto. Devuelve `false` si `object` no es una instancia de `class` o si `object` es `null`.  
  
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