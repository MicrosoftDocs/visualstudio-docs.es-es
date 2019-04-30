---
title: Excepción producida y no detectada | Documentos de Microsoft
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: reference
f1_keywords:
- VS.WebClient.Help.SCRIPT5022
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: b5235490-a8e7-42e3-804e-d85235bc6f05
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: bae4ed0a335a9c12d16cb46208f77c4b66f12547
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62946334"
---
# <a name="exception-thrown-and-not-caught"></a>Excepción producida y no detectada
Se incluye un `throw` instrucción en el código, pero no se ha delimitado por un **intente** bloque, o no se asoció no **catch** bloque para capturar el error. Excepciones desde el **intente** bloquear mediante la **throw** instrucción y capturadas fuera el **intente** bloque con un **catch** instrucción.  
  
### <a name="to-correct-this-error"></a>Para corregir este error  
  
- Coloque el código que puede producir una excepción en un **intente** bloquear y asegúrese de que hay correspondiente **catch** bloque.  
  
- Asegúrese de que la instrucción catch espera el formato correcto de la excepción.  
  
- Si se vuelve a producir la excepción, asegúrese de que hay otra instrucción catch correspondiente.  
  
## <a name="see-also"></a>Vea también  
 [Objeto de error](../../javascript/reference/error-object-javascript.md)   
 [Throw (instrucción)](../../javascript/reference/throw-statement-javascript.md)   
 [Try...Catch...Finally (Instrucción)](../../javascript/reference/try-dot-dot-dot-catch-dot-dot-dot-finally-statement-javascript.md)