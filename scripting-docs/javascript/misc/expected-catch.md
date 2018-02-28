---
title: Se esperaba &#39; catch &#39; | Documentos de Microsoft
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
- VS.WebClient.Help.SCRIPT1033
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: f1cd947f-eba2-411e-8e84-8ca86f608643
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e6cd1e57137d220ebcf3834070e36d8257e2dca7
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="expected-39catch39"></a>Se esperaba &#39; catch &#39;
Usar el control de excepciones **intente** bloquear, pero no ha escrito asociado **detectar** instrucción. El mecanismo de control de excepciones requiere que el código que puede producir un error, junto con el código que no se debe ejecutar si se produce una excepción, se ajusta dentro de un **intente** bloque. Las excepciones se inician desde el **intente** bloquee mediante el **throw** instrucción y capturadas fuera de la **intente** bloque con uno o varios **catch**instrucciones.  
  
### <a name="to-correct-this-error"></a>Para corregir este error  
  
-   Agregar el asociado **catch** bloque.  
  
-   Pruebe a usar un **finalmente** bloquear en lugar de un **catch** bloque.  
  
## <a name="see-also"></a>Vea también  
 [try... catch... finally (instrucción)](../../javascript/reference/try-dot-dot-dot-catch-dot-dot-dot-finally-statement-javascript.md)   
 [Error (Objeto)](../../javascript/reference/error-object-javascript.md)