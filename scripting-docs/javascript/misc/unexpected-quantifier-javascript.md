---
description: Al redactar el patrón de búsqueda de expresiones regulares, se creó un elemento de patrón con un factor de repetición no válido.
title: Cuantificador inesperado (JavaScript) | Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: error-reference
f1_keywords:
- VS.WebClient.Help.SCRIPT5018
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: ba6d34f9-2d6f-486c-a929-6cd9818be322
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9351f9306cea9e3f6346b007d6fe05c1d7bbf319
ms.sourcegitcommit: 691d2a47f92f991241fdb132a82c53a537198d50
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/16/2021
ms.locfileid: "103571966"
---
# <a name="unexpected-quantifier-javascript"></a>No se esperaba un cuantificador (JavaScript)
Al redactar el patrón de búsqueda de expresiones regulares, se creó un elemento de patrón con un factor de repetición no válido. Por ejemplo, el patrón  
  
```js
/^+/  
```  
  
 no es válido porque el elemento ^ (comienzo de la entrada) no puede tener un factor de repetición. En la tabla siguiente se enumeran los elementos que no pueden tener factores de repetición.  
  
|Elemento|Descripción|  
|-------------|-----------------|  
|^|Inicio de la entrada|  
|$|Fin de la entrada|  
|\b|Límite de palabras|  
|\B|Límite sin palabras|  
|*|Cero o más repeticiones|  
|+|Una o más repeticiones|  
|?|Cero o una repetición|  
|n|n repeticiones|  
|{n,}|n o más repeticiones|  
|{n, m}|De n a m repeticiones, inclusive|  
  
### <a name="to-correct-this-error"></a>Para corregir este error  
  
- Asegúrese de que el elemento de patrón de búsqueda solo contiene factores de repetición legales.  
  
## <a name="see-also"></a>Consulte también  
 [Objeto de expresión regular](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/RegExp)   
 [Sintaxis de expresiones regulares (JavaScript)](/previous-versions/1400241x(v=vs.100))
