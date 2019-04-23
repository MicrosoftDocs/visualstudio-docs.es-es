---
title: Throw debe ir seguido de una expresión en la misma línea de código fuente | Documentos de Microsoft
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: reference
f1_keywords:
- VS.WebClient.Help.SCRIPT1035
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: b03b7747-01a1-40c6-af80-a1dd70bc5781
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 4c8ed951fb30b84f114f8f44a60e94b88f0f1d0f
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/22/2019
ms.locfileid: "60069528"
---
# <a name="throw-must-be-followed-by-an-expression-on-the-same-source-line"></a>Throw debe ir seguido de una expresión en la misma línea de código fuente
Ha utilizado el `throw` palabra clave, pero no seguido de una expresión en la misma línea de código fuente. Un `throw` instrucción consta de dos partes: el `throw` palabra clave, seguida de la expresión que se produzca. Por ejemplo:  
  
```JavaScript  
if (denominator == 0) {  
 throw new DivideByZeroException();  
}  
```  
  
 No se dividen estos dos componentes.  
  
### <a name="to-correct-this-error"></a>Para corregir este error  
  
- Asegúrese de que el `throw` palabra clave y la expresión que se produzca aparece en la misma línea.  
  
## <a name="see-also"></a>Vea también  
 [Objeto de error](../../javascript/reference/error-object-javascript.md)   
 [Throw (instrucción)](../../javascript/reference/throw-statement-javascript.md)   
 [Try...Catch...Finally (Instrucción)](../../javascript/reference/try-dot-dot-dot-catch-dot-dot-dot-finally-statement-javascript.md)