---
title: Cuantificador inesperado (JavaScript) | Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: reference
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
ms.openlocfilehash: 52b98875b560e4863a93849cf99c2f8756cd438a
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "63005896"
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
|{n,}|n o más repeticiones|  
|{n,m}|De n a m repeticiones, ambos inclusivas|  
  
### <a name="to-correct-this-error"></a>Para corregir este error  
  
- Asegúrese de que el elemento de modelo de búsqueda contiene solo los factores de repetición legal.  
  
## <a name="see-also"></a>Vea también  
 [Objeto de expresión regular](../../javascript/reference/regular-expression-object-javascript.md)   
 [Sintaxis de expresión regular (JavaScript)](https://msdn.microsoft.com/library/1400241x)