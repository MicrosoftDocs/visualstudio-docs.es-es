---
title: Se esperaba ' Catch ' | Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: error-reference
f1_keywords:
- VS.WebClient.Help.SCRIPT1033
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: f1cd947f-eba2-411e-8e84-8ca86f608643
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1d9950573e7bbeefe3594d77df2ae41c12f77ed3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "85816690"
---
# <a name="expected-catch"></a>Se esperaba 'catch'
Usó el bloque **try** del control de excepciones, pero no escribió la instrucción **catch** asociada. El mecanismo de control de excepciones requiere que el código que puede producir un error, junto con el código que no debe ejecutarse si se produce una excepción, se ajuste dentro de un bloque **try** . Las excepciones se producen en el bloque **try** mediante la instrucción **Throw** y se detectan fuera del bloque **try** con una o más instrucciones **catch** .  
  
### <a name="to-correct-this-error"></a>Para corregir este error  
  
- Agregue el bloque **catch** asociado.  
  
- Pruebe a usar un bloque **Finally** en lugar de un bloque **catch** .  
  
## <a name="see-also"></a>Vea también  
 [try... detectar... Finally (instrucción)](../../javascript/reference/try-dot-dot-dot-catch-dot-dot-dot-finally-statement-javascript.md)   
 [Error (objeto)](../../javascript/reference/error-object-javascript.md)