---
title: Se esperaba &#39;]&#39; en la expresión regular (JavaScript) | Microsoft Docs
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
- VS.WebClient.Help.SCRIPT5019
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 1ca2079a-44dd-479f-a1e3-e04a14d0739e
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 64ef929ba309f0b496e72f3cf740daf6970d08fb
ms.sourcegitcommit: 1ab675a872848c81a44d6b4bd3a49958fe673c56
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/10/2018
ms.locfileid: "44283722"
---
# <a name="expected-3939-in-regular-expression-javascript"></a>Se esperaba &#39;]&#39; en la expresión regular (JavaScript)
Se ha intentado crear una clase de caracteres para una coincidencia de expresión regular, pero no incluía el corchete de cierre. Combinaciones de caracteres literales individuales se pueden ensamblar en clases de caracteres mediante la colocación de corchetes. Una clase de caracteres coincide con cualquier carácter que contiene. Por ejemplo, / [abc] / coincide con cualquiera de las letras "a", "b" o "c".  
  
### <a name="to-correct-this-error"></a>Para corregir este error  
  
-   Agregue el corchete de cierre a la expresión regular.  
  
    > [!NOTE]
    >  Si quiere hacer coincidir con un solo corchete, un carácter de escape con una barra diagonal inversa - \\[, de modo que no se interpreta como un carácter especial por [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)].  
  
## <a name="see-also"></a>Vea también  
 [Objeto de expresión regular](../../javascript/reference/regular-expression-object-javascript.md)   
 [Sintaxis de expresión regular (JavaScript)](https://msdn.microsoft.com/library/1400241x)