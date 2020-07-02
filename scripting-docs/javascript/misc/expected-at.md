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
ms.openlocfilehash: 209a8793c0940511b7ecb2abb32f537a614ebf8b
ms.sourcegitcommit: ca777040ca372014b9af5e188d9b60bf56e3e36f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/01/2020
ms.locfileid: "85814829"
---
# <a name="expected-"></a>Se esperaba ' \@ '
Ha intentado crear una variable que se va a usar con instrucciones de compilación condicional mediante la `@set` instrucción, pero no ha colocado una arroba " **@** " antes del nombre de la variable.  
  
### <a name="to-correct-this-error"></a>Para corregir este error  
  
- Agregue un arroba " **@** " inmediatamente antes del nombre de la variable. Por ejemplo:  
  
    ```JavaScript  
    @set @myvar = 1  
    ```  
  
## <a name="see-also"></a>Vea también  
 [@setPrivacidad](../../javascript/reference/at-set-statement-javascript.md)   
 [Compilación condicional](../../javascript/advanced/conditional-compilation-javascript.md)   
 [Variables de compilación condicional](../../javascript/advanced/conditional-compilation-variables-javascript.md)
