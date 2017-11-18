---
title: "slice (método, String) (JavaScript) | Documentos de Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: slice
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- strings [Visual Studio], returning characters
- slice method
ms.assetid: 80cd77a6-3718-492e-8e96-f909d8721d91
caps.latest.revision: "16"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1baa0a05a2d6aa8c06cc962761c8e557632d034c
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="slice-method-string-javascript"></a>slice (Método, String de JavaScript)
Devuelve una sección de una cadena.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
stringObj.slice(start, [end])   
```  
  
## <a name="parameters"></a>Parámetros  
 `stringObj`  
 Obligatorio. Objeto `String` o literal de cadena.  
  
 `start`  
 Obligatorio. El índice hasta el principio de la parte especificada de `stringObj`.  
  
 `end`  
 Opcional. El índice hasta el final de la parte especificada de `stringObj`. La subcadena incluye los caracteres hasta, pero sin incluir, el carácter indicado por `end`. Si no se especifica este valor, la subcadena continúa hasta el final de `stringObj`.  
  
## <a name="remarks"></a>Comentarios  
 El `slice` método devuelve un `String` objeto que contiene la parte especificada de `stringObj`.  
  
 El `slice` método copia de seguridad, pero sin incluir el carácter indicado por `end`.  
  
 Si `start` es negativo, se trata como *longitud*  +  `start` donde *longitud* es la longitud de la cadena. Si `end` es negativo, se trata como *longitud* + `end`. Si `end` es copiar se omite, continúa hasta el final de `stringObj`. Si `end` se produce antes de `start`, ningún carácter se copia en la nueva cadena.  
  
## <a name="example"></a>Ejemplo  
 En el primer ejemplo, el `slice` método devuelve la cadena completa. En el segundo ejemplo, el `slice` método devuelve toda la cadena, excepto el último carácter.  
  
```JavaScript  
var str1 = "all good boys do fine";  
  
var slice1 = str1.slice(0);  
var slice2 = str1.slice(0,-1);  
var slice3 = str1.slice(4);  
var slice4 = str1.slice(4, 8);  
  
document.write(slice1 + "<br/>");  
document.write(slice2 + "<br/>");  
document.write(slice3 + "<br/>");  
document.write(slice4);  
  
// Output:  
// all good boys do fine  
// all good boys do fin  
// good boys do fine  
// good  
  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **Se aplica a**: [objeto de cadena](../../javascript/reference/string-object-javascript.md)  
  
## <a name="see-also"></a>Vea también  
 [slice (Método, Array)](../../javascript/reference/slice-method-array-javascript.md)