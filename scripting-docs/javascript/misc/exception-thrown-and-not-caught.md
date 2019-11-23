---
title: Excepción producida y no detectada | Microsoft Docs
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
ms.openlocfilehash: 05a9e4f51d5daf7a9e1b1153acbbe8b76b539b72
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572857"
---
# <a name="exception-thrown-and-not-caught"></a>Excepción producida y no detectada
Incluyó una instrucción `throw` en el código, pero no estaba incluida en un bloque **try** o no había ningún bloque **catch** asociado para interceptar el error. Las excepciones se producen en el bloque **try** mediante la instrucción **Throw** y se detectan fuera del bloque **try** con una instrucción **catch** .  
  
### <a name="to-correct-this-error"></a>Para corregir este error  
  
- Incluya código que pueda producir una excepción en un bloque **try** y asegúrese de que hay un bloque **catch** correspondiente.  
  
- Asegúrese de que la instrucción Catch espera la forma correcta de la excepción.  
  
- Si se vuelve a producir la excepción, asegúrese de que hay otra instrucción Catch correspondiente.  
  
## <a name="see-also"></a>Vea también  
 [Objeto de Error](../../javascript/reference/error-object-javascript.md)   
 [instrucción throw](../../javascript/reference/throw-statement-javascript.md)   
 [Try...Catch...Finally (Instrucción)](../../javascript/reference/try-dot-dot-dot-catch-dot-dot-dot-finally-statement-javascript.md)