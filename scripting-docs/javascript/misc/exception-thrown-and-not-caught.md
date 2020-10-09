---
title: Excepción producida y no detectada | Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: error-reference
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
ms.openlocfilehash: 6a0e3eb6d1275e5598ad44ea553e22f0b53eeb45
ms.sourcegitcommit: e38419bb842d587fd9e37c24b6cf3fc5c2e74817
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/09/2020
ms.locfileid: "91862762"
---
# <a name="exception-thrown-and-not-caught"></a>Excepción producida y no detectada
Incluyó una `throw` instrucción en el código, pero no estaba incluida en un bloque **try** o no había ningún bloque **catch** asociado para interceptar el error. Las excepciones se producen en el bloque **try** mediante la instrucción **Throw** y se detectan fuera del bloque **try** con una instrucción **catch** .  
  
### <a name="to-correct-this-error"></a>Para corregir este error  
  
- Incluya código que pueda producir una excepción en un bloque **try** y asegúrese de que hay un bloque **catch** correspondiente.  
  
- Asegúrese de que la instrucción Catch espera la forma correcta de la excepción.  
  
- Si se vuelve a producir la excepción, asegúrese de que hay otra instrucción Catch correspondiente.  
  
## <a name="see-also"></a>Vea también  
 [Error (objeto)](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Error)   
 [Throw (instrucción)](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Statements/throw)   
 [try... detectar... Finally (instrucción)](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Statements/try...catch)