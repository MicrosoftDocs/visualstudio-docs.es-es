---
title: Propiedad Length (función) (JavaScript) | Documentos de Microsoft
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
- length Property
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- Length property
- length property (function)
ms.assetid: fdc8e1c9-0dac-4e1b-ba3a-11073c37ef63
caps.latest.revision: 15
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 4fbd0334c18da2c6ef8de8366555d79f791e6855
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
ms.locfileid: "24637835"
---
# <a name="length-property-function-javascript"></a>length (Propiedad, Function de JavaScript)
Obtiene el número de argumentos definidos para una función.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
functionName.length  
```  
  
## <a name="remarks"></a>Comentarios  
 Requerido *functionName* es el nombre de la función.  
  
 El **longitud** propiedad de una función se inicializa el motor de scripting que el número de argumentos en la definición de la función cuando se crea una instancia de la función.  
  
 ¿Qué ocurre cuando se llama a una función con un número de argumentos diferentes del valor de su **longitud** propiedad depende de la función.  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra el uso de la **longitud** propiedad:  
  
```JavaScript  
function ArgTest(a, b){  
    var s = "";  
  
    s += "Expected Arguments: " + ArgTest.length;  
    s += "<br />";  
    s += "Passed Arguments: " + arguments.length;  
  
    return s;  
}  
  
document.write(ArgTest(1, 2));  
  
// Output:   
// Expected Arguments: 2  
// Passed Arguments: 2  
  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]  
  
## <a name="see-also"></a>Vea también  
 [arguments (propiedad) (función)](../../javascript/reference/arguments-property-function-javascript.md)   
 [Length (propiedad, Array)](../../javascript/reference/length-property-array-javascript.md)   
 [length (Propiedad, String)](../../javascript/reference/length-property-string-javascript.md)