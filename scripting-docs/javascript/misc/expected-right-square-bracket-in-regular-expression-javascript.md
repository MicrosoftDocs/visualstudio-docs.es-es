---
title: "Se esperaba &#39;] &#39; en la expresión regular (JavaScript) | Documentos de Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: javascript
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: VS.WebClient.Help.SCRIPT5019
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 1ca2079a-44dd-479f-a1e3-e04a14d0739e
caps.latest.revision: "7"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 4c59dcbeea91a1bc01e870d0a49fd22cace6562d
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="expected-3939-in-regular-expression-javascript"></a>Se esperaba &#39;] &#39; en la expresión regular (JavaScript)
Se intentó crear una clase de caracteres para una coincidencia de expresión regular, pero no incluía el corchete de cierre. Combinaciones de caracteres literales individuales pueden montarse en clases de caracteres mediante la colocación de corchetes. Una clase de caracteres coincide con cualquier carácter que contiene. Por ejemplo, / [abc] / coincide con cualquiera de las letras "a", "b" o "c".  
  
### <a name="to-correct-this-error"></a>Para corregir este error  
  
-   Agregue el corchete de cierre a la expresión regular.  
  
    > [!NOTE]
    >  Si quiere hacer coincidir con un solo corchete, escape con una barra diagonal inversa - \\[, de modo que no se interpreta como un carácter especial forma [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)].  
  
## <a name="see-also"></a>Vea también  
 [Regular Expression (objeto)](../../javascript/reference/regular-expression-object-javascript.md)   
 [Sintaxis de expresión regular (JavaScript)](http://msdn.microsoft.com/en-us/ab0766e1-7037-45ed-aa23-706f58358c0e)