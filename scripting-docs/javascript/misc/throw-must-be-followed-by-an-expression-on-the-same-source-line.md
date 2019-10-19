---
title: Throw debe ir seguido de una expresión en la misma línea de código fuente | Microsoft Docs
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
ms.openlocfilehash: 8854acb3d1992283899c4ff095f5d754c05f55a1
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572748"
---
# <a name="throw-must-be-followed-by-an-expression-on-the-same-source-line"></a>Throw debe ir seguido de una expresión en la misma línea de código fuente
Ha usado la palabra clave `throw`, pero no la ha seguido con una expresión en la misma línea de código fuente. Una instrucción `throw` consta de dos partes: la palabra clave `throw`, seguida de la expresión que se va a producir. Por ejemplo:  
  
```JavaScript  
if (denominator == 0) {  
 throw new DivideByZeroException();  
}  
```  
  
 Estos dos componentes no se pueden dividir.  
  
### <a name="to-correct-this-error"></a>Para corregir este error  
  
- Asegúrese de que la palabra clave `throw` y la expresión que se va a producir aparecen en la misma línea.  
  
## <a name="see-also"></a>Vea también  
 [Objeto de Error](../../javascript/reference/error-object-javascript.md)    
 [instrucción throw](../../javascript/reference/throw-statement-javascript.md)    
 [Try...Catch...Finally (Instrucción)](../../javascript/reference/try-dot-dot-dot-catch-dot-dot-dot-finally-statement-javascript.md)