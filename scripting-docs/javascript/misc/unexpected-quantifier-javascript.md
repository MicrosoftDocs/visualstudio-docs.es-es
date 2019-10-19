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
ms.openlocfilehash: 2070ec6ad01eb62c6be9b6b9acfc91cba7bc863d
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572528"
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
 [Objeto de expresión Regular](../../javascript/reference/regular-expression-object-javascript.md)    
 [Sintaxis de expresiones regulares (JavaScript)](https://msdn.microsoft.com/library/1400241x)