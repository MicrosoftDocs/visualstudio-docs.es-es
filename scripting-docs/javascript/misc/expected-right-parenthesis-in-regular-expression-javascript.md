---
title: "Se esperaba &#39;) &#39; en la expresión regular (JavaScript) | Documentos de Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology:
- javascript
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VS.WebClient.Help.SCRIPT5020
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 2087ba1d-9783-4d40-b609-e8542f579f7f
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ca4560c638cc0e9209141ba9b0878208eb84eb0c
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="expected-3939-in-regular-expression-javascript"></a>Se esperaba &#39;) &#39; en la expresión regular (JavaScript)
Se intentó crear una captura de la expresión regular, la aserción o el grupo, pero no incluía el paréntesis de cierre. Paréntesis tienen varias finalidades en expresiones regulares. En primer lugar, se utilizan para capturar subexpresiones, para especificar las aserciones, o para agrupar patrones de modo que los elementos se pueden tratar como una sola unidad por *, +,?, y así sucesivamente.  
  
### <a name="to-correct-this-error"></a>Para corregir este error  
  
-   Agregue el paréntesis de cierre situado.  
  
    > [!NOTE]
    >  Si desea asociar un paréntesis único, escape con una barra diagonal inversa - \\(: para que no se interpreta como un carácter especial forma [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)].  
  
## <a name="see-also"></a>Vea también  
 [Regular Expression (objeto)](../../javascript/reference/regular-expression-object-javascript.md)   
 [Sintaxis de expresión regular (JavaScript)](http://msdn.microsoft.com/en-us/ab0766e1-7037-45ed-aa23-706f58358c0e)