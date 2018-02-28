---
title: "Split (método) (cadena) (JavaScript) | Documentos de Microsoft"
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
- split
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- split method
ms.assetid: 7f093336-c887-4efb-b91f-819b6d18a181
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: eea90dda2e8e4d52451af247d139eeee44f83917
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="split-method-string-javascript"></a>split (Método, String de JavaScript)
Divide una cadena en subcadenas mediante el separador especificado y las devuelve como una matriz.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
stringObj.split([separator[, limit]])  
```  
  
## <a name="parameters"></a>Parámetros  
 `stringObj`  
 Obligatorio. Objeto `String` o literal de cadena que se va a dividir. Este objeto no es modificado por la **dividir** método.  
  
 `separator`  
 Opcional. Una cadena o un **expresión Regular** objeto que identifica uno o varios caracteres que se va a usar para separar la cadena. Si se omite, se devuelve una matriz de un único elemento que contiene toda la cadena.  
  
 `limit`  
 Opcional. Valor utilizado para limitar el número de elementos devueltos en la matriz.  
  
## <a name="return-value"></a>Valor devuelto  
 El resultado de la **dividir** método es una matriz de cadenas dividida en cada punto donde `separator` se produce en `stringObj`. El argumento `separator` no se devuelve como parte de ningún elemento de la matriz.  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra el uso de la **dividir** método.  
  
```JavaScript  
var s = "The quick brown fox jumps over the lazy dog.";  
var ss = s.split(" ");  
for (var i in ss) {  
    document.write(ss[i]);  
    document.write("<br/>");  
}  
  
// Output:   
// The  
// quick  
// brown  
// fox  
// jumps  
// over  
// the  
// lazy  
// dog.  
  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **Se aplica a**: [objeto de cadena](../../javascript/reference/string-object-javascript.md)  
  
## <a name="see-also"></a>Vea también  
 [concat (método, String)](../../javascript/reference/concat-method-string-javascript.md)   
 [RegExp (objeto)](../../javascript/reference/regexp-object-javascript.md)   
 [Regular Expression (objeto)](../../javascript/reference/regular-expression-object-javascript.md)   
 [Sintaxis de expresión regular (JavaScript)](http://msdn.microsoft.com/en-us/ab0766e1-7037-45ed-aa23-706f58358c0e)   
 [Aplicación de ejemplo de desplazamiento, panorámica y zoom](http://code.msdn.microsoft.com/ie/Scrolling-panning-and-6834aaf9)