---
title: Se esperaba '] ' en la expresión regular (JavaScript) | Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: error-reference
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
ms.openlocfilehash: 31d1ebd30ba5e793a1c52c00d8b58603bdaa9a75
ms.sourcegitcommit: e38419bb842d587fd9e37c24b6cf3fc5c2e74817
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/09/2020
ms.locfileid: "91862329"
---
# <a name="expected--in-regular-expression-javascript"></a>Se esperaba ']' en la expresión regular (JavaScript)
Se intentó crear una clase de caracteres para una coincidencia de expresión regular, pero no se incluía el corchete de cierre. Las combinaciones de caracteres literales individuales se pueden ensamblar en clases de caracteres colocándolas entre corchetes. Una clase de caracteres coincide con cualquier carácter que contenga. Por ejemplo,/[ABC]/coincide con cualquiera de las letras "a", "b" o "c".  
  
### <a name="to-correct-this-error"></a>Para corregir este error  
  
- Agregue el corchete de cierre a la expresión regular.  
  
    > [!NOTE]
    > Si desea buscar coincidencias con un solo corchete, haga una marca de escape con una barra diagonal inversa (), de \\ modo que no se interprete como un carácter especial [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] .  
  
## <a name="see-also"></a>Vea también  
 [Objeto de expresión regular](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/RegExp)   
 [Sintaxis de expresiones regulares (JavaScript)](/previous-versions/1400241x(v=vs.100))