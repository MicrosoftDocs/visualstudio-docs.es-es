---
title: Se esperaba ']' en la expresión regular (JavaScript) | Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: reference
f1_keywords:
- VS.WebClient.Help.SCRIPT5019
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 1ca2079a-44dd-479f-a1e3-e04a14d0739e
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 66fa8ba2396185bd402e4bc31a3da6b1f8bf95ab
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "63446490"
---
# <a name="expected--in-regular-expression-javascript"></a>Se esperaba ']' en la expresión regular (JavaScript)
Se ha intentado crear una clase de caracteres para una coincidencia de expresión regular, pero no incluía el corchete de cierre. Combinaciones de caracteres literales individuales se pueden ensamblar en clases de caracteres mediante la colocación de corchetes. Una clase de caracteres coincide con cualquier carácter que contiene. Por ejemplo, / [abc] / coincide con cualquiera de las letras "a", "b" o "c".  
  
### <a name="to-correct-this-error"></a>Para corregir este error  
  
- Agregue el corchete de cierre a la expresión regular.  
  
    > [!NOTE]
    > Si quiere hacer coincidir con un solo corchete, un carácter de escape con una barra diagonal inversa - \\[, de modo que no se interpreta como un carácter especial por [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)].  
  
## <a name="see-also"></a>Vea también  
 [Objeto de expresión regular](../../javascript/reference/regular-expression-object-javascript.md)   
 [Sintaxis de expresión regular (JavaScript)](https://msdn.microsoft.com/library/1400241x)