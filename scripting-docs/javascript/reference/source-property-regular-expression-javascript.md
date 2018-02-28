---
title: "Source (propiedad) (expresión Regular) (JavaScript) | Documentos de Microsoft"
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
- source
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- Source property
ms.assetid: d58ac57e-fcde-49d1-bbba-e8c4218448c4
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 05bf118aec0f31de11a3df6f4b875fad3092e53d
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="source-property-regular-expression-javascript"></a>source (Propiedad, Regular Expression de JavaScript)
Devuelve una copia del texto del patrón de expresión regular. Sólo lectura. El `rgExp` argumento es un **expresión Regular** objeto. Puede ser un nombre de variable o un literal.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
rgExp.source  
```  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se muestra el uso de la **origen** propiedad:  
  
```JavaScript  
function SourceDemo(re, s){  
   var s1;  
   // Test string for existence of regular expression.  
   if (re.test(s))  
      s1 = " contains ";  
   else  
      s1 = " does not contain ";  
   // Get the text of the regular expression itself.  
   return(s + s1 + re.source);  
}  
```  
  
## <a name="requirements"></a>Requisitos  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **Se aplica a**: [Regular Expression (objeto)](../../javascript/reference/regular-expression-object-javascript.md)  
  
## <a name="see-also"></a>Vea también  
 [Regular Expression (objeto)](../../javascript/reference/regular-expression-object-javascript.md)   
 [Regular Expression (objeto)](../../javascript/reference/regular-expression-object-javascript.md)   
 [Sintaxis de expresión regular (JavaScript)](http://msdn.microsoft.com/en-us/ab0766e1-7037-45ed-aa23-706f58358c0e)