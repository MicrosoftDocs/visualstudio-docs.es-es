---
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
ms.openlocfilehash: f67f9a2fc81b0bd950e171e4274eb09eacd88bbc
ms.sourcegitcommit: e38419bb842d587fd9e37c24b6cf3fc5c2e74817
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/09/2020
ms.locfileid: "91861857"
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
  
## <a name="see-also"></a>Vea también  
 [Objeto de expresión regular](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/RegExp)   
 [Sintaxis de expresiones regulares (JavaScript)](/previous-versions/1400241x(v=vs.100))