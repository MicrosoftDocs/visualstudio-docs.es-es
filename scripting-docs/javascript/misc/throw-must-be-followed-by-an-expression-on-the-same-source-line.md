---
title: Throw debe ir seguida de una expresión en la misma línea de código fuente | Documentos de Microsoft
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
- VS.WebClient.Help.SCRIPT1035
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: b03b7747-01a1-40c6-af80-a1dd70bc5781
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7179a22d2713c9ddc894618bd6921f3f873f2ad8
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
ms.locfileid: "24633135"
---
# <a name="throw-must-be-followed-by-an-expression-on-the-same-source-line"></a>Throw debe ir seguido de una expresión en la misma línea de código fuente
Se usa el `throw` palabra clave, pero no siguiera con una expresión en la misma línea de código fuente. A `throw` instrucción consta de dos partes: el `throw` (palabra clave), seguido de la expresión que se produzca. Por ejemplo:  
  
```JavaScript  
if (denominator == 0) {  
 throw new DivideByZeroException();  
}  
```  
  
 No se dividen estos dos componentes.  
  
### <a name="to-correct-this-error"></a>Para corregir este error  
  
-   Asegúrese de que el `throw` palabra clave y la expresión que se produzca aparece en la misma línea.  
  
## <a name="see-also"></a>Vea también  
 [Objeto de error](../../javascript/reference/error-object-javascript.md)   
 [throw (instrucción)](../../javascript/reference/throw-statement-javascript.md)   
 [Try...Catch...Finally (Instrucción)](../../javascript/reference/try-dot-dot-dot-catch-dot-dot-dot-finally-statement-javascript.md)