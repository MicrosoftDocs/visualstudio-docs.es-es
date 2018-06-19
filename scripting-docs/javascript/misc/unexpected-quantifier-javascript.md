---
title: Cuantificador inesperado (JavaScript) | Documentos de Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.technology:
- javascript
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- VS.WebClient.Help.SCRIPT5018
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: ba6d34f9-2d6f-486c-a929-6cd9818be322
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: fb6d6d3129057c399dd7369c6f69eb7396f07ab4
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
ms.locfileid: "24633255"
---
# <a name="unexpected-quantifier-javascript"></a>No se esperaba un cuantificador (JavaScript)
Cuando se crea el patrón de búsqueda de expresión regular, se crea un elemento de modelo con un factor de repetición no válido. Por ejemplo, el patrón  
  
```  
/^+/  
```  
  
 no es válido porque el elemento ^ (principio de la entrada) no puede tener un factor de repetición. En la tabla siguiente se enumera los elementos que no tienen factores de repetición.  
  
|Elemento|Descripción|  
|-------------|-----------------|  
|^|Principio de la entrada|  
|$|Final de la entrada|  
|\b|Límite de palabras|  
|\B|Límite de palabras no|  
|*|Cero o más repeticiones|  
|+|Uno o más repeticiones|  
|?|Repeticiones de cero o uno|  
|{n}|repeticiones n|  
|{n}|n o más repeticiones|  
|{n, m}|De n a m repeticiones, ambos inclusivas|  
  
### <a name="to-correct-this-error"></a>Para corregir este error  
  
-   Asegúrese de que el elemento de modelo de búsqueda contiene solo los factores de repetición legal.  
  
## <a name="see-also"></a>Vea también  
 [Regular Expression (objeto)](../../javascript/reference/regular-expression-object-javascript.md)   
 [Sintaxis de expresión regular (JavaScript)](http://msdn.microsoft.com/en-us/ab0766e1-7037-45ed-aa23-706f58358c0e)