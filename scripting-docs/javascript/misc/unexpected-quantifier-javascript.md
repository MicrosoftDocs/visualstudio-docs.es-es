---
title: Cuantificador inesperado (JavaScript) | Microsoft Docs
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
ms.openlocfilehash: 693fdf4091a6f6fdf63c701b63c4355a67ee6fbd
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/08/2019
ms.locfileid: "54096751"
---
# <a name="unexpected-quantifier-javascript"></a>No se esperaba un cuantificador (JavaScript)
Al redactar su patrón de búsqueda de expresión regular, crea un elemento de modelo con un factor de repetición no válido. Por ejemplo, el patrón  
  
```js
/^+/  
```  
  
 no es válido porque el elemento ^ (principio de la entrada) no puede tener un factor de repetición. En la tabla siguiente se enumera los elementos que no tienen factores de repetición.  
  
|Elemento|Descripción|  
|-------------|-----------------|  
|^|Principio de la entrada|  
|$|Final de la entrada|  
|\b|Límite de palabra|  
|\B|Límite de palabras que no son|  
|*|Cero o más repeticiones|  
|+|Uno o más repeticiones|  
|?|Cero o una de las repeticiones|  
|{n}|n repeticiones|  
|{n}|n o más repeticiones|  
|{n, m}|De n a m repeticiones, ambos inclusivas|  
  
### <a name="to-correct-this-error"></a>Para corregir este error  
  
-   Asegúrese de que el elemento de modelo de búsqueda contiene solo los factores de repetición legal.  
  
## <a name="see-also"></a>Vea también  
 [Objeto de expresión regular](../../javascript/reference/regular-expression-object-javascript.md)   
 [Sintaxis de expresión regular (JavaScript)](https://msdn.microsoft.com/library/1400241x)