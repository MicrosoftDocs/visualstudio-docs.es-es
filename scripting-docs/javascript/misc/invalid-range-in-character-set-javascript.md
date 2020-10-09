---
title: Intervalo no válido en el juego de caracteres (JavaScript) | Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: error-reference
f1_keywords:
- VS.WebClient.Help.SCRIPT5021
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 971e9d5a-f88a-47a8-af94-f3c7c4aed5ab
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 12624d1a0256360ef1e4538a14100923c7de8af8
ms.sourcegitcommit: e38419bb842d587fd9e37c24b6cf3fc5c2e74817
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/09/2020
ms.locfileid: "91862579"
---
# <a name="invalid-range-in-character-set-javascript"></a>Intervalo no válido en el juego de caracteres (JavaScript)
Ha intentado crear una expresión regular con un intervalo de juego de caracteres no válido. Los juegos de caracteres deben abarcar solo caracteres individuales, como a-z o 0-9; no se pueden incluir clases de caracteres como \w en un juego de caracteres. El primer carácter del intervalo también debe ir delante del segundo carácter del intervalo. Por ejemplo:  
  
```JavaScript  
var good = /[a-z]/;     // A valid character range - a comes before z.  
var notGood = /[z-a]/;  // An invalid character range - z does not come before a.  
```  
  
### <a name="to-correct-this-error"></a>Para corregir este error  
  
- Use solo caracteres individuales para crear el juego de caracteres de la expresión regular y asegúrese de que están en el orden correcto.  
  
## <a name="see-also"></a>Vea también  
 [Objeto de expresión regular](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/RegExp)   
 [Sintaxis de expresiones regulares (JavaScript)](/previous-versions/1400241x(v=vs.100))