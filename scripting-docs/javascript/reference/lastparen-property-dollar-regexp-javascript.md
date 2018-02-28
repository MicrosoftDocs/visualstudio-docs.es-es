---
title: lastParen ($ +) (RegExp) (JavaScript) de la propiedad | Documentos de Microsoft
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
- $+
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- lastParen property ($+)
ms.assetid: 18aca591-a97a-48da-8b06-422346804b16
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 059cfc6556873d770798eff59bf7415426526626
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="lastparen-property--regexp-javascript"></a>lastParen (Propiedad) ($+) (RegExp) (JavaScript)
Devuelve la última subcoincidencia entre paréntesis de una búsqueda de expresión regular, si existe. Sólo lectura.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
RegExp.lastParen  
```  
  
## <a name="remarks"></a>Comentarios  
 El objeto asociado a esta propiedad siempre es global `RegExp` objeto.  
  
 El valor inicial de la `lastParen` propiedad es una cadena vacía. El valor de la `lastParen` propiedad cambia cada vez que se realiza una coincidencia correcta.  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra el uso de la propiedad `lastParen`.  
  
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
 [Propiedad leftContext ($') (RegExp)](../../javascript/reference/leftcontext-property-dollar-grave-regexp-javascript.md)   
 [rightContext (Propiedad) ($') (RegExp)](../../javascript/reference/rightcontext-property-dollar-regexp-javascript.md)