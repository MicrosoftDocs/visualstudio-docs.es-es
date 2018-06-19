---
title: Propiedad leftContext ($') (RegExp) (JavaScript) | Documentos de Microsoft
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
- $`
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- leftContext property ($`)
ms.assetid: 840e56c0-eb7c-461f-bb56-91acff9b5bcf
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b0234a547d2e26c6cf6b1d1a058a46135e577fdd
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
ms.locfileid: "24637805"
---
# <a name="leftcontext-property--regexp-javascript"></a>leftContext (Propiedad) ($`) (RegExp) (JavaScript)
Devuelve los caracteres desde el principio de una cadena de búsqueda hasta la posición antes del comienzo de la última coincidencia. Sólo lectura.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
RegExp.leftContext  
```  
  
## <a name="remarks"></a>Comentarios  
 El objeto asociado a esta propiedad siempre es global `RegExp` objeto.  
  
 El valor inicial de la `leftContext` propiedad es una cadena vacía. El valor de la `leftContext` propiedad cambia cada vez que se realiza una coincidencia correcta.  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra el uso de la propiedad `leftContext`.  
  
```JavaScript  
// Create the regular expression pattern.  
var re = new RegExp("d(b+)(d)","ig");  
var str = "cdbBdbsbdbdz";  
  
// Perform the search.  
var arr = re.exec(str);  
  
// Print the output.  
var s = ""   
s += "$1: " + RegExp.$1 + "<br />";  
s += "$2: " + RegExp.$2 + "<br />";  
s += "$3: " + RegExp.$3 + "<br />";  
s += "input: " + RegExp.input + "<br />";  
s += "lastMatch: " + RegExp.lastMatch + "<br />";  
s += "leftContext: " + RegExp.leftContext + "<br />";  
s += "rightContext: " + RegExp.rightContext + "<br />";   
s += "lastParen: " + RegExp.lastParen + "<br />";  
  
document.write(s);  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
 **Se aplica a**: [RegExp (objeto)](../../javascript/reference/regexp-object-javascript.md)  
  
## <a name="see-also"></a>Vea también  
 [$1... $9 (propiedades, RegExp)](../../javascript/reference/dollar-1-dot-dot-dot-dollar-9-properties-regexp-javascript.md)   
 [Index (propiedad) (RegExp)](../../javascript/reference/index-property-regexp-javascript.md)   
 [Input (propiedad) ($_) (RegExp)](../../javascript/reference/input-property-dollar-regexp-javascript.md)   
 [lastIndex (propiedad) (RegExp)](../../javascript/reference/lastindex-property-regexp-javascript.md)   
 [Propiedad lastMatch ($&) (RegExp)](../../javascript/reference/lastmatch-property-dollar-regexp-javascript.md)   
 [lastParen ($ +) (RegExp) de la propiedad](../../javascript/reference/lastparen-property-dollar-regexp-javascript.md)   
 [rightContext (Propiedad) ($') (RegExp)](../../javascript/reference/rightcontext-property-dollar-regexp-javascript.md)