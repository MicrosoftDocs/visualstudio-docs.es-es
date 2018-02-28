---
title: "Excepción producida y no detectada | Documentos de Microsoft"
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
- VS.WebClient.Help.SCRIPT5022
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: b5235490-a8e7-42e3-804e-d85235bc6f05
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 839ff08da4d26406b508a206c809b0813d2b32e1
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="exception-thrown-and-not-caught"></a>Excepción producida y no detectada
Se incluye un `throw` instrucción en el código, pero no se incluyera en un **intente** bloque, o se produjo asociado ya no **catch** bloque para capturar el error. Las excepciones se inician desde el **intente** bloquee mediante el **throw** instrucción y capturadas fuera de la **intente** bloque con un **detectar** instrucción.  
  
### <a name="to-correct-this-error"></a>Para corregir este error  
  
-   Coloque el código que puede producir una excepción en un **intente** bloquear y asegúrese de que hay un correspondiente **catch** bloque.  
  
-   Asegúrese de que la instrucción catch espera un formato correcto de excepción.  
  
-   Si se vuelve a producir la excepción, asegúrese de que hay otra instrucción catch correspondiente.  
  
## <a name="see-also"></a>Vea también  
 [Objeto de error](../../javascript/reference/error-object-javascript.md)   
 [throw (instrucción)](../../javascript/reference/throw-statement-javascript.md)   
 [Try...Catch...Finally (Instrucción)](../../javascript/reference/try-dot-dot-dot-catch-dot-dot-dot-finally-statement-javascript.md)