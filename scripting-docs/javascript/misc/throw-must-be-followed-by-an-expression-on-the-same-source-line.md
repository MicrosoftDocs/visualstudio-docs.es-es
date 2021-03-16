---
description: Usó la palabra clave Throw, pero no la siguió con una expresión en la misma línea de código fuente.
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
ms.openlocfilehash: cfa2bace6f82ae972204cc0a405cc7e8682e98af
ms.sourcegitcommit: 691d2a47f92f991241fdb132a82c53a537198d50
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/16/2021
ms.locfileid: "103570718"
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
  
## <a name="see-also"></a>Consulte también  
 [Error (objeto)](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Error)   
 [Throw (instrucción)](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Statements/throw)   
 [try... detectar... Finally (instrucción)](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Statements/try...catch)
