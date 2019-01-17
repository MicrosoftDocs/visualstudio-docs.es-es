---
title: Se esperaba 'catch' | Microsoft Docs
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
- VS.WebClient.Help.SCRIPT1033
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: f1cd947f-eba2-411e-8e84-8ca86f608643
caps.latest.revision: 6
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 244635605abafc5c0bd22c5203b105aa6e7dc669
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/16/2019
ms.locfileid: "54344114"
---
# <a name="expected-catch"></a>Se esperaba 'catch'
Usar el control de excepciones **intente** bloquea, pero no ha escrito asociado **catch** instrucción. El mecanismo de control de excepciones requiere que el código que puede producir un error, junto con el código que no se debe ejecutar si se produce una excepción, se ajusta dentro de un **intente** bloque. Excepciones desde el **intente** bloquear mediante la **throw** instrucción y capturadas fuera el **intente** bloque con uno o varios **catch**instrucciones.  
  
### <a name="to-correct-this-error"></a>Para corregir este error  
  
-   Agregar asociado **catch** bloque.  
  
-   Pruebe a usar un **finalmente** bloquear en lugar de un **catch** bloque.  
  
## <a name="see-also"></a>Vea también  
 [try... catch... finally (instrucción)](../../javascript/reference/try-dot-dot-dot-catch-dot-dot-dot-finally-statement-javascript.md)   
 [Error (Objeto)](../../javascript/reference/error-object-javascript.md)