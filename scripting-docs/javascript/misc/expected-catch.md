---
description: Usó el bloque try del control de excepciones, pero no escribió la instrucción Catch asociada.
title: Se esperaba ' Catch ' | Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: error-reference
f1_keywords:
- VS.WebClient.Help.SCRIPT1033
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: f1cd947f-eba2-411e-8e84-8ca86f608643
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b5cf6087ff5a299c575ac4f2cd5eb8a3e206b7e0
ms.sourcegitcommit: 691d2a47f92f991241fdb132a82c53a537198d50
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/16/2021
ms.locfileid: "103571043"
---
# <a name="expected-catch"></a>Se esperaba 'catch'
Usó el bloque **try** del control de excepciones, pero no escribió la instrucción **catch** asociada. El mecanismo de control de excepciones requiere que el código que puede producir un error, junto con el código que no debe ejecutarse si se produce una excepción, se ajuste dentro de un bloque **try** . Las excepciones se producen en el bloque **try** mediante la instrucción **Throw** y se detectan fuera del bloque **try** con una o más instrucciones **catch** .  
  
### <a name="to-correct-this-error"></a>Para corregir este error  
  
- Agregue el bloque **catch** asociado.  
  
- Pruebe a usar un bloque **Finally** en lugar de un bloque **catch** .  
  
## <a name="see-also"></a>Consulte también  
 [try... detectar... Finally (instrucción)](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Statements/try...catch)   
 [Objeto de error](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Error)
