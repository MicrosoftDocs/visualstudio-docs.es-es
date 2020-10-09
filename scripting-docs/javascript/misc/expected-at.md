---
title: Se esperaba ' @ ' | Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: error-reference
f1_keywords:
- VS.WebClient.Help.SCRIPT1032
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 82ff8b74-1710-4358-9a26-dc92ab29c53b
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 98a35421054e4d2236fe509224ed146063b61a79
ms.sourcegitcommit: e38419bb842d587fd9e37c24b6cf3fc5c2e74817
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/09/2020
ms.locfileid: "91862306"
---
# <a name="expected-"></a>Se esperaba "\@"
Ha intentado crear una variable que se va a usar con instrucciones de compilación condicional mediante la `@set` instrucción, pero no ha colocado una arroba " **@** " antes del nombre de la variable.  
  
### <a name="to-correct-this-error"></a>Para corregir este error  
  
- Agregue un arroba " **@** " inmediatamente antes del nombre de la variable. Por ejemplo:  
  
    ```JavaScript  
    @set @myvar = 1  
    ```  
  
## <a name="see-also"></a>Vea también  
 [@set Privacidad](https://developer.mozilla.org/docs/Archive/Web/JavaScript/Microsoft_Extensions/at-set)   
 [Compilación condicional](/previous-versions/windows/internet-explorer/ie-developer/scripting-articles/121hztk3(v=vs.84))   
 [Variables de compilación condicional](/previous-versions/windows/internet-explorer/ie-developer/scripting-articles/s59bkzce(v=vs.84))