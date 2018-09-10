---
title: Intervalo no válido en el carácter establecido (JavaScript) | Microsoft Docs
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
- VS.WebClient.Help.SCRIPT5021
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 971e9d5a-f88a-47a8-af94-f3c7c4aed5ab
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e4cc8feb9a33c2995e592f8031beb2e03605891d
ms.sourcegitcommit: 1ab675a872848c81a44d6b4bd3a49958fe673c56
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/10/2018
ms.locfileid: "44282825"
---
# <a name="invalid-range-in-character-set-javascript"></a>Intervalo no válido en el juego de caracteres (JavaScript)
Se intentó crear una expresión regular con un intervalo de conjunto de caracteres no válidos. Juegos de caracteres deben oscilar entre caracteres individuales, como a-z o 0-9; no se incluyen las clases de caracteres como \w en un juego de caracteres. El primer carácter del intervalo también debe ir delante del segundo carácter del intervalo. Por ejemplo:  
  
```JavaScript  
var good = /[a-z]/;     // A valid character range - a comes before z.  
var notGood = /[z-a]/;  // An invalid character range - z does not come before a.  
```  
  
### <a name="to-correct-this-error"></a>Para corregir este error  
  
-   Use caracteres único solo para componer el juego de caracteres de expresión regular y asegúrese de que se encuentran en el orden correcto.  
  
## <a name="see-also"></a>Vea también  
 [Objeto de expresión regular](../../javascript/reference/regular-expression-object-javascript.md)   
 [Sintaxis de expresión regular (JavaScript)](https://msdn.microsoft.com/library/1400241x)