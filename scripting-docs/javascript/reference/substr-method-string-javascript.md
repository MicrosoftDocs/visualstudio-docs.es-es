---
title: "substr (método, String) (JavaScript) | Documentos de Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: substr
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords: substr method
ms.assetid: f12541c1-2623-482e-941d-2e22bc3c4a4a
caps.latest.revision: "15"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6b002bfefbeb81c534c882fa4a4720c93ccca185
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="substr-method-string-javascript"></a>substr (Método, String de JavaScript)
Obtiene una subcadena empezando por la ubicación especificada y con la longitud especificada.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
stringvar.substr(start [, length ])   
```  
  
## <a name="parameters"></a>Parámetros  
 `stringvar`  
 Obligatorio. Un literal de cadena o `String` del objeto de la que se extrae la subcadena.  
  
 `start`  
 Obligatorio. La posición inicial de la subcadena deseada. El índice del primer carácter de la cadena es cero.  
  
 `length`  
 Opcional. El número de caracteres que se va a incluir en la subcadena devuelta.  
  
## <a name="remarks"></a>Comentarios  
 Si `length` es cero o negativo, se devuelve una cadena vacía. Si no se especifica, la subcadena continúa hasta el final de `stringvar`.  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra el uso del método `substr`.  
  
```JavaScript  
var s = "The quick brown fox jumps over the lazy dog.";  
var ss = s.substr(10, 5);    
document.write("[" + ss + "] <br>");  
  
ss = s.substr(10);  
document.write("[" + ss + "] <br>");  
  
ss = s.substr(10, -5);  
document.write("[" + ss + "] <br>");  
  
// Output:  
// [brown]   
// [brown fox jumps over the lazy dog.]   
// []  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **Se aplica a**: [objeto de cadena](../../javascript/reference/string-object-javascript.md)  
  
## <a name="see-also"></a>Vea también  
 [substring (Método, String)](../../javascript/reference/substring-method-string-javascript.md)