---
title: Se esperaba '] ' en la expresión regular (JavaScript) | Microsoft Docs
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
ms.openlocfilehash: 9af38a5fa754a811416f1a998b90946345f3e4a2
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/18/2019
ms.locfileid: "72576488"
---
# <a name="expected--in-regular-expression-javascript"></a>Se esperaba ']' en la expresión regular (JavaScript)
Se intentó crear una clase de caracteres para una coincidencia de expresión regular, pero no se incluía el corchete de cierre. Las combinaciones de caracteres literales individuales se pueden ensamblar en clases de caracteres colocándolas entre corchetes. Una clase de caracteres coincide con cualquier carácter que contenga. Por ejemplo,/[ABC]/coincide con cualquiera de las letras "a", "b" o "c".  
  
### <a name="to-correct-this-error"></a>Para corregir este error  
  
- Agregue el corchete de cierre a la expresión regular.  
  
    > [!NOTE]
    > Si desea buscar una coincidencia con un solo corchete, haga una escape con una barra diagonal inversa \\ [-por lo que no se interpreta como un carácter especial en [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)].  
  
## <a name="see-also"></a>Vea también  
 [Objeto de expresión Regular](../../javascript/reference/regular-expression-object-javascript.md)    
 [Sintaxis de expresiones regulares (JavaScript)](https://msdn.microsoft.com/library/1400241x)