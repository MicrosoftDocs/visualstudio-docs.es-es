---
title: Propiedad lastMatch ($&amp;) (RegExp) (JavaScript) | Documentos de Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: $&
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- lastMatch property ($%)
- lastMatch property ($&)
ms.assetid: d223836d-5235-48a5-a926-d20764ad3f14
caps.latest.revision: "12"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 25991bf5b577d785fc4f7d8c6b2af14b93486000
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="lastmatch-property-amp-regexp-javascript"></a>Propiedad lastMatch ($&amp;) (RegExp) (JavaScript)
Devuelve el último carácter coincidente de una búsqueda de expresión regular. Sólo lectura.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
RegExp.lastMatch  
```  
  
## <a name="remarks"></a>Comentarios  
 El objeto asociado a esta propiedad siempre es global `RegExp` objeto.  
  
 El valor inicial de la `lastMatch` propiedad es una cadena vacía. El valor de la `lastMatch` propiedad cambia cada vez que se realiza una coincidencia correcta.  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra el uso de la propiedad `lastMatch`.  
  
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
 [lastParen ($ +) (RegExp) de la propiedad](../../javascript/reference/lastparen-property-dollar-regexp-javascript.md)   
 [Propiedad leftContext ($') (RegExp)](../../javascript/reference/leftcontext-property-dollar-grave-regexp-javascript.md)   
 [rightContext (Propiedad) ($') (RegExp)](../../javascript/reference/rightcontext-property-dollar-regexp-javascript.md)