---
title: Se esperaba 'catch' | Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: reference
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
ms.openlocfilehash: 941d49a530b14e2af64ddcb599dd775feb347de0
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62935404"
---
# <a name="expected-catch"></a>Se esperaba 'catch'
Usar el control de excepciones **intente** bloquea, pero no ha escrito asociado **catch** instrucción. El mecanismo de control de excepciones requiere que el código que puede producir un error, junto con el código que no se debe ejecutar si se produce una excepción, se ajusta dentro de un **intente** bloque. Excepciones desde el **intente** bloquear mediante la **throw** instrucción y capturadas fuera el **intente** bloque con uno o varios **catch**instrucciones.  
  
### <a name="to-correct-this-error"></a>Para corregir este error  
  
- Agregar asociado **catch** bloque.  
  
- Pruebe a usar un **finalmente** bloquear en lugar de un **catch** bloque.  
  
## <a name="see-also"></a>Vea también  
 [try... catch... finally (instrucción)](../../javascript/reference/try-dot-dot-dot-catch-dot-dot-dot-finally-statement-javascript.md)   
 [Error (Objeto)](../../javascript/reference/error-object-javascript.md)