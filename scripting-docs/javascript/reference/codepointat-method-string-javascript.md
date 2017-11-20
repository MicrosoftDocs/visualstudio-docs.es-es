---
title: "Método codePointAt (String) (JavaScript) | Documentos de Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 7979018f-1be3-4a13-9e8f-c84c7ed35288
caps.latest.revision: "4"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0dd5ef17db177dfb1d532bfb88d1d0d77cdb7304
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="codepointat-method-string-javascript"></a>Método codePointAt (String) (JavaScript)
Devuelve el punto de código de un carácter Unicode UTF-16.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
stringObj.codePointAt(pos);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `stringObj`  
 Obligatorio. El objeto de cadena.  
  
 `pos`  
 Obligatorio. Posición del carácter.  
  
## <a name="remarks"></a>Comentarios  
 Este método devuelve valores de punto de código, incluidos puntos de código astrales (puntos de código con más de cuatro valores hexadecimales), para todos los caracteres UTF-16.  
  
 Si `pos` es menor que cero (0) o mayor que el tamaño de la cadena, el valor devuelto es `undefined`.  
  
## <a name="example"></a>Ejemplo  
 En el siguiente ejemplo, se muestra cómo utilizar el método `codePointAt`.  
  
```JavaScript  
var cp1 = "𠮷".codePointAt(0);  
var cp2 = 'abc'.codePointAt(1);  
  
if(console && console.log) {  
    console.log(cp1);  
    console.log(cp2);}  
  
// Output:  
// 0x20BB7  
// 98   
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]
