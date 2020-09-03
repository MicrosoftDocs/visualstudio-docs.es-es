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
ms.openlocfilehash: da4ff08ae667b868670364c7ad6b9a6b69ae6ad3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "85815336"
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
 [Objeto de expresión regular](../../javascript/reference/regular-expression-object-javascript.md)   
 [Sintaxis de expresiones regulares (JavaScript)](https://msdn.microsoft.com/library/1400241x)