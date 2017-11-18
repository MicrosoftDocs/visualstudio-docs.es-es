---
title: RegExp (objeto) (JavaScript) | Documentos de Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: RegExp
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- RegExp object, overview
- RegExp object
ms.assetid: 7f6b1073-8cbb-49ed-94b6-56833ba663c5
caps.latest.revision: "12"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b7319e4556721bcfd397061ce525acfb3278c6b9
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="regexp-object-javascript"></a>RegExp (Objeto de JavaScript)
Coincide con un objeto intrínseco global que almacena información sobre los resultados del patrón de expresión regular.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
RegExp.property   
```  
  
## <a name="remarks"></a>Comentarios  
 Requerido *propiedad* argumento puede ser cualquiera de los `RegExp` propiedades del objeto.  
  
 La `RegExp` objeto no se puede crear directamente, pero siempre está disponible para su uso. Hasta que se ha completado una búsqueda de expresión regular correcta, los valores iniciales de las diversas propiedades de la `RegExp` objeto son los siguientes:  
  
|Propiedad|Forma abreviada|Valor inicial|  
|--------------|---------------|-------------------|  
|índice||-1|  
|entrada|$_|Cadena vacía.|  
|lastIndex)||-1|  
|lastMatch|$&|Cadena vacía.|  
|lastParen|$+|Cadena vacía.|  
|leftContext|$`|Cadena vacía.|  
|rightContext|$'|Cadena vacía.|  
|$1 - $9|$1 - $9|Cadena vacía.|  
  
 Sus propiedades tienen sin definir como su valor hasta que se ha completado una búsqueda de expresión regular correcta.  
  
 Global `RegExp` objeto no debe confundirse con el **expresión Regular** objeto. Aunque parecen ser lo mismo, son independientes y distintos. Las propiedades de la información global `RegExp` objeto contienen información continuamente actualizada sobre cada coincidencia que tiene lugar, mientras que las propiedades de la **expresión Regular** objeto sólo contienen información sobre las coincidencias que se producen con esa instancia de la **expresión Regular**.  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se realiza una búsqueda de expresión regular. Muestra coincidencias y submatches desde global `RegExp` objeto y de la matriz devuelta por la `exec` método.  
  
<CodeContentPlaceHolder>1</CodeContentPlaceHolder>  
<a name="js56jsobjregexpprop"></a>   
## <a name="properties"></a>Propiedades  
 [$1... $9 propiedades](../../javascript/reference/dollar-1-dot-dot-dot-dollar-9-properties-regexp-javascript.md) &#124; [index (propiedad)](../../javascript/reference/index-property-regexp-javascript.md) &#124; [input (propiedad)](../../javascript/reference/input-property-dollar-regexp-javascript.md) &#124; [lastIndex (propiedad)](../../javascript/reference/lastindex-property-regexp-javascript.md) &#124; [propiedad lastMatch](../../javascript/reference/lastmatch-property-dollar-regexp-javascript.md) &#124; [propiedad lastParen](../../javascript/reference/lastparen-property-dollar-regexp-javascript.md) &#124; [leftContext (propiedad)](../../javascript/reference/leftcontext-property-dollar-grave-regexp-javascript.md) &#124; [propiedad rightContext](../../javascript/reference/rightcontext-property-dollar-regexp-javascript.md)  
  
## <a name="methods"></a>Métodos  
 La `RegExp` objeto no tiene métodos.  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
## <a name="see-also"></a>Vea también  
 [Regular Expression (objeto)](../../javascript/reference/regular-expression-object-javascript.md)   
 [Sintaxis de expresión regular (JavaScript)](http://msdn.microsoft.com/en-us/ab0766e1-7037-45ed-aa23-706f58358c0e)   
 [String (Objeto)](../../javascript/reference/string-object-javascript.md)