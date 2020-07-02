---
title: Throw debe ir seguido de una expresión en la misma línea de código fuente | Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: error-reference
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
ms.openlocfilehash: b7bc7ff09152cd0ce7b95c6de73ea98446529c44
ms.sourcegitcommit: ca777040ca372014b9af5e188d9b60bf56e3e36f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/01/2020
ms.locfileid: "85815531"
---
# <a name="throw-must-be-followed-by-an-expression-on-the-same-source-line"></a>Throw debe ir seguido de una expresión en la misma línea de código fuente
Usó la `throw` palabra clave, pero no la siguió con una expresión en la misma línea de código fuente. Una `throw` instrucción consta de dos partes: la `throw` palabra clave, seguida de la expresión que se va a producir. Por ejemplo:  
  
```JavaScript  
if (denominator == 0) {  
 throw new DivideByZeroException();  
}  
```  
  
 Estos dos componentes no se pueden dividir.  
  
### <a name="to-correct-this-error"></a>Para corregir este error  
  
- Asegúrese de que la `throw` palabra clave y la expresión que se va a producir aparecen en la misma línea.  
  
## <a name="see-also"></a>Vea también  
 [Error (objeto)](../../javascript/reference/error-object-javascript.md)   
 [Throw (instrucción)](../../javascript/reference/throw-statement-javascript.md)   
 [try... detectar... Finally (instrucción)](../../javascript/reference/try-dot-dot-dot-catch-dot-dot-dot-finally-statement-javascript.md)