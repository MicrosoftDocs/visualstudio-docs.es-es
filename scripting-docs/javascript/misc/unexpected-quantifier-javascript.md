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
ms.openlocfilehash: f18195f344adca16fce7403d225c42826a2af544
ms.sourcegitcommit: 23feea519c47e77b5685fec86c4bbd00d22054e3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/26/2019
ms.locfileid: "56843408"
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
  
-   Asegúrese de que el elemento de modelo de búsqueda contiene solo los factores de repetición legal.  
  
## <a name="see-also"></a>Vea también  
 [Objeto de expresión regular](../../javascript/reference/regular-expression-object-javascript.md)   
 [Sintaxis de expresión regular (JavaScript)](https://msdn.microsoft.com/library/1400241x)